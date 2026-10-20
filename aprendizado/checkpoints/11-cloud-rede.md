# Cloud Networking (AWS)

## VPC (Virtual Private Cloud)
- [ ] Sabe o que é uma VPC
- [ ] Sabe criar VPC com CIDR (ex: 10.0.0.0/16)
- [ ] Sabe o que é uma Subnet (public vs. private)
- [ ] Sabe o que é uma Route Table
- [ ] Sabe o que é um Internet Gateway (IGW)
- [ ] Sabe o que é um NAT Gateway
- [ ] Sabe o que é um NAT Instance
- [ ] Sabe a diferença entre IGW e NAT
- [ ] Sabe o que é um VPC Peering
- [ ] Sabe o que é um Transit Gateway
- [ ] Sabe o que é AWS Direct Connect
- [ ] Sabe o que é Site-to-Site VPN
- [ ] Sabe o que é Client VPN

## Security Groups e NACLs
- [ ] Sabe o que é um Security Group (stateful)
- [ ] Sabe o que é uma NACL (stateless)
- [ ] Sabe a diferença entre os dois
- [ ] Sabe criar SG com regras (allow/deny, inbound/outbound)
- [ ] Sabe o que é "least privilege" em rede
- [ ] Sabe o que é uma port (80, 443, 22, 3306, 5432)

## Load Balancing
- [ ] Sabe o que é um ELB (Elastic Load Balancer)
- [ ] Sabe a diferença entre ALB, NLB, GLB
- [ ] Sabe o que é health check
- [ ] Sabe o que é sticky session
- [ ] Sabe o que é target group
- [ ] Sabe o que é blue/green deployment (conceito)

## DNS
- [ ] Sabe o que é Route 53
- [ ] Sabe o que é um record (A, AAAA, CNAME, MX, TXT)
- [ ] Sabe o que é DNS failover
- [ ] Sabe o que é latency-based routing
- [ ] Sabe o que é health check no Route 53

## Prática
- [ ] Criar VPC com 2 subnets públicas + 2 privadas
- [ ] Lançar EC2 em subnet pública (com IGW)
- [ ] Lançar EC2 em subnet privada (com NAT)
- [ ] Criar ALB na frente de 2 EC2s
- [ ] Configurar Security Group (só 80/443 aberto)
- [ ] Registrar domínio no Route 53
- [ ] Desenhar o diagrama (draw.io ou Lucidchart)