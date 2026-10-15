## Para `12-cloud-storage.md`

### Cursos
- [ ] **AWS Storage — Stephane Maarek** (Udemy, ~$15)
  - S3, EBS, EFS, FSx, Glacier, Storage Gateway.
  - **Seu arquivo.** Assista 2x.

- [ ] **AWS S3 in Depth** (Udemy, vários instrutores)
  - S3 em profundidade: versioning, lifecycle, replication,
    object lock, access points, tables.

- [ ] **AWS Certified Storage Specialty (SAP-S01) — Stephane Maarek** (Udemy, ~$15)
  - **A certificação do seu nicho.** Cobre: S3, EBS, EFS, FSx,
    Glacier, Snowball, DataSync, Storage Gateway, backup, DR.
  - Estude depois do SAA-C03.

### Livros
- [ ] **AWS Certified Storage Specialty Exam Guide** (Sybex)
  - Se quiser livro para o SAP-S01.
- [ ] **Documentação AWS S3** (grátis)
  - https://docs.aws.amazon.com/AmazonS3/
  - Leia os capítulos de: versioning, replication, lifecycle,
    object lock, storage classes.

### Prática (conectar com Part 1)
- [ ] Explicar em voz alta: "S3 usa erasure coding, que é o
      equivalente de RAID 6, mas distribuído em milhares de
      máquinas. EBS é 1 volume em 1 AZ — se o AZ cair, o volume
      morre. Por isso RDS Multi-AZ existe."
- [ ] Explicar: "S3 Versioning é como snapshot LVM, mas
      incremental e automático. S3 Lifecycle é como 'mover
      dados para arquivamento' — equivalente a mover para
      um HDD frio no seu data center."