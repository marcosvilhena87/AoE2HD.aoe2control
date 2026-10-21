# Inventário funcional do AoE2Control (DE) — v1

> Pesquisa de fontes oficiais e repositórios públicos. Data da revisão: 2026-10-20. Base de versão: AoE2Control 1.1.2 (2026-10-14).
> **Status**: referência funcional DE, não comprovação de implementação ou compatibilidade HD.

## Metodologia e limites

- Fonte primária: documentação oficial em https://aoe2control.github.io/ ; release notes https://github.com/aoe2control/AoE2Control/releases
- Código publicamente acessível: https://github.com/aoe2control/AoE2Control (exemplos) e https://github.com/aoe2control/aoe2-control-lua-vscode-extension (declarações Lua, snippets). A implementação nativa completa do motor não está apresentada no repositório principal aberto; documentação de API não é código-fonte de implementação.
- Estado DE: `documentado_DE`. Estado HD de TODAS as linhas: `a_investigar_HD`. Não converter observações DE em endereços, classes ou comandos HD sem experiência reprodutível.
- Em caso de divergências, usar versão 1.1.2 das páginas oficiais e changelog. A extensão VS Code pode conter declarações defasadas.
- Na implementação HD, limitar controle a sessões locais/offline e respeitar restrições do jogo.

## Inventário de grupos

