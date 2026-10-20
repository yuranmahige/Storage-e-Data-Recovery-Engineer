# Recuperação de Dados (Lógica / Software)

## Fundamentos
- [ ] Sabe o que é imagem de disco (clone bit a bit)
- [ ] Sabe usar `dd if=/dev/sdX of=imagem.img bs=4M`
- [ ] Sabe usar `ddrescue` (melhor que dd para discos com erros)
- [ ] Sabe SEMPRE trabalhar na imagem, nunca no disco original
- [ ] Sabe o que é uma partição perdida
- [ ] Sabe o que é um MBR corrompido
- [ ] Sabe a diferença entre recuperação de partição e recuperação de arquivo
- [ ] Sabe o que é file carving (recuperação por assinatura)

## TestDisk
- [ ] Sabe instalar `testdisk`
- [ ] Sabe escanear um disco/imagem
- [ ] Sabe recuperar uma partição perdida (MBR)
- [ ] Sabe recuperar uma partição GPT
- [ ] Sabe reescrever MBR
- [ ] Sabe copiar arquivos de uma partição não montável

## PhotoRec
- [ ] Sabe o que é file carving
- [ ] Sabe usar `photorec` para recuperar por tipo (foto, doc, vídeo)
- [ ] Sabe os limites: nomes originais são perdidos

## ext4 específico
- [ ] Sabe o que é `extundelete`
- [ ] Sabe usar `extundelete` para recuperar arquivo apagado
- [ ] Sabe o que é `debugfs` (debug filesystem ext4)
- [ ] Sabe usar `debugfs` para listar inodes apagados
- [ ] Sabe o que é `ext4magic`
- [ ] Sabe o que é journaling e como afeta recuperação
- [ ] Sabe que após `e2fsck` a recuperação fica mais difícil

## NTFS específico
- [ ] Sabe o que é MFT (Master File Table)
- [ ] Sabe o que é MFT mirror
- [ ] Sabe usar `ntfsfix`
- [ ] Sabe usar `testdisk` em NTFS
- [ ] Sabe o que é `$MFT` e `$MFTMirr`
- [ ] Sabe o que são atributos NTFS ($DATA, $FILE_NAME)
- [ ] Sabe usar `ntfsundelete` (se disponível)

## Ferramentas pagas (conhecer)
- [ ] Conhece R-Studio (o que faz, quando vale)
- [ ] Conhece DiskDrake (foco em HDD físico + lógico)
- [ ] Conhece UFS Explorer
- [ ] Sabe quando vale a pena pagar vs. ferramenta gratuita

## Cenários práticos (simular em VM)
- [ ] Apagar partição → recuperar com TestDisk
- [ ] Apagar arquivo ext4 → recuperar com extundelete
- [ ] Corromper MBR → reescrever
- [ ] Criar imagem com ddrescue de disco com "erros" simulados
- [ ] Recuperar arquivo de NTFS em VM Windows
- [ ] Recuperar dados de pen drive (FAT32/exFAT)