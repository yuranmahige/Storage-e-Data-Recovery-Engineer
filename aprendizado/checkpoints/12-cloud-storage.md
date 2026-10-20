# Cloud Storage (AWS)

> **Este é o seu arquivo.** Você já entende o que está por baixo.
> Aqui você aprende como a AWS expõe isso.

## S3 (Object Storage)
- [ ] Sabe o que é um Bucket
- [ ] Sabe o que é um Object (chave + valor + metadados)
- [ ] Sabe o que é um Key (caminho)
- [ ] Sabe a diferença entre S3 Standard, IA, Glacier, Deep Archive
- [ ] Sabe o que é S3 Versioning
- [ ] Sabe o que é S3 Lifecycle Policy
- [ ] Sabe o que é S3 Cross-Region Replication (CRR)
- [ ] Sabe o que é S3 Bucket Policy vs. Object ACL
- [ ] Sabe o que é S3 Pre-signed URL
- [ ] Sabe o que é S3 Event Notifications
- [ ] Sabe o que é S3 Select
- [ ] Sabe o que é S3 Storage Lens
- [ ] Sabe o que é S3 Object Lock (WORM)
- [ ] Sabe o que é S3 Replication Time Control (RTC)
- [ ] Sabe o que é S3 Access Points
- [ ] Sabe o que é S3 Directory Buckets (S3 Express One Zone)
- [ ] Sabe o que é S3 Tables (Iceberg)
- [ ] Sabe o que é erasure coding (e que S3 usa internamente)
- [ ] Sabe que S3 é "infinitely scalable" (não tem limite de disco)
- [ ] Sabe o que é S3 Multipart Upload

## EBS (Block Storage)
- [ ] Sabe o que é um Volume EBS
- [ ] Sabe os tipos: gp3, io2, io2 Block Express, st1, sc1
- [ ] Sabe o que é IOPS e Throughput
- [ ] Sabe o que é EBS Snapshot
- [ ] Sabe o que é EBS Multi-Attach
- [ ] Sabe o que é EBS Encryption
- [ ] Sabe o que é EBS Fast Snapshot Restore
- [ ] Sabe o que é EBS Direct
- [ ] Sabe que EBS é "sticky" (1 AZ, não replica automaticamente)
- [ ] Sabe a diferença entre EBS e S3 (block vs. object)
- [ ] Sabe o que é EBS Volume Resize (online)
- [ ] Sabe o que é EBS Throughput Optimized

## EFS (File Storage)
- [ ] Sabe o que é EFS (NFS na cloud)
- [ ] Sabe a diferença entre EFS e EBS
- [ ] Sabe o que é EFS Access Point
- [ ] Sabe o que é EFS Lifecycle (IA)
- [ ] Sabe o que é EFS Replication
- [ ] Sabe o que é File Cache

## FSx
- [ ] Sabe o que é FSx for Windows File Server
- [ ] Sabe o que é FSx for Lustre
- [ ] Sabe o que é FSx for OpenZFS
- [ ] Sabe o que é FSx for NetApp ONTAP

## Backup e DR
- [ ] Sabe o que é AWS Backup
- [ ] Sabe o que é Backup Vault
- [ ] Sabe o que é Cross-Region Backup
- [ ] Sabe o que é Backup Lifecycle (cold, warm, archive)
- [ ] Sabe o que é AWS Storage Gateway
- [ ] Sabe o que é AWS Snowball / Snowmobile
- [ ] Sabe o que é AWS DataSync
- [ ] Sabe o que é AWS Transfer Family (SFTP/FTPS)

## Prática
- [ ] Criar S3 Bucket + versioning + lifecycle
- [ ] Criar EBS Volume + attach a EC2 + formatar + montar
- [ ] Criar EBS Snapshot + restore para novo volume
- [ ] Criar EFS + mount em 2 EC2s
- [ ] Configurar S3 CRR (2 buckets em regions diferentes)
- [ ] Criar AWS Backup policy para EC2 + EBS + RDS
- [ ] Fazer S3 Multipart Upload de arquivo > 100MB
- [ ] Configurar S3 Object Lock (WORM)
- [ ] **Conectar com Part 1:** explicar em voz alta como S3
      é "RAID 6 + replication" e EBS é "1 disco em 1 AZ"