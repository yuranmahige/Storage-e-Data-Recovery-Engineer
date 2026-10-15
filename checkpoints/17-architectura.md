# Arquitetura de Cloud

## Well-Architected Framework (6 pilares)
- [ ] **Operational Excellence** — automação, monitoring, incident response
- [ ] **Security** — IAM, encryption, network security, compliance
- [ ] **Reliability** — HA, failover, DR, multi-AZ/region
- [ ] **Performance Efficiency** — right-sizing, caching, scaling
- [ ] **Cost Optimization** — reserved, spot, lifecycle, rightsizing
- [ ] **Sustainability** — energia, região, right-sizing

## Disaster Recovery (DR)
- [ ] Sabe os 4 níveis:
  - **Backup and Restore** (RPO: horas, RTO: horas)
  - **Pilot Light** (RPO: minutos, RTO: horas)
  - **Warm Standby** (RPO: minutos, RTO: minutos)
  - **Multi-Site Active/Active** (RPO: 0, RTO: 0)
- [ ] Sabe o que é RTO (Recovery Time Objective)
- [ ] Sabe o que é RPO (Recovery Point Objective)
- [ ] Sabe o que é RDS Multi-AZ (failover automático)
- [ ] Sabe o que é RDS Cross-Region Read Replica
- [ ] Sabe o que é S3 CRR (cross-region replication)
- [ ] Sabe o que é EBS Cross-Region Copy
- [ ] Sabe o que é Route 53 Failover
- [ ] Sabe o que é AWS Elastic Disaster Recovery
- [ ] Sabe o que é AWS Backup Cross-Region
- [ ] Sabe o que é Chaos Engineering (conceito)

## High Availability (HA)
- [ ] Sabe o que é single point of failure
- [ ] Sabe o que é multi-AZ (redundância)
- [ ] Sabe o que é multi-region (geographic redundancy)
- [ ] Sabe o que é load balancing (ALB/NLB)
- [ ] Sabe o que é Auto Scaling (resiliência)
- [ ] Sabe o que é health check + auto-replacement
- [ ] Sabe o que é circuit breaker (padrão)
- [ ] Sabe o que é retry with backoff (padrão)

## Architecture Patterns
- [ ] Sabe o que é 3-Tier Architecture (web, app, data)
- [ ] Sabe o que é Microservices (conceito)
- [ ] Sabe o que é Event-Driven Architecture
- [ ] Sabe o que é Serverless Architecture
- [ ] Sabe o que é CQRS (Command Query Responsibility Segregation)
- [ ] Sabe o que é Saga Pattern
- [ ] Sabe o que é Sidecar Pattern
- [ ] Sabe o que é API Gateway Pattern
- [ ] Sabe o que é Service Mesh (conceito)

## Cost Optimization
- [ ] Sabe o que é AWS Cost Explorer
- [ ] Sabe o que é AWS Budgets
- [ ] Sabe o que é AWS Trusted Advisor
- [ ] Sabe o que é Reserved Instances vs. Savings Plans
- [ ] Sabe o que é Spot Instances (e quando usar)
- [ ] Sabe o que é S3 Lifecycle (reduzir custo)
- [ ] Sabe o que é Right-Sizing (CloudWatch + Compute Optimizer)
- [ ] Sabe o que é FinOps (conceito)

## Prática
- [ ] Desenhar arquitetura 3-Tier (draw.io)
- [ ] Desenhar DR: Pilot Light para RDS + S3
- [ ] Desenhar DR: Multi-Region Active/Active
- [ ] Implementar: RDS Multi-AZ + S3 CRR + Route 53 Failover
- [ ] Fazer cost analysis de uma stack (Cost Explorer)
- [ ] Otimizar: trocar On-Demand por Savings Plan + Spot
- [ ] **Projeto:** arquitetura HA multi-AZ + DR cross-region
      (documentar RTO/RPO de cada componente)