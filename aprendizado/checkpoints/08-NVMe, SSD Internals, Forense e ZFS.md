## 07 — Avançado: NVMe, SSD Internals, Forense e ZFS

> **Pré-requisitos:** Fases 3, 4 e 5 concluídas
> **Duração estimada:** 4–6 semanas
> **Meta:** Dominar o que muda quando o disco não é mais um "disco" — quando é um SSD com FTL, um NVMe com encryption, ou um pool ZFS com 12 vdevs.

---

### 7.1 — SSD Internals: O que muda na recuperação

- [ ] Entender o **FTL (Flash Translation Layer)**: mapping LBA → PBA, tabela em DRAM, flush para NAND
- [ ] **Wear leveling:** dynamic vs. static; por que um SSD "morre" com 0% de bad sectors
- [ ] **Over-provisioning (OP):** o que é, por que o fabricante esconde setores, e como isso afeta a recuperação
- [ ] **TRIM:** o que o SO envia, o que o FTL faz, e por que dados "apagados" com TRIM são **irrecuperáveis**
- [ ] **Garbage collection:** quando acontece, por que causa latência, e por que um SSD "lento" pode ter GC em loop
- [ ] **Read disturb / retention:** degradação de carga na célula NAND; por que dados "somem" em SSDs desligados há meses
- [ ] **S.M.A.R.T. específico de SSD:** atributos 201 (program fail), 202 (erase fail), 231 (worn level), 233 (media wearout)
- [ ] **Prática:** `smartctl -a /dev/sdX` em um SSD — identificar cada atributo e interpretar o valor

> **Exercício:** Compre um SSD usado (32–128 GB). Preencha com dados, envie TRIM, tente recuperar com `photorec`. Documente o que **não** recuperou e por quê.

---

### 7.2 — NVMe / PCIe: O que muda em relação a SATA

- [ ] **Diferença fundamental:** NVMe não é "SATA mais rápido" — é um protocolo diferente (queues, commands, namespaces)
- [ ] **NVMe command set:** 64.000 queues × 64.000 commands vs. 1 queue × 32 commands (SATA)
- [ ] **`nvme` CLI (nvme-cli):**
  - [ ] `nvme list` — identificar drives
  - [ ] `nvme smart-log /dev/nvme0` — S.M.A.R.T. NVMe
  - [ ] `nvme error-log /dev/nvme0` — erros recentes
  - [ ] `nvme fw-log /dev/nvme0` — firmware info
  - [ ] `nvme id-ctrl /dev/nvme0` — controller capabilities
  - [ ] `nvme format /dev/nvme0n1` — **NUNCA** usar em drive com dados críticos
- [ ] **Resets em camadas** (do físico ao protocolo):
  - [ ] PERST# (hardware) — quando usar
  - [ ] Secondary Bus Reset / Retrain Link
  - [ ] Function Level Reset (FLR)
  - [ ] NVMe Controller Reset (CC.EN=0→1)
- [ ] **PCIe AER:** ler `dmesg | grep -i aer` e classificar o erro (Correctable / Non-Fatal / Fatal)
- [ ] **Encryption em NVMe:** AES-256 por hardware + scrambling proprietário → por que `ddrescue` **não funciona** em NVMe com controller em panic
- [ ] **`ddrescue` em NVMe:** funciona? (Sim, se o controller responde. Não, se o FTL está em panic.)
- [ ] **Prática:** Instalar um NVMe na VM (ou usar U.2/M.2 no host). Fazer `nvme smart-log`, `nvme error-log`, interpretar.

> **Exercício:** Simular um "controller em panic" (se possível com firmware antigo) e documentar a sequência de resets necessária para recuperar o link.

---

### 7.3 — Raw Hex Editing / Sector-Level Analysis

- [ ] **MBR em hex:** abrir setor 0 com `xxd -l 512 /dev/sdX > mbr.hex` e identificar:
  - [ ] Boot code (bytes 0–445)
  - [ ] Partition table (bytes 446–509) — 4 entradas de 16 bytes
  - [ ] Signature `0x55AA` (bytes 510–511)
- [ ] **GPT em hex:** identificar:
  - [ ] Protective MBR (setor 0)
  - [ ] GPT Header (setor 1) — signature `EFI PART`
  - [ ] Partition entries (setores 2–33)
  - [ ] Backup GPT (último setor)
- [ ] **`binwalk` em imagens de disco:** identificar filesystems embutidos, MBRs aninhados, firmware
- [ ] **`hexdump` / `xxd` / `hexedit`:** navegar por uma imagem `.img` e encontrar:
  - [ ] Magic bytes de ext4 (`0xEF53` no superblock, setor 0 do FS = LBA 2048)
  - [ ] Magic bytes de NTFS (`NTFS    ` no setor 0 do volume)
  - [ ] Inode table de ext4
- [ ] **Prática:** Criar uma imagem de 1 GB com `dd`, particionar, formatar ext4, escrever um arquivo. Abrir em hex e encontrar o arquivo pelo conteúdo.

> **Exercício:** Escrever um script Python que lê o setor 0 de uma imagem e imprime a partition table em formato legível (sem usar `fdisk -l`). (Isso é o `mbr-parser` do seu roadmap.)

---

### 7.4 — `ddrescue` na prática: mapfile e retoma de jobs

