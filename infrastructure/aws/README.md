# AWS Target Architecture

O GFM TruckHub é **offline/local first**. A AWS complementa capacidades que precisem de sincronização, APIs, processamento assíncrono, observabilidade ou serviços compartilhados.

| Capacidade | AWS alvo | Estado inicial |
|---|---|---|
| Object storage | S3 | PLANNED |
| Filas | SQS | OPTIONAL |
| Pub/Sub | SNS | OPTIONAL |
| Event processing | Lambda | OPTIONAL |
| Containers | ECS/Fargate + ECR | PLANNED |
| VM dedicada | EC2 | OPTIONAL |
| Relacional | RDS | OPTIONAL |
| Cache | ElastiCache/Redis | OPTIONAL |
| Secrets | Secrets Manager / Parameter Store | PLANNED |
| Observabilidade | CloudWatch + OpenTelemetry | PLANNED |
| Identidade de workloads | IAM | PLANNED |
| IaC | OpenTofu | PLANNED |

Nenhum item desta tabela deve ser tratado como implementado sem código/IaC e Quality Gate correspondente.
