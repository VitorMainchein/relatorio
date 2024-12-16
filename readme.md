# Relatório de Teste de Desempenho

## Cabeçalho

- **Conclusão:** O teste revelou que o sistema não atende aos critérios de sucesso esperados em relação ao tempo médio de resposta, taxa de erro e vazão. Além disso, foram observados altos tempos de resposta e uma taxa de erro elevada, especialmente sob carga máxima. Sugere-se a realização de otimizações no sistema, incluindo a identificação de gargalos, melhorias na escalabilidade e a implementação de cache para melhorar o desempenho geral.
- **O que:** Testes de desempenho utilizando o JMeter, simulando cenários de carga, estresse e resistência para avaliar o desempenho do sistema.
- **Quem:** Equipe de Testes de Desempenho da empresa (ou equipe de desenvolvimento ou responsável pelo teste).
- **Quando:** Teste realizado em [inserir data], com a utilização do JMeter para simulação de 2000 usuários simultâneos e 18.000 requisições.

## Introdução

### Descrição

Este relatório apresenta os resultados de um teste de desempenho realizado no sistema utilizando o JMeter. O objetivo foi avaliar como o sistema lida com diferentes tipos de carga (média, máxima e sustentada) e identificar possíveis pontos de falha. Os testes foram realizados para medir o tempo de resposta, taxa de erro e vazão sob diferentes condições.

### Detalhes

- **Ferramenta utilizada:** JMeter
- **Protocólo de requisição:** HTTPS
- **Tipo de requisição:** GET
- **Número de usuários simulados:** 2000
- **Tempo entre as requisições:** 5 segundos
- **Número de iterações:** 1

### Objetivos

1. **Cenário de Carga:** Avaliar o desempenho do sistema com um número médio de requisições (18.000) e verificar como o sistema lida com acessos simultâneos.
2. **Cenário de Estresse:** Testar o sistema até seu limite para medir a performance sob carga máxima.
3. **Cenário de Resistência:** Avaliar a estabilidade do sistema ao longo de um período de carga sustentada e observar as variações no tempo de resposta.

### Setup

O teste foi configurado com os seguintes parâmetros principais no JMeter:

- **Protocolo:** HTTPS
- **Servidor:** [Link fornecido pelo professor]
- **Tipo de requisição:** GET
- **Número de usuários:** 2000
- **Tempo entre as requisições:** 5 segundos
- **Iterações:** 1
- **Configuração de relatórios:** Árvores de Resultados, Relatórios de Sumário

## Critérios de Aceitação

### Critérios Esperados

1. **Tempo Médio de Resposta:**
   - **Esperado:** Menor que 2.000 ms
   - **Resultado:** 7.998 ms (não atende)

2. **Taxa de Erro:**
   - **Esperado:** Menor que 1%
   - **Resultado:** 8,15% (não atende)

3. **Vazão (Throughput):**
   - **Esperado:** Maior que 100 requisições por segundo
   - **Resultado:** 51,4 requisições por segundo (não atende)

## Análise dos Resultados

- **Cenário de Carga:**
  - **Tempo Médio de Resposta:** 7.998 ms, o que é significativamente maior que o valor esperado (2.000 ms).
  - **Taxa de Erro:** 8,15%, muito acima do limite de 1%, indicando que o sistema apresentou falhas frequentes.
  - **Vazão:** 51,4 requisições por segundo, o que está bem abaixo do esperado (100 requisições por segundo).

- **Cenário de Estresse:**
  - **Tempo Máximo de Resposta:** O maior tempo registrado foi 42.755 ms, indicando que o sistema não consegue suportar altos picos de carga sem sofrer degradação severa.
  
- **Cenário de Resistência:**
  - **Desvio Padrão do Tempo de Resposta:** 5.812,66 ms, mostrando uma variação significativa nos tempos de resposta, o que implica em inconsistência no desempenho ao longo do tempo.

## Pontos de Falha Identificados

- **Altos Tempos de Resposta:** O tempo médio e máximo de resposta estão elevados, o que sugere a presença de gargalos no sistema.
- **Alta Taxa de Erros:** A taxa de erro elevada pode indicar problemas de infraestrutura ou falhas na aplicação sob carga.
- **Desempenho Insuficiente sob Carga Máxima:** O sistema não suporta adequadamente a carga máxima testada, resultando em degradação severa.
- **Inconsistência no Desempenho:** O alto desvio padrão nos tempos de resposta indica que o sistema não mantém um desempenho consistente, especialmente sob carga sustentada.

## Sugestões de Otimização

1. **Identificação de Gargalos:** Realizar uma análise detalhada para identificar gargalos no banco de dados, na rede ou no código da aplicação.
2. **Escalabilidade Horizontal:** Considerar a implementação de escalabilidade horizontal, adicionando mais servidores para distribuir a carga e melhorar o desempenho.
3. **Implementação de Caching:** Adotar cache para reduzir a pressão no backend e melhorar o tempo de resposta para requisições repetidas.
4. **Monitoramento Contínuo:** Implementar ferramentas de monitoramento em tempo real para identificar problemas de desempenho antes que afetem os usuários finais.
5. **Otimização de Código:** Revisar partes críticas do código, buscando oportunidades de otimização, como a redução de complexidade e a melhoria na eficiência de algoritmos.
6. **Rate Limiting:** Aplicar limites de taxa (rate limiting) para evitar acessos abusivos que possam sobrecarregar o sistema.
7. **Testes Iterativos:** Após as otimizações, realizar novos testes para validar as melhorias implementadas.

## Conclusão Final

O sistema apresentou um desempenho insatisfatório em todos os critérios de aceitação, com altos tempos de resposta, alta taxa de erros e baixa vazão. A implementação das otimizações sugeridas é necessária para melhorar a performance do sistema e atender aos critérios de sucesso estabelecidos.
