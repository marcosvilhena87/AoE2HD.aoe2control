# Protocolo de investigação e evidência

Para cada funcionalidade, abrir um registro com:

- Identificador, nome e domínio.
- Fonte primária e data de consulta.
- Assinatura da API, parâmetros e retornos, quando conhecidos.
- Comportamento da UI (menu, padrão, atalhos, estados).
- Condições de uso e causas de rejeição/erro.
- Diferenças conhecidas DE × HD e **lacunas de evidência**.
- Experimento proposto no HD, cenário e passos reproduzíveis.
- Resultado, logs, versão exata do executável e status.
- Contrato sugerido para `AoE2HD.control` e testes de aceitação.

## Estados

- `documentado_DE`: observado na documentação primária; sem afirmação sobre HD.
- `a_investigar_HD`: sem evidência suficiente.
- `viavel_HD`: demonstrado por experimento reproduzível no HD.
- `implementado_HD`: código e testes publicados em `AoE2HD.control`.
- `bloqueado_HD`: evidência de incompatibilidade/limitação documentada.

## Regras entre repositórios

- Não executar um recurso neste repositório de pesquisa.
- Não copiar catálogos nem criar nova fonte de verdade para endereços.
- Novos endereços e IDs vão para `AoE2HD.mapping`; candidatos permanecem candidatos.
- O `AoE2HD.control` referencia registros canônicos e implementa o comportamento.
- Manter separado o que é especificação DE, hipótese HD, experimento e validação efetiva.
