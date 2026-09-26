# GFM TruckHub — Claude Code

Template refatorado para desenvolvimento orientado por tasks com Claude Code.

## Início
1. Abra o repositório no diretório raiz.
2. Leia `CLAUDE.md`.
3. Execute `/current`.
4. Para trabalhar, execute `/execute-current-task`.
5. Ao terminar uma task, o Claude deve rodar gates, gerar relatório e **STOP**.

## Estrutura Claude Code
- `CLAUDE.md` — contrato global do projeto.
- `.claude/commands/` — comandos operacionais.
- `.claude/agents/` — especialistas/subagentes.
- `.claude/skills/` — procedimentos reutilizáveis.
- `.claude/rules/` — invariantes arquiteturais e de execução.
- `.claude/settings.json` — permissões compartilhadas.
- `tasks/CURRENT.md` — ponteiro da única task autorizada.
- `PROJECT-STATE.md` — estado factual do projeto.

## Referências visuais
As imagens pesadas ficam fora do pacote.

Raiz esperada:
`D:\Empresa\GFMaurila\projetos\gfm-truckhub-claude-code-zip\references\screens`

O índice canônico permanece em `docs/screens/SCREEN-CATALOG.md`.

## Fases
00 Research → 01 Desktop Mock → 02 Core → 03 Map Extractor → 04 Routing → 05 Telemetry → 06 Live Assistant → 07 n8n → 08 Crazy Traffic.

## Regra principal
UI First. Todo o Desktop navegável com Mock JSON e validação visual do Product Owner antes das regras reais.

## Segurança operacional
Instalações, perfis, mods e arquivos ATS/ETS2 são read-only por padrão. Não copie dados pesados nem altere arquivos reais sem autorização explícita.