| Código | Categoria | Capacidades / símbolos confirmados | Fonte | Prioridade HD |
|---|---|---|---|---|
| UI-01 | Launcher e configuração | Carregamento do motor no jogo; inicialização headless; pasta de configuração e settings.ini; log | [Getting Started](https://aoe2control.github.io/getting-started/), [Headless](https://aoe2control.github.io/headless-mode/), [Interface](https://aoe2control.github.io/interface-options/) | P2 |
| UI-02 | Menu principal | Shift abre menu; MODULES, MISC, UI, KEYBINDS, DEBUG; logs | [Interface](https://aoe2control.github.io/interface-options/) | P2 |
| UI-03 | Gerência de módulos | Slots jogador 1–8; enabled, sync, seleção e reload; atualização por intervalo; visualização de comandos | [Interface](https://aoe2control.github.io/interface-options/) | P1 |
| UI-04 | Opções de execução | Sequential Actions, Auto Move Camera, Suppress Native AI, Tournament Mode, Multithreading, Modules See Everything, Agent Bridge | [Interface](https://aoe2control.github.io/interface-options/) | P2 |
| MOD-01 | Ciclo de vida | `Load`, `Init`, `Update`, `Render`, `End` | [Lifecycle](https://aoe2control.github.io/lifecycle/) | P1 |
| MOD-02 | Arquivos | `{name}.main.lua`, `{name}.main.module`; descoberta até 3 níveis; `require` local com cache; módulos compilados | [Module System](https://aoe2control.github.io/module-system/) | P2 |
| MOD-03 | Engenharia do motor | `Log`, `GetAssignedPlayerId`, `AssignAndLoadModule`, `SetEngineUIVisibility`, `UnloadEngine`, `GetModuleTelemetry` | [Commands](https://aoe2control.github.io/commands/), [Facts](https://aoe2control.github.io/facts/) | P2 |
| GAME-01 | Estado de jogador | `GetAssignedPlayer`, `GetPlayerById`, `GetPlayerCount`, `IsEnemyPlayer`; objeto Player e recursos/diplomacia | [Facts](https://aoe2control.github.io/facts/), [Types](https://aoe2control.github.io/types/) | P0 |
| GAME-02 | Economia e tecnologia (leitura) | `GetFact`, `GetAttribute`, `GetUnitTypeCount`, `CanAfford`, `CanResearch`, `IsTechnologyResearched`, `GetTechCost`, `GetObjectCost`, `IsObjectTypeAvailable` | [Facts](https://aoe2control.github.io/facts/) | P0 |
| OBJ-01 | Identidade e consulta | `GetObjectById`, `GetObjectsByType[s]`, `GetObjectsByClass[es]`, `GetObjectsInArea`; métodos da classe `Object` | [Facts](https://aoe2control.github.io/facts/), [Types](https://aoe2control.github.io/types/) | P0 |
| OBJ-02 | Estado avançado | `GetObjectStates`, `GetObjectChanges`, `GetObjectTypeData`, `GetObjectTypeAttribute`, `GetObjectsPtr` | [Facts](https://aoe2control.github.io/facts/) | P0 |
| OBJ-03 | Projéteis | `GetProjectileById`, `GetAllProjectiles`, `GetProjectilesByType` | [Facts](https://aoe2control.github.io/facts/) | P3 |
| MAP-01 | Grade/mapa | `GetMapWidth`, `GetMapHeight`, `GetMapTile`, `GetAllMapTiles`, `GetMapTilesPtr`; classe `MapTile` | [Facts](https://aoe2control.github.io/facts/), [Types](https://aoe2control.github.io/types/) | P1 |
| MAP-02 | Navegação e construção | `CalculatePath`, `CheckPlacement`, `CanPlaceObject`; testes de visibilidade e colisão | [Facts](https://aoe2control.github.io/facts/) | P1 |
| CMD-01 | Movimento e interação | `UnitsMove`, `UnitsTargetObject`, `UnitsBuildStructure` | [Commands](https://aoe2control.github.io/commands/) | P0 |
| CMD-02 | Produção | `TrainUnit`, `ResearchTechnology`, `SetGatherPoint` | [Commands](https://aoe2control.github.io/commands/) | P1 |
| CMD-03 | Tática militar | `EnableScouting`, `SetUnitStanceAutoScout`, `SetUnitStancePatrol`, `SetUnitStanceGuard`, `SetUnitStanceFollow`, `SetUnitStanceAttackMove`, `SetUnitCombatStance`, `SetFormation` | [Commands](https://aoe2control.github.io/commands/) | P1 |
| CMD-04 | Proteção / guarnição | `SetUnitStanceGarrison`, `SetUnitStanceUngarrison`, `SetUnitStanceSeekShelter`, `RingTownBell`, `SendBackToWork`, `SendAllBackToWork` | [Commands](https://aoe2control.github.io/commands/) | P2 |
| CMD-05 | Manutenção da economia | `QueueFarmReseeds`, `CancelFarmReseeds`, `SetAutoFarmReseed`, `QueueFishTrapRebuilds`, `CancelFishTrapRebuilds`, `SetAutoFishTrapRebuild` | [Commands](https://aoe2control.github.io/commands/) | P2 |
| CMD-06 | Exclusão de objetos | `DeleteUnit`, `DestroyBuilding` | [Commands](https://aoe2control.github.io/commands/) | P3 |
| CMD-07 | AI nativa | `SetGoal`, `SetGoals`, `Player:GetGoal`, `Player:GetGoals`; interação com script .per | [Commands](https://aoe2control.github.io/commands/) | P3 |
| CMD-08 | Câmera/chat | `SetCameraPosition`, `SendChatMessage`, `GetAllChatMessages`, `GetNewChatMessages`, `GetLastChatMessage` | [Commands](https://aoe2control.github.io/commands/), [Facts](https://aoe2control.github.io/facts/) | P2 |
| SESS-01 | Sessão | `DispatchStartGame`, `DispatchRestartGame`, `DispatchResignGame`, `DispatchQuitGame`, `DispatchLoadGame`, `GetAvailableSaveFiles`, `GetCurrentGameOptions` | [Automation](https://aoe2control.github.io/automation/) | P2 |
| SESS-02 | Pause/replay | `IsGamePaused`, `IsMenuOpen`, `SetGamePaused`, `SetGameSpeedMultiplier`, `SetReplaySpeed`, `GetCurrentReplayFileName`, `GetVictoryPlayer`, `GetVictoryCondition`, `GetGameTime` | [Commands](https://aoe2control.github.io/commands/), [Facts](https://aoe2control.github.io/facts/) | P2 |
| CFG-01 | Controles personalizados | `Settings.AddBool/AddInt/AddFloat/AddDropdown/AddKeybind/AddTooltip/AddColor`; `Settings.GetBool/GetInt/GetFloat/GetString/GetKeybind/GetColor`; `IsKeyPressed` | [Settings](https://aoe2control.github.io/settings-api/) | P2 |
| DRAW-01 | Tela 2D | `GetScreenSize`, `IsOnScreen`, `RenderText`, `RenderLine`, `RenderCircle`, `RenderCircleFilled`, `RenderRect`, `RenderRectFilled` | [Render API](https://aoe2control.github.io/render-api/) | P2 |
| DRAW-02 | Mundo/minimapa | `IsWorldPosOnScreen`, `WorldToScreen`, `WorldToMinimap`, `GetZoom`, `GetCameraPosition`, `RenderWorldLine`, `RenderWorldRect`, `RenderWorldRectFilled`; demais funções Render* na fonte | [Render API](https://aoe2control.github.io/render-api/) | P2 |
| IPC-01 | IPC módulos | Named pipes e mensagens JSON; `IPC.HasMessages`, `IPC.WaitForMessage`; API detalhada na fonte | [IPC](https://aoe2control.github.io/ipc-api/) | P2 |
| AGENT-01 | Agent Bridge 1.1.1+ | Pipes `AoE2ControlAgentV3.P1` ... `P8`; protocolo `status`, `open`, `observe`, `map`, `act`, `query`, `close`; sem módulo Lua obrigatório | [Agent Bridge](https://aoe2control.github.io/agent-bridge/) | P2 |
| AGENT-02 | Estado de agente | Catálogos, observação, objetos, tecnologias, estatísticas com upgrades; 1.1.2 adiciona filtros `object_types`, `technologies` e `last_result` | [Agent Bridge](https://aoe2control.github.io/agent-bridge/), [releases](https://github.com/aoe2control/AoE2Control/releases) | P2 |
| AUTO-01 | Componentes estratégicos | `VillagerOccupation` (alocação e prioridades); `ResourceTracker` (recursos); `ConstructionPlacement` (posicionamento e construção) | [Types](https://aoe2control.github.io/types/), [extensão VS Code](https://github.com/aoe2control/aoe2-control-lua-vscode-extension) | P1 |
| TYPE-01 | Tipos de domínio | `Object`, `Player`, `MapTile`, `GameOptions`, `Vector2`, `Vector3`, `Color`; enums `UnitObjectType`, `UnitClass`, `Technology`, `Fact`, `ResourceType`, `ObjectData`, `ObjectAttribute`, `ProjectileType`, `PlacementResult` e outros | [Types](https://aoe2control.github.io/types/), [Enums](https://aoe2control.github.io/enums/) | P0 |
| TOOL-01 | Ambiente auxiliar | Extensão VS Code IntelliSense/snippets; AoE2RMSIDE editor RMS com pré-visualização/testes/deploy | [VS Code](https://github.com/aoe2control/aoe2-control-lua-vscode-extension), [RMSIDE](https://aoe2control.github.io/rmside/) | P3 |

## Regras relevantes do contrato DE

1. Comandos pertencem ao jogador designado; referências a unidades alheias são ignoradas.
2. Preferir execução no `Update()`; Tournament Mode impede comandos em outros callbacks.
3. Com Sequential Actions habilitado, há no máximo um comando de jogo por `Update()`.
4. Em Multithreading ou Agent Bridge, confirmação `true` pode significar apenas **enfileirado**, não executado.
5. Em replay, comandos de jogo são bloqueados; consultas e determinados controles de câmera/chat continuam disponíveis.
6. `Render*` só pode ser chamado em `Render()`; renderização é desabilitada ou limitada em modos especiais.
7. A visibilidade é a perspectiva do jogador, salvo a opção `Modules See Everything`.
8. Objetos podem desaparecer, referências ficam inválidas e valores inacessíveis podem ser `nil`; checagem obrigatória.
9. O Agent Bridge V3 substitui o protocolo V1 da versão 1.1.0; **não desenvolver com `AgentBridge.Start()`** como API vigente.
10. A documentação do projeto proíbe uso do motor para controle multiplayer competitivo.

## Plano de transposição para HD

| Etapa | Contrato mínimo | Critério verificável | Repositório de destino |
|---|---|---|---|
| H0 | Catálogo de identidade | Unidade selecionada: id individual + tipo/classe comprovados com capturas repetidas | mapping |
| H1 | Leitura de unidade | Listar aldeões, proprietário, posição e tipo; comparar com estado em jogo | control + mapping |
| H2 | Estado do jogador | Ler recursos/tempo/população com testes de mudança controlada | control + mapping |
| H3 | Comando unitário | Ordenar movimento de um aldeão com confirmação de mudança de estado | control |
| H4 | Coleta | Identificar recurso-alvo e ordem de coleta sem depender apenas de aparência | control + mapping |
| H5 | Construção | Validar posição e ordem de construção, falhas de custo e ocupação | control |
| H6 | Compatibilidade Lua/API | Criar camada de adaptação, não importar diretamente ponteiros/ABI DE | control |
| H7 | Interface/IPC | Configuração e logs independentes do processo de leitura; canal externo com contrato explícito | control |

## Pendências de investigação

- Inventariar exaustivamente **cada** método de `Object`, `Player`, `MapTile`, `GameOptions`, `ResourceTracker`, `VillagerOccupation`, `ConstructionPlacement`, assinaturas/overloads e enums, em catálogo estruturado extraído da referência integral.
- Confirmar a arquitetura nativa: estruturas e offsets não são inferíveis com segurança apenas de declarações Lua; registrar como **não público/não confirmado** quando for o caso.
- Catalogar cada controle em MISC/UI/KEYBINDS/DEBUG com valores padrão e limites.
- Montar provas locais no HD separadas da pesquisa de documentação DE.
- Capturar o commit/release exato de cada evidência para detectar mudanças na documentação.

## Fontes centrais

- https://aoe2control.github.io/
- https://aoe2control.github.io/interface-options/
- https://aoe2control.github.io/module-system/
- https://aoe2control.github.io/lifecycle/
- https://aoe2control.github.io/commands/
- https://aoe2control.github.io/facts/
- https://aoe2control.github.io/types/
- https://aoe2control.github.io/enums/
- https://aoe2control.github.io/render-api/
- https://aoe2control.github.io/settings-api/
- https://aoe2control.github.io/ipc-api/
- https://aoe2control.github.io/agent-bridge/
- https://aoe2control.github.io/ai-agent-reference/
- https://github.com/aoe2control/AoE2Control/releases
- https://github.com/aoe2control/aoe2-control-lua-vscode-extension
