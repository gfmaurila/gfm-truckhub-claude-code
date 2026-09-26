# Claude Code Structure

## Orchestration
`CLAUDE.md` defines invariants, execution protocol, external references and STOP behavior.
`tasks/CURRENT.md` is the single task pointer.

## Commands
- `/current` — inspect current task without editing.
- `/execute-current-task` — execute exactly the current task.
- `/research` — research within current scope.
- `/review` — review current task implementation.
- `/test-all` — run applicable quality gates.
- `/visual-check` — compare against real external screens.
- `/project-status` — factual status only.

## Agents
Researcher -> Architect -> Tech Lead -> Developer/Frontend/Specialists -> Tester -> Reviewer -> Documentation.
This is not an automatic pipeline: use only roles needed by the current task.

## Skills
Skills contain reusable procedures and domain guidance. They reduce duplication in agents/commands and keep `CLAUDE.md` focused.

## Rules
Rules are invariants that apply across tasks: architecture, UI-first, storage, Docker, testing, game environment and external references.

## External visuals
Canonical root:
`D:\Empresa\GFMaurila\projetos\gfm-truckhub-claude-code-zip\references\screens`

Visual approval requires the actual image plus Product Owner validation.
