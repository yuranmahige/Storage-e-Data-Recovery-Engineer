# Infrastructure as Code + DevOps

## Terraform
- [ ] Sabe o que é Terraform (HCL, provider, state)
- [ ] Sabe o que é `terraform init`, `plan`, `apply`, `destroy`
- [ ] Sabe o que é um Provider (aws, azurerm, google)
- [ ] Sabe o que é um Resource vs. Data Source
- [ ] Sabe o que é uma Variable (input, output)
- [ ] Sabe o que é um Module
- [ ] Sabe o que é State (local, S3 backend, DynamoDB lock)
- [ ] Sabe o que é `terraform state` (mv, import, rm)
- [ ] Sabe o que é `terraform workspace`
- [ ] Sabe o que é `terraform fmt` e `terraform validate`
- [ ] Sabe o que é `terraform output`
- [ ] Sabe o que é `terraform import`
- [ ] Sabe o que é OpenTofu (fork aberto do Terraform)

## CloudFormation (AWS)
- [ ] Sabe o que é CloudFormation (YAML/JSON)
- [ ] Sabe a diferença entre Terraform e CloudFormation
- [ ] Sabe o que é um Stack
- [ ] Sabe o que é Stack Sets
- [ ] Sabe o que é Change Set
- [ ] Sabe o que é Drift Detection

## CI/CD
- [ ] Sabe o que é CI (Continuous Integration)
- [ ] Sabe o que é CD (Continuous Delivery/Deployment)
- [ ] Sabe o que é AWS CodePipeline
- [ ] Sabe o que é AWS CodeBuild
- [ ] Sabe o que é AWS CodeDeploy
- [ ] Sabe o que é GitHub Actions (alternativa)
- [ ] Sabe o que é Jenkins (alternativa)
- [ ] Sabe o que é Blue/Green Deployment
- [ ] Sabe o que é Canary Deployment
- [ ] Sabe o que é Rolling Update

## Docker + Containers
- [ ] Sabe o que é Dockerfile
- [ ] Sabe o que é `docker build`, `run`, `push`
- [ ] Sabe o que é Docker Compose
- [ ] Sabe o que é ECR (push/pull)
- [ ] Sabe o que é uma imagem multi-stage
- [ ] Sabe o que é container scanning (Trivy, Snyk)

## Prática
- [ ] Criar VPC + EC2 + S3 com Terraform
- [ ] Criar module reutilizável (VPC)
- [ ] Usar S3 backend + DynamoDB lock para state
- [ ] Criar pipeline: GitHub push → CodeBuild → CodeDeploy
- [ ] Criar Dockerfile + build + push para ECR
- [ ] Deploy de container com ECS + Terraform
- [ ] **Projeto:** stack completa (VPC + ALB + EC2 + RDS + S3)
      em 1 `terraform apply`