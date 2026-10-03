# GFM.TruckHub — Estrutura Oficial

Esta é a estrutura física alvo do TruckHub. Ela preserva o Desktop WPF e prepara capacidades backend/cloud sem obrigar sua implementação antecipada.

```text
GFM.TruckHub/
├── backend/
│   ├── src/
│   │   ├── api/GFM.TruckHub.API/             # PLANNED quando houver necessidade comprovada
│   │   └── core/
│   │       ├── GFM.TruckHub.Domain/
│   │       ├── GFM.TruckHub.Application/
│   │       ├── GFM.TruckHub.Infrastructure/
│   │       └── GFM.TruckHub.CrossCutting/
│   ├── workers/
│   ├── batch/
│   └── tools/
├── frontend/                                  # reservado para web, se aprovado
├── mobile/                                    # reservado, se aprovado
├── tests/
│   ├── unit/
│   ├── integration/
│   ├── architecture/
│   └── e2e/
├── infrastructure/
│   ├── aws/
│   ├── docker/
│   ├── observability/
│   └── opentofu/
├── deploy/
│   ├── aws/
│   └── docker/
├── data/mock/                                 # mocks existentes preservados
├── docs/
│   ├── architecture/drawio/
│   ├── architecture/exports/
│   ├── adr/
│   ├── reports/
│   └── screens/
├── references/                                # metadados/referências leves
├── tasks/                                     # fluxo atual preservado
├── scripts/
├── tools/
├── .claude/                                   # agentes, skills, rules, commands
├── .github/workflows/
├── prompts.md
├── PROJECT_STRUCTURE.md
├── PROJECT_SKILLS.md
├── PROJECT-STATE.md
├── CLAUDE.md
└── README.md
```

## Dependências

`UI/Desktop → Application → Domain` e `Infrastructure → Application/Domain`. Domain não referencia WPF, AWS, Docker, n8n, JSON, HTTP ou SDK de jogo.

## AWS

AWS é `CLOUD TARGET`, não requisito do modo local. Infrastructure as Code deve ficar em `infrastructure/opentofu/`; documentação AWS em `infrastructure/aws/`; artefatos de implantação em `deploy/aws/`.

## Diagramas

Fonte oficial: `docs/architecture/drawio/*.drawio`. Exportações: `docs/architecture/exports/`. Não substituir fonte editável por screenshot.

## Bootstrap de Agents — fonte obrigatória

A estrutura inicial de Agents/Skills não deve ser inventada diretamente pelo projeto.

Fonte local obrigatória:

`D:\Empresa\GFMaurila\projetos\gfm-truckhub-claude-code\references\Kit-IA-Dev.zip`

O fluxo de bootstrap está definido em `prompts.md` e detalhado em `docs/agents/AGENTS-BOOTSTRAP-KIT-IA-DEV.md`.
A estrutura gerada a partir do Kit deve ser especializada para o TruckHub sem alterar a ideia de negócio.

## Desenho de infraestrutura AWS

- `docs/architecture/GFM-TruckHub-AWS-Infrastructure.drawio` — fonte editável Draw.io.
- `docs/architecture/AWS-INFRASTRUCTURE.md` — contrato textual da infraestrutura target.

Qualquer mudança relevante de infraestrutura deve atualizar ambos.
