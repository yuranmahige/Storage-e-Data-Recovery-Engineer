## Para `06-avancado.md`

### Cursos
- [ ] **4Linux – LPIC-2 (Módulo 204.4)** (pago, dentro do LPIC-2)
  - ZFS e Btrfs: pool, dataset, snapshot, send/receive.

- [ ] **CyberExperts – Perícia e Investigação Forense Digital** (pago)
  - https://cyberexperts.com.br/curso-pericia-digital/
  - Cadeia de custódia, coleta, Autopsy, carving, esteganografia.
  - Certificado com prova técnica.

- [ ] **IBSEC – Perícia Digital Forense** (pago)
  - https://ibsec.com.br/curso-pericia-digital-forense
  - 7 módulos, 5 meses, 100% online, labs práticos.
  - Mais avançado: laudos periciais, evidências, análise forense completa.

- [ ] **Wizape – Forense Digital** (grátis)
  - https://wizape.com/Portugu%C3%AAs/Forense-digital
  - Módulos: resposta a incidentes, aquisição forense, file carving.
  - Gratuito, bom para introdução.

### Livros
- [ ] **Ricardo Galvão – Perícia Forense Digital** (Novatec)
  - Cap. 3: mídias de armazenamento, extração, análise de fs.
  - Em português, focado em perícia.

- [ ] **Brian Carrier – File System Forensic Analysis** (cap. 16-19)
  - Cap. 16: XFS
  - Cap. 17: UFS
  - Cap. 18: Recovery (técnicas avançadas)
  - Cap. 19: File Carving (avançado)

### Prática
- [ ] Criar pool ZFS (raidz1) com 2 discos virtuais
- [ ] Criar dataset, snapshot, rollback
- [ ] Criar subvolumes Btrfs + snapshot + send/receive
- [ ] Rodar `btrfs scrub` e `zpool scrub`
- [ ] Instalar Autopsy, carregar imagem de disco, navegar timeline
- [ ] Fazer hash SHA256 de imagem (cadeia de custódia)
- [ ] Criar VM "quebrada" de propósito e documentar o processo

### O que marcar no 06 após estudar
- [ ] Forense (cadeia de custódia, hash, Autopsy, timeline)
- [ ] ZFS (pool, dataset, snapshot, copy-on-write, auto-repair)
- [ ] Btrfs (subvolumes, snapshots, btrfs rescue)
- [ ] Virtualização (VM quebrada, qemu-nbd, guestfish)
- [ ] Rotina prática semanal