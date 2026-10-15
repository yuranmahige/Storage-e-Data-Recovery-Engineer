O Foco é o **lado de software** do armazenamento: sistemas de arquivos, particionamento, LVM, recuperação lógica de dados, gestão de setores defeituosos. O hardware entra só como contexto mínimo.

Aqui vão os livros mais alinhados com esse perfil:

## Sistemas de Arquivos e Administração de Discos (Linux)

| Livro | Autor | Por quê |
|-------|-------|---------|
| *Guia prático do servidor Linux* | Juliano Ramos (Casa do Código) | Capítulos de particionamento, LVM, RAID, sistemas de arquivos. Prático e direto. |
| *Administração de Sistemas Linux* | Ari Frazão Jr. & Marcelo Braga | Particionamento, LVM, ext4, XFS. Bom para estrutura completa. |
| *Linux From Scratch* (LFS) | (comunidade) | Gratuito, PDF. Mostra **exatamente** como criar partições, formatar ext4, montar, configurar LVM — do zero. Excelente para entender o que acontece "por baixo". |

> **Bônus gratuito:** os materiais do [LPI Linux Professional Institute](https://learning.lpi.org/pt/learning-materials/101-500/104/104.1/104.1_01/) (certificação LPIC-1, módulo 104) cobrem particionamento MBR/GPT, ext4, XFS, LVM, RAID — tudo que você quer, de forma estruturada e gratuita.

## Recuperação de Dados (foco lógico / software)

| Livro | Autor | Por quê |
|-------|-------|---------|
| *File System Forensic Analysis* | **Brian Carrier** | **A** referência. Explica a estrutura interna de NTFS, ext2/3/4, FAT, XFS — MFT, inodes, blocos, journaling — e como recuperar dados a partir deles. É denso, mas é o livro que separa quem "usa um software de recuperação" de quem **entende** o que está acontecendo no disco. |
| *Data Recovery* | Kris Kaspersky | Foco em NTFS (MFT, $LogFile, atributos), técnicas de recuperação, análise de metadados. Menos "forense", mais "recuperação prática". |
| *Curso Prático de Recuperação de Dados em HDs e SSDs – Vol. 1* | Silvio Ferreira (Instituto Alpha) | 350 páginas, em português. Cobre: como funciona um HD, partições, MBR, GPT, recuperação com TestDisk, R-Studio, Recuva, extundelete. Prático, passo a passo. |

## Forense Digital

| Livro | Autor | Por quê |
|-------|-------|---------|
| *Perícia Forense Digital* | Ricardo Kléber M. Galvão (Novatec) | Tipos de armazenamento, recuperação de arquivos, imagem de disco (dd, FTK), Autopsy. |
| *Tratado de Computação Forense* | Vários autores (Millennium) | Cap. 3: "Exames em mídias de armazenamento" — anatomia de HDs/SSDs, extração, análise de sistemas de arquivos. |

## Roteiro sugerido (do básico ao avançado)

1. **LPI LPIC-1 (módulo 104)** — gratuito, online. Particionamento, ext4, LVM, RAID.
2. **Brian Carrier – *File System Forensic Analysis*** — a base teórica de *como* os dados estão organizados no disco.
3. **Silvio Ferreira – *Recuperação de Dados Vol. 1*** — prática em português, ferramentas reais.
4. **Kris Kaspersky – *Data Recovery*** — aprofundamento em NTFS e técnicas avançadas.
5. **LFS (Linux From Scratch)** — se quiser entender cada comando (`fdisk`, `mkfs.ext4`, `mount`, `lvm`) na prática.

## Ferramentas essenciais para praticar (gratuitas)

| Ferramenta | Uso |
|-----------|-----|
| `fdisk` / `gdisk` / `parted` | Particionamento (MBR/GPT) |
| `mkfs.ext4`, `mkfs.xfs`, `mkfs.ntfs` | Formatação |
| `mount` / `umount` | Montar/desmontar |
| `lvm` (pvcreate, vgcreate, lvcreate) | Volumes lógicos |
| `dd` / `ddrescue` | Imagem de disco (clone bit a bit) |
| `smartctl` (smartmontools) | Ler S.M.A.R.T. — detectar setores defeituosos |
| `badblocks` | Testar e mapear setores ruins |
| `e2fsck` / `xfs_repair` | Reparar sistemas de arquivos |
| `chkdsk /r` (Windows) | Reparar NTFS + remapear setores |
| `testdisk` / `photorec` | Recuperação de partições e arquivos |
| `extundelete` / `ext4magic` | Recuperação específica de ext4 |
| `R-Studio` (pago) | Recuperação profissional multi-OS |

**Dica:** instale um Linux (Ubuntu, Fedora ou até um live USB) e pratique em um disco velho ou em VMs. Criar partições, formatar, corromper de propósito e recuperar — é assim que a fixação acontece.