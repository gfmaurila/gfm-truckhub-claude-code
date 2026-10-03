# GFM TruckHub — Claude Code

## Missão
Construir o GFM TruckHub para Euro Truck Simulator 2 (ETS2) e American Truck Simulator (ATS), seguindo as tasks versionadas, a arquitetura aprovada e as referências visuais externas.

## Fonte de estado
Antes de qualquer alteração, leia nesta ordem:
1. `PROJECT-STATE.md`
2. `tasks/CURRENT.md`
3. a task apontada por `tasks/CURRENT.md`
4. regras relevantes em `.claude/rules/`
5. skills relevantes em `.claude/skills/`

A task atual é a única unidade de trabalho autorizada. Não avance automaticamente.

## Referências visuais externas — caminho canônico
As imagens pesadas não precisam estar no pacote/ZIP. Considere como raiz canônica:

`D:\Empresa\GFMaurila\projetos\gfm-truckhub-claude-code-zip\references\screens`

Os caminhos relativos documentados em `docs/screens/SCREEN-CATALOG.md` e `docs/screens/SCREEN-MANIFEST.md` são resolvidos a partir dessa raiz.

Exemplo:
`references/screens/routes/010-dashboard.png`
=> `D:\Empresa\GFMaurila\projetos\gfm-truckhub-claude-code-zip\references\screens\routes\010-dashboard.png`

Se uma imagem não estiver acessível:
- NÃO invente seu conteúdo;
- use as notas textuais disponíveis apenas para planejamento;
- registre `VISUAL_REFERENCE_UNAVAILABLE`;
- não declare fidelidade visual nem conclua Quality Gate visual sem inspeção real.

## REGRA MÁXIMA — UI FIRST
Antes de implementar regras reais, o Desktop inteiro deve existir, abrir e ser navegável com JSON mock.

Ordem obrigatória:
1. Pesquisa técnica.
2. Arquitetura.
3. Decomposição completa em tasks.
4. Implementação de TODAS as telas aprovadas.
5. Navegação completa.
6. JSON mock em TODAS as telas.
7. Comparação com as referências visuais reais.
8. Execução do Desktop para validação do Product Owner.
9. STOP e aguardar aprovação explícita.
10. Somente depois: Domain/CQRS real, Map Extractor, persistência real, jobs, graph/routing, telemetria e integrações.

Nunca pule o Quality Gate visual.

## Arquitetura alvo
- .NET 10
- WPF / MVVM
- Domain puro
- Application com CQRS
- Contracts
- Infrastructure
- JSON local inicialmente
- abstrações de repository
- jobs internos do Desktop inicialmente
- Map Extractor ETS2/ATS
- Graph / Routing
- Telemetry Provider real + mock
- API somente quando houver necessidade comprovada
- Docker não é requisito de Core/Rotas
- Docker Compose permitido para n8n/automações opcionais

## Limites arquiteturais
- Domain não referencia WPF, JSON, HTTP, Docker, n8n ou Infrastructure.
- Application não conhece detalhes de persistência.
- Infrastructure implementa portas/contratos.
- UI consome Application/Contracts; regra de negócio não vive em View/ViewModel.
- Código dependente de ATS/ETS2 deve ficar atrás de contratos substituíveis.
- Mock e Real devem compartilhar contratos quando representam a mesma capability.

## Offline First
Rotas deve funcionar sem Docker, PostgreSQL, Redis, n8n, API remota ou servidor externo.

## Game Environment
Instalação do jogo e pasta de perfil/dados são conceitos distintos.

Detectar Steam e Steam Libraries, inclusive em outros discos. Caminhos de perfil/dados são configuráveis e nunca devem ser hardcoded como requisito.

Arquivos pesados, perfis e instalações ATS/ETS2 usados como referência podem ficar fora do repositório. Documente o caminho esperado; não copie esses dados para o projeto.

## Grounding
Nunca especule sobre código, arquivo de jogo, formato SCS ou imagem que não foi aberto/validado.
Para pesquisa externa, prefira documentação/fonte primária e registre fonte, data e implicação técnica.
Não copie implementação de terceiros sem verificar licença.

## Execução de tasks
Uma task por vez.

Antes:
- confirme task atual;
- leia critérios de aceite;
- identifique arquivos permitidos/proibidos;
- identifique referências visuais e skills aplicáveis.

Durante:
- faça apenas mudanças necessárias à task;
- preserve decisões existentes;
- não crie infraestrutura futura por antecipação;
- mantenha mocks determinísticos.

Ao concluir:
- `dotnet restore` quando aplicável;
- `dotnet build` quando aplicável;
- `dotnet test` quando aplicável;
- `git diff --check`;
- revisão de escopo;
- relatório em `docs/reports/<TASK-ID>.md`;
- atualize `PROJECT-STATE.md` somente com fatos concluídos;
- STOP.

Falha em qualquer gate => task não está concluída.

## Política de subagentes
Use subagentes quando houver trabalho independente, pesquisa isolada ou revisão especializada.
Não use subagentes para uma alteração simples de um único arquivo.

Papéis disponíveis em `.claude/agents/`:
- researcher
- architect
- tech-lead
- frontend
- developer
- tester
- reviewer
- map-specialist
- telemetry-specialist
- documentation

O agente principal/orquestrador mantém a responsabilidade pelo escopo e pela decisão de STOP.

## Skills
Skills em `.claude/skills/` são procedimentos reutilizáveis. Leia a skill correspondente antes de executar trabalho especializado.

## Segurança
- Nunca gravar secrets no repositório, `CLAUDE.md`, relatórios ou mocks.
- Não modificar arquivos reais de instalação/perfil ATS/ETS2 sem autorização explícita.
- Operações de descoberta são read-only por padrão.
- Modificação de mods/perfis pertence às fases explicitamente autorizadas.
- Nunca remover teste ou relaxar assertion apenas para obter PASS.

## Convenções
Arquivos próprios do projeto: lowercase kebab-case, exceto nomes fixos/convenções (`CLAUDE.md`, `README.md`, `PROJECT-STATE.md`).
IDs de telas e tasks são estáveis.
Não renomeie IDs históricos para “organizar”.

## Definição de STOP
STOP significa:
- não iniciar próxima task;
- não implementar “só mais uma coisa”;
- não transformar recomendação futura em código;
- apresentar resultado, gates e pendências;
- aguardar comando explícito do Product Owner.
