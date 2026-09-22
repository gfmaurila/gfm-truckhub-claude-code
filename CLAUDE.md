# GFM TruckHub — CLAUDE.md

## Missão
Construir um novo GFM TruckHub para Euro Truck Simulator 2 e American Truck Simulator a partir dos layouts fornecidos em `references/screens/`.

## REGRA MÁXIMA — UI FIRST
Antes de implementar regras reais, o sistema Desktop inteiro deve existir, abrir e ser 100% navegável usando JSON de mock.

Ordem obrigatória:
1. Pesquisa técnica.
2. Arquitetura.
3. Separação completa das tasks.
4. Implementar TODAS as telas aprovadas.
5. Tornar TODO o Desktop navegável.
6. Alimentar TODAS as telas com JSON mock.
7. Validar fidelidade visual aos layouts.
8. Executar o Desktop para validação do Product Owner.
9. PARAR e aguardar aprovação explícita.
10. Somente depois implementar Domain/CQRS, extração real, persistência real, jobs, graph/routing, telemetria e integrações.

NUNCA pule o Quality Gate visual.

## Layouts
Os PNGs em `references/screens/` são ESPECIFICAÇÃO VISUAL, não inspiração.
- Não redesenhar.
- Não simplificar.
- Não remover campos.
- Não alterar hierarquia visual sem solicitação.
- Reproduzir os layouts o mais fielmente possível.

## Arquitetura alvo
- .NET Desktop / WPF / MVVM
- Domain puro
- Application com CQRS
- Contracts
- Infrastructure
- armazenamento local JSON inicialmente
- jobs internos do Desktop inicialmente
- Map Extractor ETS2/ATS
- Graph / Routing
- Telemetry Provider real + mock
- API é evolução posterior quando necessária
- Docker NÃO é requisito do Core/Rotas
- Docker Compose é permitido/previsto para n8n e automações

## Offline First
Rotas deve funcionar sem Docker, PostgreSQL, Redis, n8n ou servidor externo.

## Game Environment
### Instalação
Detectar automaticamente ao iniciar o programa.
Local típico Steam:
`C:\Program Files (x86)\Steam\steamapps\common\`
- `Euro Truck Simulator 2`
- `American Truck Simulator`

Não assumir somente C:. Detectar Steam Libraries em outros discos.

### Perfil/dados definidos pelo usuário
O usuário configura separadamente:
- `D:\Work\Euro Truck Simulator 2`
- `D:\Work\American Truck Simulator`

Instalação do jogo e pasta de perfil/dados são conceitos diferentes.
Todos os caminhos devem aceitar detecção, validação, persistência e alteração.

## Pesquisa obrigatória antes do Map Extractor
Pesquisar como ferramentas/ecossistema ETS2/ATS extraem e estruturam mapas.
Estudar conceitos e formatos usados por:
- SCS Game Archive / HashFS
- MapExporter
- TruckSim Maps
- TsMap
- TruckLib
- formatos de sector/prefab/SII
- base game + DLC
- mods + load order + overrides

Não copiar implementação de terceiros sem análise de licença.
Gerar documentação e decisões antes do código real.

## Mapa efetivo
O objetivo é representar o mapa realmente carregado:
Base Game + DLCs instaladas + Mods ativos + ordem/prioridade + overrides.

## Storage inicial
JSON local, particionado quando necessário:
- config
- maps
- sectors
- routes
- history
- telemetry
- imports

Implementar abstrações de repository para permitir trocar JSON por outro storage futuramente sem contaminar Domain/Application.

## Jobs internos
Inicialmente podem rodar no processo Desktop:
- GameInstallationScanJob
- GameVersionDetectionJob
- DlcDetectionJob
- ModDetectionJob
- MapChangeDetectionJob
- MapExtractionJob
- MapIndexJob
- TelemetryPollingJob
- RouteProgressJob
- AutoSaveJob

Jobs pesados devem ser canceláveis, observáveis e não bloquear a UI.

## Módulos futuros
Planejar agora, desenvolver somente na fase correspondente:
- Rotas
- Live Assistant
- Narration Engine
- n8n Automation
- GFM Crazy Traffic

## n8n
n8n/automação de voz mantém Docker Compose.
Falha/ausência do Docker não pode impedir o Core/Rotas de iniciar.

## Regra de execução
Uma task por vez.
Nunca iniciar automaticamente a próxima task.
Ao concluir:
- build
- testes aplicáveis
- `git diff --check`
- relatório
- STOP

Mudança visual exige validação manual do Product Owner.


## Canonical file naming

Project-owned files and folders use lowercase kebab-case unless the tool requires a fixed filename.
Claude Code fixed entry files remain uppercase where conventional, e.g. `CLAUDE.md`.

Visual references are grouped by module:
- `references/screens/core/`
- `references/screens/routes/`
- `references/screens/live-assistant/`
- `references/screens/automation-n8n/`
- `references/screens/crazy-traffic/`

Screen filenames use a sortable numeric prefix plus a semantic English slug:
`010-dashboard.png`, `030-route-editor.png`, `090-hud.png`.

Before implementing any UI task, read:
- `docs/screens/SCREEN-CATALOG.md`
- the relevant module images
- relevant notes under `docs/screens/notes/`

Never infer a screen from its filename alone: inspect the actual image before coding.
