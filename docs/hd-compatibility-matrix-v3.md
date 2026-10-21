# HD Compatibility Matrix v3 — 21/10/2026

## Escopo e proveniência

Revisão de **19 grupos de contratos**, preservando o inventário da [v2](hd-compatibility-matrix-v2.md). Compara contratos AoE2Control DE, implementações publicadas de [AoE2HD.control](https://github.com/marcosvilhena87/AoE2HD.control) e evidências registradas em [AoE2HD.mapping](https://github.com/marcosvilhena87/AoE2HD.mapping). Fonte estruturada: [CSV v3](hd-compatibility-matrix-v3.csv).

**Não** certifica compatibilidade binária DE/HD, API completa, qualidade de execução no Windows nem layout de memória definitivo. A versão-alvo declarada para os testes de seleção é `AoK HD.exe 5.8.INT`, PE32/x86, sem SHA-256 da build anexado às capturas.

## Eixos independentes de classificação

- **Estado de implementação:** existência de código ou instrumentação no control; não garante funcionamento efetivo.
- **Nível de evidência:** `pendente`, `parcial`, `validado_experimentalmente_escopo`, `bloqueado` ou `independente`. A evidência experimental é *restrita à observação descrita*.
- **Layout de memória:** `candidato` permanece candidato até validação independente. Não confundir `validado_experimentalmente` com `validado` canônico ou layout definitivo.
- **Equivalência de API DE:** nenhuma linha obtém equivalência plena por simples similaridade de assinatura.

## Inventário reconciliado

| ID | Contrato DE | Prioridade | Estado HD | Evidência HD | Restrição |
|---|---|---|---|---|---|
| OBJ-001 | `GetObjectById` | P0 | `implementado_experimental` | `parcial` | Identidade para IDs conhecidos; sem cobertura global |
| OBJ-002 | `GetObjectsByClass` | P0 | `implementado_limitado` | `parcial` | Filtro de IDs conhecidos; não é enumeração global |
| PLY-001 | `GetAssignedPlayer` | P0 | `implementado_experimental` | `parcial` | Cadeia de jogador candidata; build não verificada por hash |
| OBJ-003 | `GetObjectsInArea` | P0 | `nao_implementado` | `pendente` | Coordenadas e coleção espacial não comprovadas |
| CMD-001 | `UnitsMove` | P0 | `nao_implementado` | `bloqueado` | Despacho programático HD não validado |
| OBJ-004 | `Object:GetPosition` | P0 | `candidato_nao_exposto` | `pendente` | Posição retorna None; offsets candidatos |
| OBJ-005 | `Player:GetSelectedObject` | P0 | `instrumentacao_v2_6` | `validado_experimentalmente_escopo` | Enumeração por contador candidato em 0,60 móveis e 15 construções; não é getter DE plenamente equivalente |
| OBJ-006 | `Object:GetOwner` | P1 | `candidato_exposto` | `pendente` | Dono é atributo opt-in candidato |
| OBJ-007 | `GetObjectsByType` | P1 | `filtro_parcial` | `parcial` | Filtro por IDs existentes, não consulta global |
| PLY-002 | `GetResourceFacts` | P1 | `nao_implementado_na_api` | `pendente` | Mapeamento de recursos não implica getter |
| PLY-003 | `GetVillagerCount` | P1 | `nao_implementado_na_api` | `pendente` | Contador catalogado não implica getter publicado |
| CMD-002 | `UnitsTargetObject` | P1 | `nao_implementado` | `bloqueado` | Coleta observada não prova envio de ordem |
| CMD-003 | `UnitsBuildStructure` | P1 | `nao_implementado` | `bloqueado` | Sem mecanismo de construção validado |
| MAP-001 | `GetMapTile / IsWalkable` | P1 | `nao_implementado` | `pendente` | Malha e colisão carecem de prova |
| CMD-004 | `TrainUnit / ResearchTechnology` | P1 | `nao_implementado` | `bloqueado` | Fila observada não é emissão de comando |
| OBJ-008 | `Object:GetHP` | P2 | `nao_implementado` | `pendente` | Offset candidato não confirmado como HP |
| SES-001 | `GetGameTime / GameState` | P2 | `nao_implementado` | `pendente` | Sem getter equivalente estabelecido |
| IPC-001 | `IPC.StartServer / Agent Bridge V3` | P2 | `nao_implementado` | `independente` | Possível protótipo de protocolo sem offsets; sem equivalência binária |
| UI-001 | `Settings / Render` | P2 | `nao_implementado` | `independente` | Interface e renderização não implementadas |

## Revisão especial OBJ-005 — Selected Objects API v2.6

A v2 documentava apenas a instrumentação v1.9; a v3 incorpora o código [v2.6](https://github.com/marcosvilhena87/AoE2HD.control/blob/main/aoe2hdcontrol/selected_objects_v2_6.py), [contrato e comando de teste](https://github.com/marcosvilhena87/AoE2HD.control/blob/main/docs/selected-objects-api-v2-6.md) e [registro experimental do mapping](https://github.com/marcosvilhena87/AoE2HD.mapping/blob/main/docs/evidencia_selecao_v2_6_2026-10-21.md).

| Campo | Observação reproduzida | Interpretação permitida |
|---|---|---|
| `LocalPlayer+0x160` | Primeiro ponteiro de seleção; entradas sucessivas de 4 bytes | Início observado de vetor contíguo, não dimensão física conhecida |
| `LocalPlayer+0x24C` | Entrada índice 59 verificada no teste com 60 móveis | 60 é limite observado de interface móvel, não capacidade estrutural |
| `LocalPlayer+0x254` | Contagens 0/60/15 na v2.6 e 32/40/50 na v2.5 | Candidato forte a contador, **não** validado canonicamente |
| `Object+0x38 & 0x00010000` | Bit presente nos objetos selecionados verificados | Máscara de seleção observada, demais bits desconhecidos |
| `LocalPlayer+0x15C` | Varia como referência a objeto em ensaios anteriores | Sem semântica conclusiva, não contador |
| `LocalPlayer+0x250` | Variabilidade incompatível com contador simples ou 61º ponteiro | Significado desconhecido |

**Capturas resumidas:** `selected_v2_6_clear.json`, `selected_v2_6_60.json`, `selected_v2_6_buildings.json`. O registro informa contagens estáveis nas três leituras e ausência de entradas inválidas, duplicadas e de flags divergentes. Os JSON brutos foram fornecidos pelo operador na conversa, **não estão versionados no repositório mapping**; esta matriz referencia somente a evidência documental publicada.

**Restrições fundamentais:** as leituras não são atômicas e não excluem substituição de objetos com contagem constante; `completeness=unknown`; testes não foram repetidos após reiniciar o executável; capacidade de seleção de construções não foi estabelecida; o vetor de selecionados **não** é a tabela global de objetos do World. A v2.6 restringe leitura a `count * 4`, com contador de 0 a 60, sem provar limite de memória.

## Diferenças v2 → v3

1. OBJ-005 migra de instrumentação v1.9 para **instrumentação v2.6 com evidência experimental delimitada**.
2. O registro de seleção passa a distinguir limite da interface, janela de leitura e capacidade física desconhecida.
3. A contagem candidata em `+0x254` e a máscara `0x10000` são explicitadas sem promoção automática a offsets definitivos.
4. Estados dos demais 18 contratos permanecem conservadores; a revisão de seleção não valida comandos, coleção global, posição ou mapas.
5. Evidência documentada no mapping é separada dos JSON brutos não versionados.

## Gates de aceitação da v4

1. **Build e repetibilidade:** anexar identificação de executável, SHA-256, sessões separadas e evidências após reinício.
2. **Seleção:** 0/1/várias unidades, grupos móveis e construções, trocas com contagem igual, mutação durante leitura, flags e identidade; distinguir estabilidade de snapshot e cobertura completa.
3. **Layout:** medir limites sem assumir que `+0x250` seja entrada válida, confirmar semântica de `+0x15C`, manter candidatos no mapping até prova independente.
4. **Coleção e posição:** validar objetos em área, enumeração global por classe/tipo, eixos e escala mediante transições controladas.
5. **Comandos:** separar intenção emitida, aceitação e execução observada. Apenas ambiente offline/local.
6. **Regressão:** verificar unicidade dos 19 IDs, correspondência CSV/Markdown e consistência das classificações; testes simulados não equivalem a testes no jogo.

## Política de manutenção

O `AoE2HD.aoe2control` documenta compatibilidade e contratos; o `AoE2HD.control` implementa; o `AoE2HD.mapping` é a fonte de referência para estruturas e identificadores. Mudanças de memória devem ser evidenciadas primeiro no mapping. Nenhuma atualização neste documento altera código do motor nem promove candidatos no catálogo canônico.
