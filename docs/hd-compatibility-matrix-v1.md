# HD Compatibility Matrix v1 — 20/10/2026

**Finalidade:** mapear contratos DE para capacidades *demonstradas* no HD; sem edição de mapas; leitura de terreno para navegação permitida.

**Referência DE:** [API Audit v2](api-audit-v2-relatorio.md) e [catálogo de assinaturas](api-audit-v2-contratos.md).

**Fontes HD consultadas:**
- [AoE2HD.mapping / README](https://github.com/marcosvilhena87/AoE2HD.mapping/blob/main/README.md)
- [estruturas de memória (64 registros)](https://github.com/marcosvilhena87/AoE2HD.mapping/blob/main/dados/enderecos.csv)
- [classes](https://github.com/marcosvilhena87/AoE2HD.mapping/blob/main/dados/catalogos/classes_objetos.csv)
- [Genie IDs](https://github.com/marcosvilhena87/AoE2HD.mapping/blob/main/dados/genie_type_ids.csv)
- [identidades de sessão](https://github.com/marcosvilhena87/AoE2HD.mapping/blob/main/dados/catalogos/identidades_individuais.csv)
- [coordenadas v9.13](https://github.com/marcosvilhena87/AoE2HD.mapping/blob/main/docs/coordenadas_aldeoes_v9_13_2026-10-18.md)
- [identidade experimental](https://github.com/marcosvilhena87/AoE2HD.mapping/blob/main/docs/evidencia_identidade_aldeoes_2026-10-17.md)
- [AoE2HD.control / README v0.1](https://github.com/marcosvilhena87/AoE2HD.control/blob/main/README.md)
- [consumidor de catalogos](https://github.com/marcosvilhena87/AoE2HD.control/blob/main/aoe2hdcontrol/catalog.py)

## Resultado executivo

O mapping ja oferece dados validados para *partes* de identidade por objeto, classe, tipo e recursos. Isso nao equivale a dizer que o contrato completo de qualquer API DE ja foi implementado no HD. O `AoE2HD.control` publica apenas infraestrutura v0.1, sem leitura nem escrita de memoria do processo. Portanto **zero linhas da matriz sao classificadas como `implementado_HD`**.

O campo `status_hd` descreve *prontidao das dependencias* — nao conformidade da API. Significados:
- `base_validada`: dependencias centrais do campo especifico com status validado no mapping; contrato de API ainda nao construido
- `base_parcial`: parte da cadeia validada, outras partes candidatas/nao demonstradas
- `candidato_forte`: evidencia experimental reproduzida, mas falta validacao de semantica/escala
- `candidato`: hipotese sem prova suficiente
- `dependencia_pendente`: ausencia de parte indispensavel ou dependencia sem caracterizacao completa
- `bloqueado_comando`: nao existe caminho de emissao de comando HD validado
- `independente_de_memoria`: possivel componente de infraestrutura sem equivalencia comprovada com a DE

## Matriz completa desta fase (19 contratos agrupados)

| ID | API DE | Prioridade | Prontidao HD | Dependencias |
|---|---|---|---|---|
| OBJ-001 | `GetObjectById` | P0 | `base_parcial` | /W/o/r/l/d/+/0/x/0/E/8/ /[/v/a/l/i/d/a/d/o/]/;/ /O/b/j/e/c/t/+/0/x/0/8/ /[/h/i/p/o/t/e/s/e/]/ |
| OBJ-002 | `GetObjectsByClass` | P0 | `base_parcial` | /O/b/j/e/c/t/+/0/x/0/7/8/ /[/v/a/l/i/d/a/d/o/]/;/ /O/b/j/e/c/t/7/8/T/a/r/g/e/t/+/0/x/0/0/C/ /[/v/a/l/i/d/a/d/o/]/;/ /W/o/r/l/d/+/0/x/0/E/8/ /[/v/a/l/i/d/a/d/o/]/ |
| PLY-001 | `GetAssignedPlayer` | P0 | `base_parcial` | /W/o/r/l/d/+/0/x/1/7/4/;/ /W/o/r/l/d/+/0/x/1/8/4///1/8/8/;/ /P/l/a/y/e/r/E/n/t/r/y/+/0/x/0/0/ /[/h/i/s/t/o/r/i/c/o/_/v/a/l/i/d/a/d/o/]/ |
| OBJ-003 | `GetObjectsInArea` | P0 | `dependencia_pendente` | /O/b/j/e/c/t/+/0/x/3/C///+/0/x/4/0/ /c/a/n/d/i/d/a/t/o/s/;/ /W/o/r/l/d/+/0/x/0/E/8/ /v/a/l/i/d/a/d/o/ |
| CMD-001 | `UnitsMove` | P0 | `bloqueado_comando` | /S/e/m/ /c/a/d/e/i/a/ /p/u/b/l/i/c/a/ /d/e/ /c/o/m/a/n/d/o/ /H/D/ /v/a/l/i/d/a/d/a/ |
| OBJ-004 | `Object:GetPosition` | P0 | `candidato_forte` | /O/b/j/e/c/t/+/0/x/3/C/ /X/;/ /O/b/j/e/c/t/+/0/x/4/0/ /Y/ /[/e/v/i/d/e/n/c/i/a/ /v/9/./1/3/;/ /n/a/o/ /c/a/n/o/n/i/c/a/m/e/n/t/e/ /v/a/l/i/d/a/d/o/s/]/ |
| OBJ-005 | `Player:GetSelectedObject` | P0 | `base_parcial` | /L/o/c/a/l/P/l/a/y/e/r/+/0/x/1/5/C///+/0/x/1/6/0/ /[/a/n/c/o/r/a/_/e/x/p/e/r/i/m/e/n/t/a/l/]/;/ /O/b/j/e/c/t/+/0/x/0/8/ /[/h/i/p/o/t/e/s/e/]/ |
| OBJ-006 | `Object:GetOwner` | P1 | `candidato` | /O/b/j/e/c/t/+/0/x/1/0/ /[/h/i/p/o/t/e/s/e/]/;/ /W/o/r/l/d/P/l/a/y/e/r/ |
| OBJ-007 | `GetObjectsByType` | P1 | `base_parcial` | /O/b/j/e/c/t/T/y/p/e/T/a/r/g/e/t/+/0/x/1/0/ /[/v/a/l/i/d/a/d/o/]/;/ /W/o/r/l/d/+/0/x/0/E/8/ /[/v/a/l/i/d/a/d/o/]/ |
| PLY-002 | `GetResourceFacts` | P1 | `base_parcial` | /W/o/r/l/d/P/l/a/y/e/r/+/0/x/3/C/ /e/ /R/e/s/o/u/r/c/e/T/a/b/l/e/+/0/x/0/0///+/0/x/0/4///+/0/x/0/8///+/0/x/0/C/ /[/h/i/s/t/o/r/i/c/o/_/v/a/l/i/d/a/d/o/]/ |
| PLY-003 | `GetVillagerCount` | P1 | `base_validada` | /R/e/s/o/u/r/c/e/T/a/b/l/e/+/0/x/0/9/4/ /[/v/a/l/i/d/a/d/o/]/ |
| CMD-002 | `UnitsTargetObject` | P1 | `bloqueado_comando` | /T/i/p/o/ /e/ /a/l/v/o/ /p/a/r/c/i/a/l/m/e/n/t/e/ /c/o/n/h/e/c/i/d/o/s/;/ /o/r/d/e/m/ /H/D/ /n/a/o/ /m/a/p/e/a/d/a/ |
| CMD-003 | `UnitsBuildStructure` | P1 | `bloqueado_comando` | /G/e/n/i/e/ /T/y/p/e/ /I/D/s/ /p/a/r/c/i/a/i/s/;/ /s/i/s/t/e/m/a/ /d/e/ /o/r/d/e/m/ /d/e/s/c/o/n/h/e/c/i/d/o/ |
| MAP-001 | `GetMapTile / IsWalkable` | P1 | `dependencia_pendente` | /S/e/m/ /e/s/t/r/u/t/u/r/a/ /d/e/ /g/r/i/d///c/o/l/i/s/a/o/ /v/a/l/i/d/a/d/a/ /n/o/ /c/a/t/a/l/o/g/o/ /a/u/d/i/t/a/d/o/ |
| CMD-004 | `TrainUnit / ResearchTechnology` | P1 | `dependencia_pendente` | /B/u/i/l/d/i/n/g/+/0/x/2/1/4///2/1/8///2/1/C/ /[/e/x/p/e/r/i/m/e/n/t/a/l/_/i/m/p/l/e/m/e/n/t/a/d/o/]/;/ /c/a/m/p/o/s/ /d/e/ /t/r/e/i/n/a/m/e/n/t/o/ /c/a/n/d/i/d/a/t/o/s/ |
| OBJ-008 | `Object:GetHP` | P2 | `candidato` | /O/b/j/e/c/t/+/0/x/3/4/ /[/h/i/p/o/t/e/s/e/]/ |
| SES-001 | `GetGameTime / GameState` | P2 | `dependencia_pendente` | /S/e/m/ /c/o/n/t/r/a/t/o/ /c/a/n/o/n/i/c/o/ /c/o/m/p/l/e/t/o/ /d/e/ /t/e/m/p/o///f/r/a/m/e/ |
| IPC-001 | `IPC.StartServer / Agent Bridge V3` | P2 | `independente_de_memoria` | /P/r/o/t/o/c/o/l/o/s/ /D/E/ /s/a/o/ /r/e/f/e/r/e/n/c/i/a/s/;/ /H/D/ /r/e/q/u/e/r/ /i/m/p/l/e/m/e/n/t/a/c/a/o/ /p/r/o/p/r/i/a/ |
| UI-001 | `Settings / Render` | P2 | `independente_de_memoria` | /U/I/ /e/ /l/o/g/ /n/a/o/ /d/e/p/e/n/d/e/m/ /d/e/ /o/f/f/s/e/t/ /p/a/r/a/ /p/r/o/t/o/t/i/p/o/ |

A matriz estruturada detalhada, incluindo limites e proximo teste, esta em [hd-compatibility-matrix-v1.csv](hd-compatibility-matrix-v1.csv). Alguns grupos representam mais de uma funcao; **19 linhas nao sao equivalentes a 19 assinaturas individuais**.

## Dependencias e bloqueios criticos

1. **Identidade e enumeracao:** a tabela `World+0x0E8` foi validada funcionalmente, mas nao demonstra que todos os objetos do mundo podem ser percorridos com cobertura exaustiva.
2. **Classe x profissao:** `Object78Target+0x00C` identifica classe; tipos de lenhador, mineiro e coletor refletem tipo/profissao, e podem mudar com a atividade. Nunca classificar classe de aldeao apenas pelo tipo de trabalho.
3. **Object ID x Genie Type ID:** `Object+0x08` e campo individual candidato; `ObjectTypeTarget+0x10` e tipo especifico validado; nao intercambiar os domínios.
4. **Posicao:** `Object+0x3C/+0x40` observados em v9.13 (20 amostras, 3 aldeoes), com movimento consistente de um objeto. Escala e convencao dos eixos pendentes.
5. **Selecionado e proprietario:** `LocalPlayer+0x15C/+0x160` sao ancoras experimentais e `Object+0x10` segue hipotese.
6. **Comandos:** existencia de ordem nativa dada pelo jogador **nao equivale** a descobrir interface segura de emissao por programa. Separar solicitação, aceitação e execução.
7. **Infraestrutura:** o controle HD permanece somente leitura de catálogos (nao do processo). Todas as linhas estao nao implementadas no atual main.
8. **Seguranca:** somente partidas locais/offline; sem injetar DLL DE no HD nem presumir ABI compativel.

## Critérios de saida: HD Object API v1

- Integrar leitura somente do processo do HD apos identificar binario/processo e versao.
- Construir snapshots imutaveis com id, classe, tipo, dono (se validado) e posicao (com campo `candidate` enquanto pendente).
- Tratar ponteiro nulo, objeto deletado, troca de partida, ID reaproveitado e leitura incoerente.
- Testar 2 sessoes, 3 classes distintas, ausencia de selecao e objeto inexistente.
- Catalogo mapping permanece a unica fonte de verdade; novas descobertas vao primeiro para la com origem e evidencia.
- Nao publicar `implementado_HD` ate teste em binario HD verificavel.

## Ordem recomendada

**Gate A**: processo x86 e assinatura de versao → **Gate B**: snapshot jogador e objeto por ID → **Gate C**: filtros de classe e tipo → **Gate D**: coordenadas e consulta espacial → **Gate E**: estudos de ordens/comandos. IPC e interface depois dos gates de leitura.
