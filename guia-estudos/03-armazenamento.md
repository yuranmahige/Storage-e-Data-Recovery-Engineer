## Para `03-armazenamento.md`

### Cursos
- [ ] **LPI – Materiais oficiais LPIC-1 (Módulo 104)** (grátis) ⭐ **PRIORIDADE**
  - https://learning.lpi.org/pt/learning-materials/101-500/104/104.1/104.1_01/
  - 104.1: Criar partições e sistemas de arquivos (MBR, GPT, ext4, swap)
  - 104.2: Criar e configurar opções de sistemas de arquivos (mount, fstab)
  - 104.3: Administrar sistemas de arquivos (chown, chmod, ACLs, quota)
  - 104.4: Criar e administrar LVM (PV, VG, LV, snapshot, resize)
  - **É exatamente o conteúdo do arquivo 03.**

- [ ] **4Linux – Preparatório LPIC-2 (Módulo 204)** (pago) ⭐
  - https://4linux.com.br/cursos/treinamento/preparatorio-certificacao-linux-lpic2/
  - 204.1: RAID (software, mdadm, tipos 0/1/5/6/10)
  - 204.2: Ajuste de Storage (ferramentas de disco, iSCSI)
  - 204.3: LVM avançado (snapshot, resize, thin provisioning)
  - 204.4: ZFS e Btrfs (introdução)
  - **Cobre RAID + LVM avançado + ZFS/Btrfs.**

- [ ] **Certificação Linux – LPIC-2** (pago, online)
  - https://www.certificacaolinux.com.br/cursos/linux-para-lpic-2/
  - 53h, módulos em vídeo: RAID, LVM, iSCSI, snapshot.
  - Alternativa ao 4Linux se preferir outro estilo.

### Livros
- [ ] **Brian Carrier – File System Forensic Analysis** (2005, em inglês)
  - Cap. 2: File System Overview (superblock, inode, journaling)
  - Cap. 3-6: ext2/3/4 em profundidade
  - Cap. 7-9: NTFS (MFT, $LogFile, atributos)
  - Cap. 10-12: FAT, XFS
  - **Este livro é a base teórica de TUDO que você quer entender.**
  - Denso, mas é a referência. Leia os capítulos de ext4 e NTFS primeiro.

- [ ] **Juliano Ramos – Guia Prático do Servidor Linux** (Casa do Código)
  - Capítulos de particionamento, LVM, RAID, sistemas de arquivos.
  - Mais "admin de servidor" do que "recuperação", mas reforça a prática.

### Prática (na VM + HD de estudo)
- [ ] Criar 3 partições (ext4, xfs, swap) com parted
- [ ] Formatar cada uma e montar com opções diferentes
- [ ] Criar LVM: 1 PV → 1 VG → 2 LVs
- [ ] Expandir um LV online (lvextend + resize2fs)
- [ ] Criar snapshot LVM e reverter
- [ ] Criar RAID 1 com mdadm (2 discos virtuais)
- [ ] Criar RAID 5 com mdadm (3 discos virtuais)
- [ ] Remover um disco do RAID 5 e reconstruir
- [ ] Verificar TRIM: lsblk -D, fstrim.timer
- [ ] Rodar smartctl -a no HD de estudo

### O que marcar no 03 após estudar
- [ ] Particionamento (MBR, GPT, fdisk, parted, gdisk, blkid, lsblk)
- [ ] Sistemas de Arquivos (inode, superblock, journaling, ext4, XFS, NTFS, FAT)
- [ ] LVM (PV, VG, LV, expandir, snapshot)
- [ ] RAID (0, 1, 5, 6, 10, mdadm)
- [ ] SSD (TRIM, wear level, S.M.A.R.T. SSD)