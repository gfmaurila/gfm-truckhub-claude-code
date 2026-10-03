# GFM.TruckHub — Skills do Projeto

As skills existentes em `.claude/skills/` continuam válidas. A refatoração acrescenta responsabilidades transversais que qualquer agente deve respeitar.

## Skills principais

- `project-orchestration`: task atual, gates, relatórios e STOP.
- `dotnet-architecture`: .NET 10, Domain, Application/CQRS, Infrastructure e WPF/MVVM.
- `wpf-ui`: UI First, navegação e mocks.
- `ats-ets-environment`: instalações, profiles e segurança read-only.
- `map-extraction`: extração/mapas ETS2/ATS.
- `telemetry`: providers real/mock e contratos.
- `testing-quality-gates`: unit/integration/architecture/e2e e gates.
- `security-review`: secrets, least privilege e dependências.
- `documentation`: README, ADRs, reports e sincronização documental.

## Responsabilidades adicionais

### project-architecture
Preservar boundaries, estrutura física, offline-first e evolução Local → Cloud. Impedir infraestrutura antecipada sem requisito.

### aws-cloud-architecture
Orientar S3, SQS, SNS, Lambda, ECS/Fargate, EC2, RDS, ElastiCache, ECR, IAM, Secrets Manager, CloudWatch e OpenTelemetry. Toda escolha deve registrar motivação e estado (PLANNED/IMPLEMENTED/OPTIONAL).

### infrastructure-as-code
OpenTofu como fonte de IaC AWS. Proibir secrets hardcoded e exigir ambientes/variáveis explícitos.

### architecture-as-code
Manter desenhos editáveis em Draw.io e documentação coerente com a implementação. PNG/SVG/PDF são exportações.

### architecture-quality-gate
Validar estrutura, dependências, diagramas, estados arquiteturais, segurança, observabilidade e infraestrutura antes de considerar alteração arquitetural concluída.

## Origem da estrutura de Agents e Skills

Antes de criar ou reorganizar Agents/Skills, consultar obrigatoriamente:

`D:\Empresa\GFMaurila\projetos\gfm-truckhub-claude-code\references\Kit-IA-Dev.zip`

O Kit IA Dev é a referência de estrutura e convenções. Este arquivo continua sendo o contrato de especialização das Skills do GFM TruckHub.
Consulte também `docs/agents/AGENTS-BOOTSTRAP-KIT-IA-DEV.md`.
