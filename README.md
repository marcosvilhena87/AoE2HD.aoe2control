# AoE2HD.aoe2control — pesquisa e adaptação

Este repositório é o **laboratório de investigação** das funcionalidades, APIs, arquitetura, módulos e interface do [AoE2Control](https://aoe2control.github.io/) (feito para Age of Empires II: Definitive Edition), visando à futura adaptação para **Age of Empires II HD**.

**Não é o motor de controle do jogo e não é o catálogo canônico de memória.**

## Responsabilidades

| Projeto | Papel |
| --- | --- |
| [AoE2HD.aoe2control](https://github.com/marcosvilhena87/AoE2HD.aoe2control) | Estudar o AoE2Control DE, documentar comportamento, registrar evidências, especificar adaptação HD |
| [AoE2HD.control](https://github.com/marcosvilhena87/AoE2HD.control) | Desenvolver e testar o motor funcional para HD |
| [AoE2HD.mapping](https://github.com/marcosvilhena87/AoE2HD.mapping) | Manter exclusivamente endereços, identificadores e estruturas de memória, com evidência e status |

## Método de investigação

1. Identificar cada função e elemento visual em documentação ou implementação pública do AoE2Control.
2. Registrar origem, link, comportamento, pré-condições, parâmetros, retornos e restrições.
3. Classificar a transposição: `documentado_DE`, `a_investigar_HD`, `viavel_HD`, `implementado_HD`, `bloqueado_HD`.
4. Propor contrato mínimo e critérios de aceitação para `AoE2HD.control`.
5. Se surgir mapeamento novo, registrá-lo **primeiro** no `AoE2HD.mapping` com evidências, sem promover candidatos a validados automaticamente.

**Cuidado:** a documentação DE não confirma equivalência de memória, ABI, comandos ou interface com HD. Não presumir que o binário ou uma DLL de DE funcione no HD. Não copiar conteúdo proprietário de binários ou contornar proteções; estudos e testes devem respeitar licenças e uso em partidas locais.

## Índice

- [HD Compatibility Matrix v3 — estado atual da adaptação](docs/hd-compatibility-matrix-v3.md)
- [HD Compatibility Matrix v3 — CSV estruturado](docs/hd-compatibility-matrix-v3.csv)
- [HD Compatibility Matrix v2 — histórico da adaptação](docs/hd-compatibility-matrix-v2.md)
- [HD Compatibility Matrix v2 — CSV estruturado](docs/hd-compatibility-matrix-v2.csv)
- [Matriz inicial de funcionalidades e interface](docs/matriz-funcionalidades.md)
- [Protocolo de investigação](docs/protocolo-investigacao.md)

## Fontes primárias

- https://aoe2control.github.io/
- https://aoe2control.github.io/commands/
- https://aoe2control.github.io/interface-options/
- https://aoe2control.github.io/module-system/
- https://aoe2control.github.io/getting-started/
- https://github.com/aoe2control/AoE2Control
- https://github.com/aoe2control/aoe2-control-lua-vscode-extension

*As características do produto são registradas com referência às fontes; não são declarações de compatibilidade com HD.*
