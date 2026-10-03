# GFM.TruckHub

# ORQUESTRAÇÃO PRINCIPAL — REFATORAÇÃO, ARQUITETURA, DESENVOLVIMENTO E VALIDAÇÃO

Fale sempre em Português do Brasil (PT-BR).


## Fase 0 — Bootstrap obrigatório do Kit IA Dev

Antes de gerar, alterar ou executar qualquer Agent/Skill deste projeto, use obrigatoriamente o pacote:

`D:\Empresa\GFMaurila\projetos\gfm-truckhub-claude-code\references\Kit-IA-Dev.zip`

### Ordem obrigatória

1. Validar que `Kit-IA-Dev.zip` existe exatamente no caminho acima.
2. Não mover, renomear ou sobrescrever o ZIP de referência.
3. Abrir/extrair o pacote em uma área temporária de trabalho.
4. Ler primeiro a documentação de instalação e bootstrap existente no próprio Kit.
5. Identificar no Kit a estrutura padrão de **Agents**, **Agent Skills (`SKILL.md`)**, instruções, templates e convenções.
6. Detectar a ferramenta de IA em execução e respeitar o local/padrão de Agents/Skills suportado por ela.
7. Usar o Kit como fonte estrutural para gerar os Agents do **GFM TruckHub**.
8. Especializar os Agents para o domínio TruckHub e para os contratos definidos em `PROJECT_STRUCTURE.md`, `PROJECT_SKILLS.md`, `CLAUDE.md` e `PROJECT-STATE.md`.
9. Somente após concluir esse bootstrap iniciar análise, geração de código ou refatoração.
10. Registrar na documentação de execução quais componentes do Kit foram utilizados.

### Regra de precedência

O `Kit-IA-Dev.zip` define o padrão inicial de construção/orquestração dos Agents e Skills.  
Os documentos do GFM TruckHub definem o domínio, arquitetura, restrições e resultado esperado.

Não substituir regras de negócio do TruckHub por exemplos genéricos do Kit e não transformar conteúdo de exemplo do Kit em funcionalidade do produto.

## 1. Objetivo

Refatorar e evoluir o **GFM.TruckHub** preservando integralmente sua ideia de negócio para Euro Truck Simulator 2 (ETS2) e American Truck Simulator (ATS). A nova organização física e os padrões de infraestrutura seguem o modelo arquitetural padronizado do projeto, com **AWS como cloud target**.

A refatoração NÃO transforma o TruckHub em CMS e NÃO autoriza remover funcionalidades, tasks, mocks, referências visuais ou decisões de produto existentes.

## 2. Fontes de verdade

Leia nesta ordem:

1. `prompts.md`
2. `PROJECT-STATE.md`
3. `PROJECT_STRUCTURE.md`
4. `PROJECT_SKILLS.md`
5. `CLAUDE.md`
6. `tasks/CURRENT.md`
7. task atual
8. regras e skills aplicáveis em `.claude/`
9. documentação e referências em `docs/` e `references/`

## 3. Princípios obrigatórios

```text
BUSINESS PRESERVED
      ↓
UI FIRST
      ↓
LOCAL / OFFLINE FIRST
      ↓
CONTAINER READY
      ↓
CLOUD READY
      ↓
AWS TARGET
```

- Desktop continua sendo .NET 10 + WPF/MVVM.
- Domain permanece puro.
- Application utiliza CQRS.
- Infrastructure implementa portas e integrações.
- ATS/ETS2 ficam atrás de contratos substituíveis.
- Rotas essenciais devem continuar funcionando offline.
- AWS é alvo de infraestrutura e capacidades cloud; não deve quebrar o modo local.
- Não criar API, banco, fila ou container apenas para preencher estrutura.
- Todo estado planejado deve ser identificado como PLANNED/OPTIONAL até existir implementação real.

## 4. Capacidades do negócio preservadas

- Desktop/UI e navegação com mocks;
- descoberta/configuração ETS2 e ATS;
- Map Extractor;
- Graph e Routing;
- rotas multi-stop;
- Telemetry Provider real + mock;
- Live Assistant;
- automações n8n;
- Crazy Traffic;
- referências visuais externas;
- desenvolvimento orientado por tasks e Quality Gates.

## 5. AWS Target

Serviços AWS são selecionados por necessidade, nunca por obrigação. Alvos previstos:

- Amazon S3: objetos, artefatos e dados apropriados;
- Amazon SQS/SNS: filas/eventos assíncronos quando necessários;
- AWS Lambda: processamento event-driven pontual;
- Amazon ECS/Fargate: serviços containerizados quando houver backend cloud;
- Amazon EC2: somente quando workload exigir host dedicado;
- Amazon RDS: persistência relacional cloud quando necessária;
- Amazon ElastiCache/Redis: cache distribuído quando necessário;
- AWS Secrets Manager / Parameter Store: secrets/configuração;
- Amazon CloudWatch + OpenTelemetry: logs, métricas e traces;
- Amazon ECR: imagens de containers;
- IAM: least privilege;
- OpenTofu: Infrastructure as Code.

## 6. Arquitetura e diagramas

A segunda atividade após validar/criar a estrutura é atualizar a arquitetura. Os arquivos-fonte oficiais dos desenhos devem ser `.drawio` em `docs/architecture/drawio/`. PNG/SVG/PDF são exportações. Diagramas devem distinguir claramente `IMPLEMENTED`, `PLANNED`, `OPTIONAL`, `LOCAL ONLY` e `AWS ONLY`.

Diagramas mínimos: Contexto, Containers, Componentes principais, fluxo Routing/Map, Telemetry, AWS Target e Deployment.

## 7. UI First e Quality Gate

A regra de `CLAUDE.md` continua soberana: antes das regras reais, todas as telas aprovadas devem existir, navegar e usar mocks determinísticos, com validação visual do Product Owner. Depois do gate, evoluir Domain/CQRS, Map Extractor, persistência, routing, telemetria e integrações.

## 8. Referências externas

Raiz canônica das imagens pesadas:

`D:\Empresa\GFMaurila\projetos\gfm-truckhub-claude-code-zip\references\screens`

Nunca inventar conteúdo de referência indisponível.

## 9. Ordem de execução

```text
01 Validar documentação existente
02 Validar estrutura oficial
03 Preservar negócio/tasks/mocks/referências
04 Atualizar arquitetura e Draw.io
05 Architecture Quality Gate
06 Executar a task corrente
07 Implementar somente o necessário
08 Testes e gates
09 Atualizar documentação/diagramas/PROJECT-STATE
10 STOP
```

Falha em gate significa trabalho não concluído. Nunca avançar automaticamente para a próxima task.

## Gate de documentação de infraestrutura

Ao alterar arquitetura/infraestrutura AWS, atualizar obrigatoriamente `docs/architecture/GFM-TruckHub-AWS-Infrastructure.drawio` e `docs/architecture/AWS-INFRASTRUCTURE.md`. O desenho deve permanecer editável em Draw.io e refletir somente o que é atual ou explicitamente marcado como target/planejado.
