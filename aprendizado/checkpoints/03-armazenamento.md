# Armazenamento: Partições, Sistemas de Arquivos, LVM, RAID

## Particionamento
- [ ] Sabe o que é MBR (tabela de partição mestra)
- [ ] Sabe o que é GPT (GUID Partition Table)
- [ ] Sabe a diferença entre MBR e GPT
- [ ] Sabe o que é uma partição primária, estendida, lógica
- [ ] Sabe o que é uma partição de boot (EFI System Partition)
- [ ] Sabe usar `fdisk -l` para listar discos e partições
- [ ] Sabe usar `parted` para criar/apagar partições
- [ ] Sabe usar `gdisk` (GPT)
- [ ] Sabe o que é `blkid` (identificar UUID e tipo de fs)
- [ ] Sabe o que é `lsblk` (árvore de blocos)
- [ ] Sabe o que é `df -h` (uso de espaço)
- [ ] Sabe o que é `du -sh` (tamanho de diretórios)

## Sistemas de Arquivos
- [ ] Sabe o que é um sistema de arquivos (estrutura de dados)
- [ ] Sabe o que é inode
- [ ] Sabe o que é superblock
- [ ] Sabe o que é journaling
- [ ] Sabe a diferença entre ext4 e XFS
- [ ] Sabe o que é NTFS (estrutura básica)
- [ ] Sabe o que é FAT32/exFAT
- [ ] Sabe formatar: `mkfs.ext4`, `mkfs.xfs`, `mkfs.ntfs`
- [ ] Sabe montar: `mount`, `umount`
- [ ] Sabe editar `/etc/fstab` (UUID, opções de montagem)
- [ ] Sabe o que são opções: `noatime`, `defaults`, `ro`, `rw`
- [ ] Sabe o que é um ponto de montagem

## LVM (Logical Volume Manager)
- [ ] Sabe o que é PV (Physical Volume)
- [ ] Sabe o que é VG (Volume Group)
- [ ] Sabe o que é LV (Logical Volume)
- [ ] Sabe usar `pvcreate`, `vgcreate`, `lvcreate`
- [ ] Sabe expandir um LV online (`lvextend` + `resize2fs`/`xfs_growfs`)
- [ ] Sabe reduzir um LV (com backup!)
- [ ] Sabe o que é snapshot em LVM
- [ ] Sabe listar: `pvs`, `vgs`, `lvs`

## RAID (software)
- [ ] Sabe o que é RAID 0, 1, 5, 6, 10
- [ ] Sabe a diferença entre RAID hardware e software
- [ ] Sabe usar `mdadm` para criar RAID 1 e RAID 5
- [ ] Sabe adicionar/remover disco em RAID
- [ ] Sabe checar saúde: `cat /proc/mdstat`
- [ ] Sabe o que é `mdadm --monitor`
- [ ] Sabe montar um array em recuperação

## SSD específico
- [ ] Sabe verificar suporte a TRIM: `lsblk -D`
- [ ] Sabe ativar TRIM automático (fstrim.timer)
- [ ] Sabe verificar wear level: `smartctl -a /dev/nvme0`
- [ ] Sabe o que é S.M.A.R.T. em SSD
- [ ] Sabe que não deve usar `badblocks` em SSD (escreve tudo)