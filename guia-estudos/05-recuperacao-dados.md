## Para `05-recuperacao-dados.md`

### Cursos
- [ ] **Linux Force – Análise Forense Digital Computacional** (pago, 160h)
  - https://linuxforce.com.br/cursos-de-seguranca-da-informacao/curso-analise-forense-digital-computacional/
  - Recuperação de arquivos e partições, TSK, Foremost, carving.
  - Certificado. Em português.

- [ ] **ESR/RNP – Análise Forense** (grátis)
  - https://esr.rnp.br/curso/analise-forense-seg3/
  - Recuperação de dados, ADS, histórico, senhas.
  - Online, gratuito, com certificado.

- [ ] **Udemy – Fundamentos de Perícia Digital e Investigação Online** (pago, barato)
  - https://www.udemy.com/course/fundamentos-de-pericia-digital-e-investigacao-online/
  - Aquisição de disco, recuperação de arquivos (data carving, FS Forensic).
  - Em português, prático.

- [ ] **Udemy – Introdução à Investigação e Computação Forense** (pago)
  - https://www.udemy.com/course/computacao-forense-e-investigacao-digital/
  - Autopsy, IPED, file carving, timeline.
  - Atualizado 2025.

### Livros
- [ ] **Silvio Ferreira – Curso Prático de Recuperação de Dados em HDs e SSDs Vol. 1**
  - 350 páginas, em português.
  - TestDisk, R-Studio, Recuva, extundelete. Passo a passo.
  - **Comece por este.** É o mais direto para o seu objetivo.

- [ ] **Brian Carrier – File System Forensic Analysis** (cap. 13-15)
  - Cap. 13: File System Analysis (como recuperar a partir da estrutura)
  - Cap. 14: NTFS in Depth (MFT, $LogFile, atributos)
  - Cap. 15: ext2/3/4 in Depth (inode, journal, block group)
  - **Este é o livro que te faz entender O PORQUÊ de cada ferramenta funcionar.**

- [ ] **Kris Kaspersky – Data Recovery Tips & Solutions** (em inglês)
  - Foco em NTFS, Windows, Linux, BSD.
  - Técnicas práticas: MFT mirror, $LogFile parsing, extundelete.

### Prática (na VM + HD de estudo) — **O CORAÇÃO DO SEU ESTUDO**
- [ ] **Cenário 1:** Apagar partição → recuperar com TestDisk
- [ ] **Cenário 2:** Apagar arquivo ext4 → recuperar com extundelete
- [ ] **Cenário 3:** Corromper MBR (zerar com dd) → reescrever com TestDisk
- [ ] **Cenário 4:** Criar imagem com ddrescue de disco com erros simulados
- [ ] **Cenário 5:** Recuperar arquivo de NTFS (VM Windows)
- [ ] **Cenário 6:** Recuperar dados de pen drive FAT32/exFAT
- [ ] **Cenário 7:** Usar debugfs para listar inodes apagados em ext4
- [ ] **Cenário 8:** PhotoRec (file carving) em imagem de disco
- [ ] **Cenário 9:** e2fsck em fs corrompido → depois tentar recuperar
- [ ] **Cenário 10:** ntfsfix + testdisk em NTFS corrompido

### O que marcar no 05 após estudar
- [ ] Fundamentos (imagem de disco, ddrescue, file carving)
- [ ] TestDisk (partição, MBR, GPT)
- [ ] PhotoRec (carving)
- [ ] ext4 (extundelete, debugfs, ext4magic, journaling)
- [ ] NTFS (MFT, ntfsfix, testdisk)
- [ ] Ferramentas pagas (R-Studio, DiskDrake, UFS)
- [ ] Cenários práticos (10 cenários acima)