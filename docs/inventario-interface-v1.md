# Inventário de interface do CONTROL — revisão 1.1.2

Fonte: https://aoe2control.github.io/interface-options/ (consulta em 2026-10-20). Estado HD de todos os controles: **a_investigar_HD**.

## Janela CONTROL
- Abre/fecha com Shift quando a janela do jogo está em foco.
- Submenus: MODULES, MISC, UI, KEYBINDS, DEBUG; um submenu por instância de módulo.
- Persiste alterações em settings.ini.
- Descobre arquivos *.main.lua e *.main.module até três subdiretórios sob modules/.

## MODULES

| Controle | Padrão | Comportamento |
|---|---|---|
| Enabled | On | ativa/desativa todos os slots |
| Update Interval | 1.0 s | intervalo em tempo de jogo; slider 0.1–2.0; INI aceita >=0.01 |
| Sequential Actions | On | um comando por Update |
| Auto Move Camera | On | move câmera para alvo de comandos |
| Command Visualization | On | overlay de comandos executados |
| Suppress Native AI | On | suspende AI nativa do jogador bot com módulo |
| Tournament Mode | Off | comandos só em Update; penalização de tempo >20 ms e bloqueios |
| Multithreading | Off | thread por módulo; Render desativado; bloqueios e riscos de sincronização |
| Modules See Everything | Off | ignora fog of war na leitura |
| Agent Bridge | Off | habilita pipes por jogador, indisponível em multiplayer |
| Open Folder | ação | abre pasta modules |

### Player 1 a Player 8
- Agent Bridge (quando disponível), Enabled, Sync, Module, Sync Profile, Create Profile, Remove Profile, Remove Module.
- Erros Lua, jogador indisponível, intervalo e atrasos Tournament Mode.
- Reatribuir o mesmo módulo faz reload.

## MISC
| Controle | Padrão | Valores/observações |
|---|---|---|
| Player Perspective | Default | Default, Gaia, Player 1–8; pode causar instabilidade |
| Game Speed Multiplier | Default | Default, 1, 1.5, 2, 5, 10, 20, 30 |
| Spectator Mode | Off | revela mapa na visualização |
| Unlock Zoom | Off | amplia zoom, possíveis problemas gráficos |
| Chat Welcome Message | On | envia boas-vindas |

## UI
| Controle | Padrão | Valores |
|---|---|---|
| Menu Scale | 1.0 | 0.5, 0.75, 1.0, 1.5 |
| Menu Transparency | 0.05 | 0–0.7 |

## KEYBINDS
- Menu Toggle Key: Shift (padrão).
- Unload Key: Delete (padrão).
- Atalhos reagem apenas com janela do jogo em foco.

## DEBUG
- Show Log / Hide Log.
- Module Telemetry (Off): tempos Update/Render, baseline, médias, p95, máximo, 256 chamadas, participação por frame e atrasos.
- API Profiling (Off): chamadas, tempo agregado, impacto de desempenho.
- Diagnósticos em diagnostics/latest.json; GetModuleTelemetry() acessa métricas do próprio módulo.
- Log('mensagem') prefixa [MODULE], indisponível em Tournament Mode.

## Diferenciações essenciais
- Player Perspective: modifica o que o jogo desenha.
- Modules See Everything: modifica o que o módulo consegue ler.
- Spectator Mode: comportamento distinto de autorização de comandos.
- Multithreading: altera ciclo de renderização, visibilidade de estado e retorno dos comandos.
- Configuração da edição DE **não garante** equivalência em HD.
