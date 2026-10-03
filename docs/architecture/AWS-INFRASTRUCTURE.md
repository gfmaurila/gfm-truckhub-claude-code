# GFM TruckHub — Infraestrutura AWS

## Princípio

**Local First → Container First → AWS Cloud Ready**

O GFM TruckHub Desktop deve continuar funcional localmente. A AWS é o alvo de evolução cloud e não uma dependência obrigatória para iniciar o aplicativo.

## Desenho editável

Abra no diagrams.net / Draw.io:

`docs/architecture/GFM-TruckHub-AWS-Infrastructure.drawio`

## Camadas representadas

### Local / Driver
- GFM TruckHub Desktop — WPF / .NET 10
- Map Extractor e Routing
- Telemetry e Live Assistant
- Crazy Traffic e integrações
- persistência/cache local para operação offline

### Edge / entrada AWS
- Route 53
- CloudFront
- API Gateway e/ou Application Load Balancer

### Compute
- ECS + Fargate para APIs e serviços containerizados
- Lambda para processamento orientado a eventos quando adequado
- Workers/Jobs para telemetria, mapas e processamento
- n8n para integrações quando aplicável

### Eventos
- SQS
- SNS

### Dados e storage
- RDS para dados relacionais quando a fase cloud exigir
- ElastiCache/Redis para cache distribuído
- S3 para mapas, artefatos, arquivos e dados
- Secrets Manager
- KMS

### Observabilidade e segurança
- CloudWatch
- OpenTelemetry
- IAM
- WAF / Security Groups

### CI/CD e infraestrutura como código
- GitHub Actions
- Amazon ECR
- OpenTofu
- ambientes dev / hml / prod

## Regra de implementação

O diagrama representa a arquitetura **target/cloud-ready**. Um serviço desenhado não deve ser documentado como já implementado enquanto não existir código, configuração IaC e validação correspondentes.
