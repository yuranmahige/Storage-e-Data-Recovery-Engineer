## Para `04-manutencao-discos.md`

### Cursos
- [ ] **Linux Universe – Manutenção Avançada do Disco Rígido** (grátis, artigo)
  - https://linuxuniverse.com.br/linux/manutencao-hdd
  - smartmontools, badblocks, hdparm — passo a passo.

- [ ] **Kbase.pt – Diagnóstico de Discos com SMART e Bad Sectors** (grátis, artigo)
  - https://kbase.pt/diagnostico-discos-smart-bad-sectors-2026/
  - Comandos práticos de smartctl, interpretação de atributos.

- [ ] **4Linux – LPIC-2 (Módulo 204.2)** (pago, dentro do curso LPIC-2)
  - "Ajuste de Storage – Ferramentas de Disco"
  - hdparm, fstrim, iostat, fio.

### Livros
- [ ] **Brian Carrier – File System Forensic Analysis** (cap. 1-2)
  - Entender a estrutura física (setores, trilhas, superfícies) ajuda a interpretar SMART.

- [ ] **Documentação oficial smartmontools** (grátis, online)
  - https://www.smartmontools.org/
  - Wiki: interpretação de cada atributo SMART por fabricante.
  - Use como referência de consulta.

### Prática (no HD de estudo)
- [ ] Instalar smartmontools: `apt install smartmontools`
- [ ] Rodar `smartctl -a /dev/sdX` e anotar cada atributo
- [ ] Rodar `smartctl -t long /dev/sdX` (teste longo, ~2-3h)
- [ ] Interpretar: Reallocated_Sector_Ct, Pending_Sector, Uncorrectable
- [ ] Rodar `badblocks -n /dev/sdX` (não destrutivo) em disco de teste
- [ ] Verificar `dmesg | grep -i error` após I/O intenso
- [ ] Rodar `fio` para benchmark de I/O
- [ ] Verificar S.M.A.R.T. de SSD: `nvme smart-log /dev/nvme0n1`
- [ ] Agendar smartd (daemon) e verificar alertas

### O que marcar no 04 após estudar
- [ ] S.M.A.R.T. (conceito, smartctl, atributos, smartd)
- [ ] Setores defeituosos (reallocated, pending, irrecuperável, badblocks)
- [ ] Health check (protocolo, critérios de "disco morrendo")
- [ ] Ferramentas (hdparm, nvme, iostat, fio)