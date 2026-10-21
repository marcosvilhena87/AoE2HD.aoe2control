# AoE2Control API Audit v2 — relatório e matriz de compatibilidade HD

Data: 2026-10-20. Escopo: AoE2Control, documentação oficial e extensão Lua. **Edição de mapas excluída**. Consulte [contratos v2](api-audit-v2-contratos.md) para assinaturas rastreáveis.

## Achados quantitativos (extração estática)

| Indicador | Resultado |
|---|---:|
| Assinaturas Lua distintas | 380 |
| Assinaturas com `@param` contíguo | 213 |
| Assinaturas com `@return` contíguo | 303 |
| Assinaturas citadas nominalmente em 16 páginas da documentação | 196 |
| Sem correspondência nominal nas páginas amostradas | 184 |
| Módulos oficiais de exemplo auditados | 5 |

**Interpretação:** os números acima não representam cobertura de execução nem 380 APIs implementadas/compatíveis. Ausência de anotação não é necessariamente ausência de parâmetro ou retorno. Há correspondências documentais aproximadas por texto.

## Matriz prioritária de contratos

| ID | API DE | Entrada / retorno declarados | Uso DE documentado | Contrato HD proposto | Prova mínima HD | Prioridade |
|---|---|---|---|---|---|---|
| OBJ-001 | `GetObjectById(id)` | id: integer → Object ou nil | Resolver unidade/objeto por identidade | `get_object_by_id(id)` com objeto tipado e falha explícita | identidade estável entre capturas, desaparecimento controlado | P0 |
| OBJ-002 | `GetObjectsByClass(unitClass)` | classe → lista Object | Listar objetos por classe | `get_objects_by_class(class_id)` | aldeões observáveis sem falsos positivos, alterações com novos aldeões | P0 |
| PLY-001 | `GetAssignedPlayer()` | sem argumentos → Player | Contexto do jogador controlado | `get_assigned_player()` | dono consistente dos aldeões na sessão local | P0 |
| OBJ-003 | `GetObjectsInArea(pos1,pos2,unitClass,owner)` | 2 Vector2, filtros opcionais → lista Object | Consulta espacial filtrada | `get_objects_in_area(rect, filters)` | comparar dentro/fora da região e filtros de dono/classe | P0 |
| CMD-001 | `UnitsMove(units,position,queue)` | Object[], Vector3, bool opcional → boolean | Movimentação de unidades | `units_move(ids,position,queue=false)` | verificar emissão, aceitação e deslocamento efetivo em etapas distintas | P0 |
| OBJ-004 | `Object:GetPosition()` | método de Object → posição | Coordenadas da unidade | `get_position(id)` | movimento no HD refletido nas coordenadas ao longo de frames | P0 |
| OBJ-005 | `Player:GetSelectedObject()` | método de Player → Object | Identificação da unidade selecionada | `get_selected_object()` | selecionar/desselecionar unidades, conferir ID de objeto | P0 |
| CMD-002 | `UnitsTargetObject` | unidades, destino objeto, fila → boolean | Direcionar ação à entidade-alvo | `units_target_object(ids,target_id)` | aldeão recebe alvo e altera ordem de coleta em teste controlado | P1 |
| MAP-001 | `GetMapTile` / `MapTile:IsWalkable` | coordenadas / boolean | Verificar transitabilidade | `is_tile_walkable(x,y)` | colidir com terreno/caminho sem editar mapas | P1 |
| CMD-003 | `UnitsBuildStructure` | construtores, tipo, posição → boolean | Ordem de construção | `units_build_structure` | falhas sem recursos e execução com recursos suficientes | P1 |
| IPC-001 | `IPC.StartServer`, `IPC.GetMessages` | nome, mensagens JSON | canal Lua ↔ processo externo | IPC JSON versionado e limitado | round-trip ping/pong; desconexão; schema inválido | P2 |
| AGENT-001 | Agent Bridge V3 | status/open/observe/map/act/query/close | agente externo por pipe/jogador | bridge opcional; não equiparar protocolo binário DE/HD | handshake, consulta, comando somente offline; códigos de erro | P2 |

Todos os contratos HD são **propostas**, não comportamentos observados.

## Evidências de código de exemplo

- [Villager Highlighting](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/villager_highlighting/villager_highlighting.main.lua): usa `GetObjectsByClass(UnitClass.VILLAGER)` e `RenderObjectBoundsFilled`.
- [Unit Pathing](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/unit_pathing/unit_pathing.main.lua): usa `Player:GetSelectedObject`, `Object:GetTargetPosition`, `Object:GetPosition`, `Object:GetPath` e renderização.
- [IPC Test](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/ipc_test/ipc_test.main.lua): usa servidor IPC, parse JSON, mensagens e encerramento.
- [Game Speed](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/game_speed/game_speed.main.lua): keybind e controle de velocidade.
- [Walkable Tiles](https://github.com/aoe2control/AoE2Control/blob/main/example_modules/walkable_tiles/collision_grid.main.lua): consulta a tiles e transitabilidade; não é edição de mapas.

## Restrições e divergências

1. Se uma API é encontrada no arquivo de definição e não na documentação, manter status **declarada sem referência textual**, sem presumir suporte ou ausência.
2. Em multithreading, comandos podem ser enfileirados e leituras podem usar snapshots; sucesso booleano não garante execução.
3. Alguns módulos estratégicos acessam dados vivos e não são seguros para atualizar no modo multithreading.
4. `Render` é exclusivo do fluxo gráfico; não é executado no modo multithreading.
5. O README descreve restrição a single-player; a página de limites admite callbacks de módulos em multiplayer com cheats, mas nega Agent Bridge em multiplayer. O HD permanecerá restrito a testes locais.
6. Não há fonte aberta suficiente para confirmar o código nativo da injeção, offsets ou ABI.

## Política de regressão

- Verificar unicidade de `symbol + signature` no catálogo.
- Alertar se uma assinatura mudar entre revisões da extensão.
- Alertar se funções P0 forem removidas ou tiverem parâmetros alterados.
- Verificar que toda funcionalidade HD depende de evidência do `AoE2HD.mapping` quando usar identificadores ou memória.
- Não promover candidatos sem captura reproduzível no jogo HD.

## Próxima sequência executável

1. **HD Object API v1:** `GetObjectById`, `GetObjectsByClass`, `GetAssignedPlayer`, `GetObjectsInArea`, `GetPosition`.
2. **HD Command API v1:** `UnitsMove` com separação entre intenção, ordem aceita e execução observada.
3. **HD Economy API:** `UnitsTargetObject` e coleta, aproveitando o comportamento nativo do jogo para continuação de recursos esgotados.

Nenhum endereço novo de memória foi alegado ou alterado nesta auditoria documental.
