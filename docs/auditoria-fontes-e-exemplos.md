# Auditoria de fontes, exemplos e limites — 2026-10-20

## Escopo
- Investigados: `aoe2control/AoE2Control`, `aoe2control/aoe2control.github.io`, `aoe2control/aoe2-control-lua-vscode-extension`.
- Excluído: `AoE2RMSIDE` e edição/criação de mapas aleatórios. Mantidas consultas de terreno e caminhos usadas por bots.
- Resultado: 380 assinaturas catalogadas de `definitions/control-api.d.lua` (ver `catalogo-assinaturas-lua.md`). Esse é o número de assinaturas encontradas, **não** 380 funcionalidades validadas no binário.
- A implementação nativa do motor não está incluída no repositório principal; portanto offsets, ABI, threads internas e comandos DE não foram comprovados por código nativo público.

## Cinco módulos oficiais — auditoria de comportamento

| Exemplo | O que demonstra | Caminho |
|---|---|---|
| Game speed | `Settings.AddKeybind` no `Load`, `Settings.GetKeybind` e `IsKeyPressed` no `Render`, `SetGameSpeedMultiplier` | [código](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/game_speed/game_speed.main.lua) |
| IPC test | `IPC.StartServer` no `Init`, `IPC.HasMessages/GetMessages/Send`, `ParseJSON`, `IPC.StopServer` no `End`/`Unload` | [código](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/ipc_test/ipc_test.main.lua) |
| Unit pathing | `Player:GetSelectedObject`, `Object:IsAlive/GetTargetPosition/GetPosition/GetPath`, `RenderWorldLine/CircleFilled` | [código](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/unit_pathing/unit_pathing.main.lua) |
| Villager highlighting | `GetObjectsByClass(UnitClass.VILLAGER)`, `RenderObjectBoundsFilled`, preferências de cor | [código](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/villager_highlighting/villager_highlighting.main.lua) |
| Walkable tiles | `GetMapWidth/Height/GetMapTile`, `MapTile:IsWalkable`, `IsWorldPosOnScreen`, geometria de câmera e overlay | [código](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/walkable_tiles/collision_grid.main.lua) |

## Restrições observadas diretamente em `docs/limits.md`

- `Update` e `Render` executam no thread do jogo em modo padrão; devem ser curtos.
- `Render` executa por frame e não é invocado em Multithreading.
- Com Multithreading, a leitura passa a snapshot por quadro, comandos são enfileirados e funções dependentes de UI/sessão podem ser bloqueadas.
- `ResourceTracker`, `VillagerOccupation`, `ConstructionPlacement` não devem ter `Update` chamado em Multithreading.
- Bridge V3: `\\.\pipe\AoE2ControlAgentV3.P<n>`, estado por jogador e protocolo `status/open/observe/map/act/query/close`.
- Replays permitem observação, mas rejeitam comandos do Agent Bridge.

## Divergência documental encontrada — multiplayer

- [README do motor](https://github.com/aoe2control/AoE2Control/blob/main/README.md) afirma ser estritamente single-player, com multiplayer completamente desativado.
- [Limits](https://github.com/aoe2control/aoe2control.github.io/blob/main/docs/limits.md) qualifica que módulos podem ser executados em multiplayer **apenas com cheats habilitados**, mas o Agent Bridge continua proibido em multiplayer.
- **Tratamento:** registrar divergência entre formulações em vez de concluir suporte geral; jamais transportar lógica para partidas multiplayer HD. Uso planejado: offline/local.

## Lacunas não resolvidas

1. O arquivo `control-api.d.lua` é uma declaração de editor; precisa de confirmação adicional por documentação ou testes do produto para cada método.
2. Existem 184 assinaturas sem ocorrência literal do nome completo nas páginas examinadas; isso não prova falta de suporte.
3. Falta identificar sobrecargas, valores retornados, efeitos colaterais e opções relevantes de cada método por inspeção semântica linha a linha.
4. Falta reproduzir no executável DE e, independentemente, testar paridade HD.
5. Fonte original pode mudar: congelar commit SHA dos três repositórios antes de alegar cobertura exaustiva de release.
6. Funções de controle de sessão e nomes próximos de RandomMapSource pertencem a configuração de partida, não a edição de mapas; não confundir com RMSIDE.

## Próximas provas HD

- Selecionar um aldeão e capturar sua identidade e posição com persistência entre frames.
- Selecionar um recurso e identificar tipo, posição e possível proprietário.
- Ordenar movimentação e coleta em sessão local; correlacionar alterações de ordem, objetivo e posição, sem equiparar IDs DE a HD.
- Diferenciar ordem **emitida**, **enfileirada** e **executada** em logs.
- Registrar memória e IDs descobertos primeiro no `AoE2HD.mapping`, preservando status candidato/validado.
