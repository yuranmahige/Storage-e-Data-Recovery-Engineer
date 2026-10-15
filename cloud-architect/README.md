# Roadmap: Cloud Architect

> **Perfil:** Profissional que desenha, implementa e gerencia
> infraestrutura em nuvem — com profundidade real em storage,
> recuperação de dados e automação.
>
> **Stack principal:** AWS (foco) · Terraform · Python · Bash · Docker
>
> **Diferencial:** Não é "cloud que clica na console".
> Entende o que acontece por baixo do disco, do byte, do setor.
> Sabe o que é erasure coding porque já entendeu RAID 5/6.
> Sabe o que é replication porque já montou RAID 1.
> Sabe o que é versioning porque já fez snapshot LVM.
>
> **Pré-requisito:** Concluir o roadmap de Storage & Data Recovery (01-07)

---

## Conexão com o que você já vai saber

| Storage (Part 1) | Cloud (Part 2) |
|------------------|----------------|
| Setor, trilha, cilindro | EBS (block storage), S3 (object) |
| RAID 1 (espelho) | Replication (multi-AZ, cross-region) |
| RAID 5/6 (parity) | Erasure coding (S3, EBS internal) |
| LVM snapshot | EBS snapshot, S3 versioning |
| S.M.A.R.T. / health check | CloudWatch, EBS metrics |
| ddrescue / recuperação | S3 lifecycle, Glacier, DR strategies |
| ZFS / Btrfs (copy-on-write) | S3 (immutability), EBS (copy-on-write snapshots) |
| `mdadm` (RAID software) | EBS multi-AZ, RDS multi-AZ |
| `smartctl` + Prometheus | CloudWatch + Grafana (cloud) |

---

## Estrutura do Estudo

```
estudos/cloud/
├── README.md                  ← este arquivo
├── 10-cloud-fundamentos.md    ← conceitos, modelos, provider
├── 11-cloud-rede.md           ← VPC, subnets, SG, LB, DNS
├── 12-cloud-storage.md        ← S3, EBS, EFS, Glacier, versioning
├── 13-cloud-compute.md        ← EC2, Lambda, ECS, autoscaling
├── 14-cloud-dados.md          ← RDS, DynamoDB, Aurora, ElastiCache
├── 15-cloud-seguranca.md      ← IAM, KMS, encryption, compliance
├── 16-iac-devops.md           ← Terraform, CI/CD, Docker
├── 17-architectura.md         ← Well-Architected, DR, HA, patterns
└── 18-projetos.md             ← projetos práticos (portfolio)
```

---

## Roadmap (ordem de estudo)

| Fase | Arquivo | Foco | Duração |
|------|---------|------|---------|
| 1 | 10 | Fundamentos + AWS Free Tier | 2-3 semanas |
| 2 | 11 | Rede (VPC, subnets, SG, LB) | 3-4 semanas |
| 3 | 12 | **Storage em cloud** (seu forte) | 2-3 semanas |
| 4 | 13 | Compute (EC2, Lambda, ECS) | 3-4 semanas |
| 5 | 14 | Dados (RDS, DynamoDB, Aurora) | 2-3 semanas |
| 6 | 15 | Segurança + IAM | 2-3 semanas |
| 7 | 16 | Terraform + CI/CD + Docker | 4-6 semanas |
| 8 | 17 | Arquitetura (Well-Architected, DR, HA) | 3-4 semanas |
| 9 | 18 | Projetos de portfolio | Contínuo |

> **Fases 3 e 4 andam juntas.** Storage e compute são inseparáveis
> na prática (EC2 + EBS, Lambda + S3, etc.)

---

## Certificações (caminho recomendado)

| Ordem | Certificação | Foco | Custo |
|-------|-------------|------|-------|
| 1 | **AWS Cloud Practitioner (CLF-C02)** | Fundamentos | ~$100 |
| 2 | **AWS Solutions Architect Associate (SAA-C03)** | Core (rede, storage, compute, IAM) | ~$150 |
| 3 | **AWS Solutions Architect Professional (SAP-C02)** | Arquitetura avançada, DR, multi-region | ~$300 |
| 4 | **AWS Storage Specialty (SAP-S01)** | **Seu nicho** — storage em profundidade | ~$300 |
| 5 | **Terraform Associate (003)** | IaC | ~$242 |
| 6 | **AWS DevOps Engineer Professional** (opcional) | CI/CD, automação | ~$300 |

> **Prioridade:** SAA-C03 → SAP-C02 → Storage Specialty.
> O Storage Specialty é o que diferencia você no mercado.
> Pouquíssimos cloud architects têm.

---

## Regras (mesmas da Part 1)

1. **AWS Free Tier é seu laboratório.** Use, quebre, apague.
2. **Terraform para TUDO.** Nada de clicar na console depois da Fase 1.
3. **Projeto > teoria.** A cada 2 semanas, 1 arquitetura no GitHub.
4. **Documente.** Cada projeto vira um README com diagrama.
5. **Conecte com Part 1.** Sempre que ver um conceito cloud,
   pense "isso é equivalente a X no meu mundo de storage".

---

## Início (quando terminar Part 1)

- [ ] Criar conta AWS + Free Tier
- [ ] Instalar AWS CLI, Terraform, Docker na VM
- [ ] Criar repositório GitHub `cloud-projects/`
- [ ] Começar Fase 1 (fundamentos)
- [ ] **Não** tentar aprender Azure/GCP ainda. AWS primeiro, depois expande.