- [ ] **Formato do mapfile:**
  ```
  # Mapfile probed with GNU ddrescue 1.28
  # Command line: ddrescue -b 4M -c 16 /dev/sdb /mnt/image.img /mnt/map.map
  # Create date: 2026-10-21 14:30:00
  # Update time: 2026-10-21 14:35:22 [Size 500 GB] [Free space 200 GB] [Req rate 120 MB/s] [Read 1.2 MB/s] [Error rate 0]
  1073741824 524288 23
  0 1073741824 0
  # Current status: finished
  ```
  - [ ] Ler e interpretar cada campo
  - [ ] Entender o que significa `23` (error code)
  - [ ] Entender a ordem: blocos bons primeiro, depois ruins (reverse)
- [ ] **Retomar um job interrompido:** `ddrescue` com o mesmo mapfile → continua de onde parou
- [ ] **Merge de mapfiles:** dois jobs com flags diferentes (`-d` direct, `-n` no-retry) → combinar
- [ ] **Estratégia de imaging:**
  - [ ] 1ª passada: `-d` (direct I/O) — rápido, lê o que lê
  - [ ] 2ª passada: `-n` (no retry) — tenta os blocos ruins uma vez
  - [ ] 3ª passada: sem flags — tenta os restantes com retry
- [ ] **Prática:** Fazer um imaging completo de um HD com setores ruins (use `badblocks -w` para criar setores ruins). Interpretar o mapfile. Retomar após "queda" simulada.

---

### 7.5 — ZFS: Pools, Vdevs e Recuperação

- [ ] **Arquitetura:** pool → vdev → disco; RAID-Z, mirror, stripe
- [ ] **Comandos essenciais:**
  - [ ] `zpool create`, `zpool status`, `zpool scrub`, `zpool replace`
  - [ ] `zfs create`, `zfs snapshot`, `zfs send`, `zfs receive`
  - [ ] `zpool import` — **recuperação de pool** (a ferramenta mais importante)
- [ ] **Recuperação de pool:**
  - [ ] Disco removido → `zpool import -F` (forçar)
  - [ ] Pool "unavail" → `zpool import -m` (forçar import)
  - [ ] Metadados corrompidos → `zpool import` com `force`
- [ ] **Snapshots como recuperação:** `zfs rollback` — o "undo" do ZFS
- [ ] **Prática:** Criar um pool mirror de 2 vdevs (VMs ou discos reais). Remover um disco. Importar. Fazer `zpool scrub`. Documentar o tempo de resync.

---

### 7.6 — Forense: Protocolo de Imaging

- [ ] **Chain of custody:** documentar quem, quando, onde, com qual ferramenta, hash de verificação
- [ ] **Write blockers:** hardware (Forensic USB) vs. software (`mount -o ro,remount,ro`)
- [ ] **Ferramentas de imaging:**
  - [ ] `dd` — básico, sem log
  - [ ] `ddrescue` — com mapfile, retoma
  - [ ] `dcfldd` (SANS) — com hash dual (MD5 + SHA256) embutido
  - [ ] `Guymager` — GUI, multi-thread, relatório automático
- [ ] **Hashing:**
  - [ ] `md5sum`, `sha256sum` — verificar integridade
  - [ ] Hash **antes** e **depois** do imaging
  - [ ] Hash do original e da imagem devem ser **idênticos**
- [ ] **Autopsy / Sleuth Kit:**
  - [ ] Carregar imagem
  - [ ] File system analysis
  - [ ] Timeline (MACB: Modified, Accessed, Created, Birth)
  - [ ] Slack space analysis
- [ ] **Prática:** Fazer um imaging forense completo:
  1. Write blocker (ou `mount -o ro`)
  2. `dcfldd` com hash dual
  3. Verificar hash
  4. Carregar no Autopsy
  5. Gerar relatório
  6. Documentar chain of custody

---

### 7.7 — Btrfs: O que saber

- [ ] **Subvolumes:** o que são, como criar, como montar individualmente
- [ ] **Snapshots:** copy-on-write, espaço quase zero
- [ ] **`btrfs rescue`:**
  - [ ] `btrfs rescue zero-log` — quando o journal está corrompido
  - [ ] `btrfs check` — verificação de consistência
  - [ ] `btrfs device delete` — remover disco de um pool
- [ ] **Prática:** Criar um subvolume, fazer snapshot, corromper o journal (simulado), recuperar com `zero-log`.

---

### 7.8 — Ferramentas finais (entregáveis)

- [ ] **`nvme-health`** (Python): S.M.A.R.T. NVMe + alerta por e-mail/webhook
- [ ] **`ftl-analyzer`** (Python): Ler S.M.A.R.T. de SSD e estimar vida útil restante
- [ ] **`forensic-imager`** (Bash): Pipeline completo: write-block → image → hash → verify → report
- [ ] **`zpool-doctor`** (Bash): Health check de pools ZFS + sugestão de ação
- [ ] **`sector-reader`** (Python): Ler setores específicos de uma imagem e decodificar (MBR, GPT, superblock ext4)

---

### 7.9 — Critério de conclusão

- [ ] Conseguiu explicar FTL em voz alta para alguém leigo (técnica Feynman)
- [ ] Fez 1 imaging forense completo com chain of custody documentada
- [ ] Recuperou um pool ZFS com disco removido
- [ ] Leu o MBR em hex e identificou a partition table sem ferramenta
- [ ] Tem 2 ferramentas novas funcionando (além das da Fase 6)
- [ ] Documentou tudo em notas

---

### Próximos passos (após Fase 7)

Se quiser expandir para **enterprise storage**:

- [ ] NVMe-oF / NVMe/TCP
- [ ] Ceph básico (pools, OSDs, MONs)
- [ ] Kubernetes CSI drivers
- [ ] HPC storage (Lustre / GPFS)

---

*Última atualização: 2026-10-21*