## Resumo: Ordem de Estudo

| Ordem | Arquivo | Recurso principal | Custo |
|-------|---------|-------------------|-------|
| 1 | 10 | AWS Cloud Practitioner Essentials (grátis) | Grátis |
| 2 | 11 | SAA-C03 (Stephane Maarek) + VPC course | ~$30 |
| 3 | 12 | AWS Storage (Stephane Maarek) + docs S3 | ~$15 |
| 4 | 13 | SAA-C03 + Docker/K8s (freeCodeCamp) | ~$0 |
| 5 | 14 | AWS Databases (Stephane Maarek) | ~$15 |
| 6 | 15 | AWS Security (Stephane Maarek) | ~$15 |
| 7 | 16 | HashiCorp Learn (grátis) + Terraform Associate | ~$15 |
| 8 | 17 | Well-Architected (grátis) + SAP-C02 (Stephane Maarek) | ~$15 |
| 9 | 18 | Projetos (AWS Free Tier) | ~$0-50/mês |

### Certificações (ordem)
| Ordem | Certificação | Custo | Quando |
|-------|-------------|-------|--------|
| 1 | CLF-C02 (Cloud Practitioner) | $100 | Após Fase 1 |
| 2 | SAA-C03 (Solutions Architect Associate) | $150 | Após Fases 2-6 |
| 3 | Terraform Associate (003) | $242 | Após Fase 7 |
| 4 | SAP-C02 (Solutions Architect Professional) | $300 | Após Fases 7-8 + 6 meses |
| 5 | SAP-S01 (Storage Specialty) | $300 | Após SAP-C02 |

### Total estimado
| Item | Custo |
|------|-------|
| Cursos Udemy (Stephane Maarek, 5-6) | ~$75-100 |
| Certificações (CLF + SAA + TF + SAP + Storage) | ~$1.092 |
| AWS Free Tier (projetos) | $0-50/mês |
| Livros (Kleppmann, Terraform, Docker) | ~$150-200 |
| **Total** | **~$1.300-1.500** |

> Dica: o Stephane Maarek SAA-C03 (~$15) cobre 70% das Fases
> 11-15. É o investimento com melhor ROI.
> O AWS Free Tier cobre os projetos.
> O HashiCorp Learn cobre Terraform.
> O Well-Architected Framework cobre arquitetura.
> **Tudo grátis ou quase.**
```

---

## Como as duas partes se conectam

```
┌─────────────────────────────────────────────────────────────┐
│                    SUA "FACULDADE"                          │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  PART 1: Storage & Data Recovery                           │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 01. Informática Básica                               │   │
│  │ 02. Linux Básico                                     │   │
│  │ 03. Armazenamento (partições, fs, LVM, RAID)         │   │
│  │ 04. Manutenção de Discos (SMART, setores)            │   │
│  │ 05. Recuperação de Dados (TestDisk, carving)         │   │
│  │ 06. Avançado (forense, ZFS, Btrfs)                   │   │
│  │ 07. Programação (Python, Bash, ferramentas)          │   │
│  └─────────────────────────────────────────────────────┘   │
│                         │                                   │
│                         ▼ (conhecimento se transfere)       │
│                                                             │
│  PART 2: Cloud Architect                                    │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 10. Cloud Fundamentos                                │   │
│  │ 11. Cloud Networking (VPC, LB, DNS)                  │   │
│  │ 12. Cloud Storage (S3, EBS, EFS) ← SEU FORTE        │   │
│  │ 13. Cloud Compute (EC2, Lambda, ECS)                 │   │
│  │ 14. Cloud Data (RDS, DynamoDB, Aurora)               │   │
│  │ 15. Cloud Security (IAM, KMS, WAF)                   │   │
│  │ 16. IaC + DevOps (Terraform, CI/CD, Docker)          │   │
│  │ 17. Arquitetura (Well-Architected, DR, HA)           │   │
│  │ 18. Projetos (portfolio)                             │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
│  RESULTADO: Storage & Cloud Engineer                        │
│  (entende do byte ao bucket, do setor ao S3)                │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Dica final

Quando chegar na Fase 12 (Cloud Storage), você vai ter uma vantagem absurda:

- O cara comum vê "S3 é object storage, é bom, é barato"
- **Você** vai ver: "S3 usa erasure coding (RAID 6 distribuído), replica em 3+ AZs, faz versioning (snapshot LVM), tem lifecycle (mover para arquivamento), object lock (WORM), e o custo por GB é X porque não tem IOPS para pagar"

Isso te diferencia de 95% dos cloud architects. Você não está "aprendendo cloud" — você está **expandindo** o que já sabe para um novo contexto.

Boa faculdade. 🎓