# Projetos de Portfolio

> Cada projeto = 1 repositório GitHub com:
> - README (diagrama, descrição, como rodar)
> - Terraform (infra)
> - Código (app, se houver)
> - Diagrama (draw.io exportado em PNG)

## Projeto 1: Landing Page (Simples)
- [ ] S3 + CloudFront + Route 53
- [ ] Terraform para tudo
- [ ] HTTPS (ACM + CloudFront)
- [ ] **Aprende:** S3, CloudFront, DNS, TLS, Terraform básico

## Projeto 2: Web App 3-Tier (Médio)
- [ ] VPC (2 public + 2 private subnets)
- [ ] ALB → 2 EC2 (ASG) → RDS PostgreSQL (Multi-AZ)
- [ ] S3 para uploads
- [ ] ElastiCache Redis
- [ ] CloudWatch + alarms
- [ ] **Aprende:** VPC, ALB, ASG, RDS, caching, monitoring

## Projeto 3: Serverless API (Médio)
- [ ] API Gateway → Lambda → DynamoDB
- [ ] S3 para logs
- [ ] CloudWatch + X-Ray
- [ ] Terraform
- [ ] **Aprende:** serverless, NoSQL, API design

## Projeto 4: DR Cross-Region (Avançado)
- [ ] Stack em us-east-1 (VPC + EC2 + RDS + S3)
- [ ] DR em us-west-2 (Pilot Light)
- [ ] S3 CRR + RDS Cross-Region Replica
- [ ] Route 53 Failover
- [ ] Script de failover (Lambda + Step Functions)
- [ ] **Aprende:** DR, RTO/RPO, cross-region, automação

## Projeto 5: Container + CI/CD (Avançado)
- [ ] Dockerfile + ECR
- [ ] ECS Fargate (ou EKS)
- [ ] GitHub Actions → build → push → deploy
- [ ] ALB + autoscaling
- [ ] **Aprende:** containers, CI/CD, orchestration

## Projeto 6: Data Pipeline (Avançado)
- [ ] S3 (raw) → Glue (ETL) → Athena (query)
- [ ] Kinesis (streaming)
- [ ] Redshift (analytics)
- [ ] **Aprende:** data engineering, ETL, analytics

## Projeto 7: Multi-Tenant SaaS (Expert)
- [ ] Cognito (auth)
- [ ] API Gateway + Lambda
- [ ] DynamoDB (tenant isolation)
- [ ] S3 (per tenant)
- [ ] CloudFront + WAF
- [ ] Terraform + modules
- [ ] **Aprende:** multi-tenancy, auth, scaling, security

---

## Regra: 1 projeto a cada 2-3 semanas

| Semana | Projeto |
|--------|---------|
| 1-2 | Projeto 1 (Landing Page) |
| 3-5 | Projeto 2 (3-Tier) |
| 6-8 | Projeto 3 (Serverless) |
| 9-11 | Projeto 4 (DR) |
| 12-14 | Projeto 5 (Containers) |
| 15-17 | Projeto 6 (Data) |
| 18-20 | Projeto 7 (SaaS) |

> Ao final: 7 projetos no GitHub = portfolio sólido.
> Mais forte que 90% dos "cloud architects" que só têm certificação.