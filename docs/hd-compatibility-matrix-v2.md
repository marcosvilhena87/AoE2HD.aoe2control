# HD Compatibility Matrix v2 — 20/10/2026

## Objetivo e critério de evidência

Comparação rastreável de **19 grupos de contratos** do AoE2Control (DE) com o código publicado no `AoE2HD.control` e os registros do `AoE2HD.mapping`. Não implica 19 APIs completas, nem compatibilidade ABI, nem validação em execução no Windows. A referência de implementação é o **código e a documentação de fases experimentais**, não o README v0.1 (desatualizado em relação aos arquivos atuais).

**Fontes:** [contratos DE v2](api-audit-v2-contratos.md), [matriz anterior](hd-compatibility-matrix-v1.md), [control/object_api.py](https://github.com/marcosvilhena87/AoE2HD.control/blob/main/aoe2hdcontrol/object_api.py), [control/selected_objects_v1_9.py](https://github.com/marcosvilhena87/AoE2HD.control/blob/main/aoe2hdcontrol/selected_objects_v1_9.py), [control/API v1](https://github.com/marcosvilhena87/AoE2HD.control/blob/main/docs/hd-object-api-v1.md), [mapping](https://github.com/marcosvilhena87/AoE2HD.mapping). A matriz [CSV v2](hd-compatibility-matrix-v2.csv) é o registro estruturado.

## Legenda

- `implementado_experimental`: método existe, depende de dados/offsets ainda não completamente validados.
- `implementado_limitado` e `filtro_parcial`: implementa apenas subconjunto explícito, sem enumerar todo o mundo.
- `instrumentacao_v1_9`: capturas e comparações de seleção, **não** getter estável nem seleção global.
- `candidato_exposto`/`candidato_nao_exposto`: campo de memória hipotético; retorno pode ser nulo.
- `nao_implementado`/`nao_implementado_na_api`: não se identificou contrato equivalente implementado na API verificada.
- `base_validada` (mapping) refere-se **somente à evidência da dependência**, nunca à API completa.
- `bloqueado`: não há mecanismo de despacho de comandos HD validado.
- `pendente`/`parcial`: provas incompletas. `independente`: protótipo pode existir sem offsets.

## Inventário reconciliado

| ID | Contrato DE | Prioridade | Estado do control | Evidência principal / limitação |
|---|---|---|---|---|
| OBJ-001 | `GetObjectById` | P0 | `implementado_experimental` | World+0x0E8; Object+0x08 candidato; ID conhecido, comparação interna; sem prova de cobertura global |
| OBJ-002 | `GetObjectsByClass` | P0 | `implementado_limitado` | Object+0x078; Object78Target+0x00C; Filtro apenas IDs fornecidos; não lista global exaustiva |
| PLY-001 | `GetAssignedPlayer` | P0 | `implementado_experimental` | World+0x174; World+0x184/188; PlayerEntry+0x00; Cadeia histórica, sem assinatura robusta de binário |
| OBJ-003 | `GetObjectsInArea` | P0 | `nao_implementado` | Object+0x3C/+0x40 posição candidata; Sem consulta espacial; requer geometria e enumeração |
| CMD-001 | `UnitsMove` | P0 | `nao_implementado` | Sem despacho de ordem HD validado; Não equiparar ordem manual a API programática |
| OBJ-004 | `Object:GetPosition` | P0 | `candidato_nao_exposto` | Object+0x3C/+0x40 experimentais; API retorna position=None intencionalmente |
| OBJ-005 | `Player:GetSelectedObject` | P0 | `instrumentacao_v1_9` | Player+0x15C/+0x160; Object+0x38 & 0x10000 candidatos; Apenas IDs monitorados; sem lista global nem getter estável |
| OBJ-006 | `Object:GetOwner` | P1 | `candidato_exposto` | Object+0x10 candidato; Atributo candidato, não equivalência validada |
| OBJ-007 | `GetObjectsByType` | P1 | `filtro_parcial` | ObjectTypeTarget+0x10; Tipo obtido por objeto; enumeração por tipo não demonstrada |
| PLY-002 | `GetResourceFacts` | P1 | `nao_implementado_na_api` | WorldPlayer+0x3C; ResourceTable+0x00/+0x04/+0x08/+0x0C; Evidência no mapping não constitui método publicado no control |
| PLY-003 | `GetVillagerCount` | P1 | `nao_implementado_na_api` | ResourceTable+0x094; Dependência catalogada; getter não verificado no control |
| CMD-002 | `UnitsTargetObject` | P1 | `nao_implementado` | Tipos e alvos conhecidos parcialmente; ordem desconhecida; Coleta observada não prova despacho programático |
| CMD-003 | `UnitsBuildStructure` | P1 | `nao_implementado` | Genie IDs parciais, comando desconhecido; Sem emissor funcional |
| MAP-001 | `GetMapTile / IsWalkable` | P1 | `nao_implementado` | Grid/colisão sem validação suficiente; Apenas leitura de navegação, não edição |
| CMD-004 | `TrainUnit / ResearchTechnology` | P1 | `nao_implementado` | Building+0x214/+0x218/+0x21C experimental; Observação de fila não prova emissão |
| OBJ-008 | `Object:GetHP` | P2 | `nao_implementado` | Object+0x34 candidato; Valor plausível não validado como HP |
| SES-001 | `GetGameTime / GameState` | P2 | `nao_implementado` | Relógio/frame sem contrato completo; Sem getter equivalente demonstrado |
| IPC-001 | `IPC.StartServer / Agent Bridge V3` | P2 | `nao_implementado` | Não depende diretamente de offsets para ping/pong; Protocolo DE é referência, não binário reutilizável |
| UI-001 | `Settings / Render` | P2 | `nao_implementado` | Configuração/log não requer acesso à memória; Overlay/render ainda não existente |

## Mudanças em relação à v1

1. **OBJ-001, OBJ-002, PLY-001:** infraestrutura somente leitura e métodos experimentais existem no `object_api.py`; a v1 dizia que não havia leitura de processo.
2. **OBJ-005:** instrumentos para seleção simples/múltipla v1.7–v1.9 já foram adicionados. O bit de seleção e os dois ponteiros continuam candidatos. A v1.9 pede três IDs reais distintos; exemplos artificiais **não são evidência**.
3. **OBJ-004:** coordenadas experimentais constam no mapping, mas `get_object_by_id` retorna `position=None` deliberadamente; não elevar a implementado.
4. **OBJ-006:** proprietário candidato é exposto com opt-in; sem confirmação abrangente de Gaia e adversários.
5. **OBJ-007:** não confundir leitura do Genie Type ID para IDs conhecidos com enumeração global `GetObjectsByType`.
6. **Comandos, mapa, IPC e UI:** não promover a implementados sem código e prova específica. A ausência de teste real impede status `validado_em_jogo`.

## Protocolo para promover estado

Para cada linha: (a) identificar arquivo, símbolo e teste automático; (b) registrar build do processo x86 e hash quando disponível; (c) capturar entrada/saída e transição manual observável, idealmente em duas sessões; (d) separar hipóteses, erro de leitura e resultado ausente; (e) registrar novas evidências de memória **primeiro no mapping**; (f) distinguir teste unitário simulado de teste de integração real.

**Proibições:** não inferir cobertura global pela varredura de IDs limitada, não supor que dois ponteiros definem lista de seleção, não reutilizar IDs de sessão, não considerar `--allow-candidates` validação, não reutilizar DLL/ABI DE na HD, não executar automação em multiplayer competitivo.

## Próxima sequência sugerida

1. **Gate A — estabilidade de identidade:** duas partidas e três classes, IDs ausentes, reutilização de ID, assinatura do binário, comparação com a UI.
2. **Gate B — seleção v1.9:** capturar `clear`, `single_a/b/c`, `multi_abc`, `multi_cba`, `clear_after`, com IDs conhecidos; produzir evidências e investigar lista global.
3. **Gate C — posição:** registrar dependências candidatas no mapping, confirmar escala/eixos e diferenciar posição de alvo.
4. **Gate D — coleção:** medir limites da tabela e cobertura antes de afirmar `GetObjectsByClass/Type/InArea`.
5. **Gate E — economia/comandos:** getters observáveis primeiro; emissão de ordens apenas quando protocolo offline de aceitação e execução estiver comprovado.

## Rastreabilidade e escopo

A atualização altera **apenas documentação** do repositório de investigação. Não modifica catálogos de memória ou código do motor. Estados relatados são inferidos de arquivos publicados em 20/10/2026 e podem precisar de atualização após resultados de capturas locais. O README do control descreve v0.1, mas seus módulos de API e seleção são posteriores; esta inconsistência editorial está explicitamente registrada, não corrigida aqui.
