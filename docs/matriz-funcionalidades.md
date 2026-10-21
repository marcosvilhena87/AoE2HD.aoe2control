# Matriz inicial de investigação

**Data da coleta documental:** 2026-10-20. **Origem:** documentação pública do AoE2Control DE. **Estado HD:** não verificado.

| Domínio | Funcionalidade de referência DE | Evidência | Situação em HD | Primeira verificação |
| --- | --- | --- | --- | --- |
| Launcher | Iniciar engine, diagnosticar estado Ready | https://aoe2control.github.io/getting-started/ | a_investigar_HD | Conexão ao processo correto sem injeção |
| Game facts | Ler unidades, edifícios, recursos, jogadores e mapa | https://aoe2control.github.io/ | a_investigar_HD | Snapshot somente leitura de uma entidade |
| Commands | Mover unidades, treinar, pesquisar | https://aoe2control.github.io/commands/ | a_investigar_HD | Contrato de ordem e critérios de rejeição |
| Module lifecycle | Load, Init, Update, Render, End, Unload | https://aoe2control.github.io/getting-started/ | a_investigar_HD | Executor simulado sem jogo |
| Module discovery | arquivos `*.main.lua`, um módulo por slot de jogador | https://aoe2control.github.io/module-system/ | a_investigar_HD | Scanner de arquivos em diretório de testes |
| Menu MODULES | habilitar módulos, intervalo Update, ações sequenciais, câmera | https://aoe2control.github.io/interface-options/ | a_investigar_HD | Protótipo de estados/configurações |
| Menu UI | escala e transparência | https://aoe2control.github.io/interface-options/ | a_investigar_HD | Protótipo visual independente |
| Menu KEYBINDS | alternar menu com Shift; descarregar com Delete (padrões DE) | https://aoe2control.github.io/interface-options/ | a_investigar_HD | Atalhos configuráveis; evitar conflito com jogo |
| Menu DEBUG | log, telemetria e profiling da API | https://aoe2control.github.io/interface-options/ | a_investigar_HD | Registro estruturado e medição local |
| Overlay | texto e formas na tela, mundo e minimapa | https://aoe2control.github.io/ | a_investigar_HD | Teste isolado com coordenadas projetadas |
| IPC | named pipes e mensagens JSON | https://aoe2control.github.io/ | a_investigar_HD | Cliente/servidor local sem jogo |
| Multi-player modules | até 8 slots de jogador por partida | https://aoe2control.github.io/ | a_investigar_HD | Modelar slots sem assumir compatibilidade |
| Configurações | controles por módulo: checkboxes, sliders, listas, atalhos, cores | https://aoe2control.github.io/ | a_investigar_HD | Esquema de configuração independente |

## Limites observados na documentação DE

- Comandos normalmente requerem partida em andamento, não são executados durante replay e são associados ao jogador atribuído ao módulo.
- `Update()` é o ponto recomendado para enviar comandos; ações sequenciais podem limitar a uma ação por atualização.
- Com multithreading ou Agent Bridge, aceitação na fila **não** equivale à execução bem-sucedida.

Fonte: https://aoe2control.github.io/commands/

## Prioridade de pesquisa

1. Especificar a API de leitura de entidades e jogadores.
2. Descrever o comportamento do menu e o ciclo de vida dos módulos.
3. Formalizar contratos de comandos e modos em que são bloqueados.
4. Projetar IPC e overlays como componentes opcionais.
5. Levar à implementação HD somente funcionalidades testadas contra a sua própria versão do jogo.

Esta matriz é um **inventário documental inicial**, não um resultado de teste em Age of Empires II HD.
