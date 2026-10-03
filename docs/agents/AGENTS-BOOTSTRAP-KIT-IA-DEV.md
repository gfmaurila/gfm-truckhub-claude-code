# Bootstrap dos Agents — Kit IA Dev

## Objetivo

Definir a origem obrigatória da estrutura inicial usada pela IA para criar e configurar os Agents e Skills do **GFM TruckHub**.

## Pacote de referência

```text
D:\Empresa\GFMaurila\projetos\gfm-truckhub-claude-code\references\Kit-IA-Dev.zip
```

Esse arquivo é uma dependência local de desenvolvimento e deve permanecer em `references`. Ele não deve ser copiado para o código de produção nem enviado para infraestrutura AWS.

## Fluxo obrigatório

```text
Kit-IA-Dev.zip
      |
      v
Ler documentação do Kit
      |
      v
Identificar padrão Agent Skills / SKILL.md
      |
      v
Detectar ferramenta de IA utilizada
      |
      v
Gerar/instalar estrutura inicial de Agents + Skills
      |
      v
Aplicar contratos do GFM TruckHub
      |
      +--> prompts.md
      +--> PROJECT_STRUCTURE.md
      +--> PROJECT_SKILLS.md
      +--> CLAUDE.md
      +--> PROJECT-STATE.md
      |
      v
Executar pipeline de desenvolvimento/refatoração
```

## Responsabilidades

O **Kit IA Dev** fornece a estrutura, convenções e mecanismo inicial de Agents/Skills.

O **GFM TruckHub** fornece o domínio e as decisões do produto: Desktop WPF/.NET, UI First, Offline First, Map Extractor, Routing, Telemetry, Live Assistant, integrações, mocks/referências e evolução Cloud Ready para AWS.

## Regras

- Não inventar uma estrutura paralela de Agents antes de consultar o Kit.
- Não alterar a ideia de negócio para adequá-la aos exemplos do Kit.
- Não considerar exemplos do Kit como requisitos funcionais do TruckHub.
- Não exigir AWS para execução local do Desktop.
- Preservar os documentos e desenhos existentes do projeto.
- Gerar novos diagramas em formato editável quando a arquitetura mudar.
- Registrar decisões relevantes de bootstrap/refatoração nos relatórios do projeto.
- Se o ZIP não estiver disponível, interromper somente a etapa de geração/instalação de Agents e informar claramente a dependência ausente; não criar uma estrutura alternativa silenciosamente.

## Sequência de Agents

A sequência concreta deve ser derivada do Kit disponível no caminho informado. Quando o Kit oferecer papéis equivalentes, especializá-los para o TruckHub (por exemplo: requisitos, arquitetura, planejamento técnico, desenvolvimento, testes, revisão e documentação) sem alterar as convenções do pacote.

## AWS

A AWS é o alvo Cloud Ready do projeto. Agents de arquitetura/infraestrutura devem considerar os serviços documentados pelo TruckHub, mas não declarar recursos como implementados enquanto forem apenas planejados.

## Critério de conclusão da Fase 0

A Fase 0 só termina quando:

1. o Kit foi localizado;
2. sua documentação relevante foi lida;
3. o padrão de Agents/Skills foi identificado;
4. a estrutura aplicável foi preparada;
5. os Agents foram especializados com os contratos do TruckHub;
6. a origem e as decisões do bootstrap foram registradas.
