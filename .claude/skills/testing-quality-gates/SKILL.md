# Testing & Quality Gates
Use antes de concluir qualquer task com código.
Execute o conjunto aplicável: restore, build, unit, integration, architecture tests e `git diff --check`.
Não apague testes nem relaxe assertions para obter PASS.
Relate comando, resultado e falhas. Gate falhou => task permanece incompleta.
Mudança visual requer validação manual do Product Owner além dos testes automatizados.
