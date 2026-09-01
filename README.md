# tcc

✅ Identificação

Nome: Guilherme Fuchter dos Santos (Gui)
Turma: 8AN, Engenharia de Software, 8º de 9 semestres
Orientador: Prof. Leanderson


✅ Tema (título)

Otimização Dinâmica de Testes A/B em Sistemas Web de Rastreamento de Eventos

✅ Tema texto dissertativo, 1.1

"Testes A/B são amplamente utilizados por sistemas web para comparar variantes de páginas, funcionalidades e fluxos de conversão, permitindo decisões orientadas por dados sobre qual versão apresenta melhor desempenho. Tradicionalmente, esses testes utilizam um modelo de divisão estática de tráfego, no qual os usuários são distribuídos de forma fixa e igualitária entre as variantes durante toda a execução do experimento, independentemente dos resultados parciais observados.

Como alternativa a esse modelo, algoritmos de otimização dinâmica de tráfego, como os baseados em aprendizado por reforço, a exemplo dos algoritmos de bandit, propõem ajustar a distribuição de tráfego em tempo real, direcionando gradualmente mais usuários para a variante que apresenta melhor desempenho ao longo do próprio teste. Embora essa abordagem prometa maior eficiência na identificação de variantes vencedoras, sua adoção introduz uma tensão pouco explorada na prática: a possível perda de confiabilidade estatística das métricas de conversão coletadas, decorrente da tomada de decisão sobre dados ainda parciais.

Este trabalho insere-se na área de Engenharia de Software, com foco na aplicação de algoritmos de otimização a sistemas de rastreamento de eventos, investigando o desenvolvimento de um sistema web de testes A/B que incorpore um mecanismo de otimização dinâmica de tráfego nativamente em sua arquitetura."

✅ Questão de Pesquisa

"Quais os trade-offs entre otimização dinâmica de tráfego e confiabilidade de métricas de conversão em testes A/B?"

✅ Objetivo Geral

"Desenvolver um sistema web de rastreamento de eventos e testes A/B com um mecanismo de otimização dinâmica de tráfego, investigando os trade-offs entre essa otimização e a confiabilidade das métricas de conversão coletadas."

✅ Objetivos Específicos (1.4)

a. Levantar, na literatura, os principais algoritmos de otimização dinâmica de alocação de tráfego aplicáveis a testes A/B;
b. Projetar a arquitetura de um sistema web de rastreamento de eventos e testes A/B capaz de coletar métricas de conversão em tempo real;
c. Implementar um mecanismo de otimização dinâmica de tráfego integrado a esse sistema;
d. Comparar os resultados obtidos com o mecanismo de otimização dinâmica em relação a um modelo de divisão estática de tráfego, quanto a desempenho e confiabilidade estatística das métricas coletadas.

✅ Justificativa (1.2)

Contextualização: A adoção de testes A/B é uma prática consolidada no desenvolvimento de produtos digitais, sendo utilizada para validar decisões de design, funcionalidades e estratégias de conversão com base em evidência empírica. O modelo tradicional de divisão estática de tráfego mantém parte dos usuários expostos a variantes de desempenho inferior durante toda a duração do teste. Modelos de otimização dinâmica respondem a essa limitação, mas podem comprometer a validade estatística da métrica que se pretende otimizar (peeking problem).

Delimitação: desenvolvimento de um sistema web de rastreamento de eventos e testes A/B com mecanismo de otimização dinâmica de tráfego, e avaliação comparativa frente a um modelo de divisão estática.

Relevância científica e acadêmica: investigação empírica dos trade-offs entre eficiência de otimização e confiabilidade estatística, pouco explorada na literatura nacional.

Relevância social: sistemas de teste A/B mais eficientes reduzem o tempo de exposição de usuários a experiências de pior qualidade.

Relevância para a formação acadêmica: experiência prática em otimização aplicada, arquitetura de software, estatística aplicada e engenharia de dados.

Viabilidade: prazo compatível com experiência prévia do estudante em sistemas web e rastreamento de eventos, com acesso a ambientes de validação controlados (simulação) e, potencialmente, ambiente real de produção.

Questão de pesquisa (reafirmada dentro da Justificativa, conforme exige o template): "Quais os trade-offs entre otimização dinâmica de tráfego e confiabilidade de métricas de conversão em testes A/B?"

✅ Cronograma e Plano de Ação (3.5)

| Período | Atividade |
|---|---|
| 01/08 a 01/09 | Capítulo 1, Definição do Projeto |
| 02/09 a 29/09 | Capítulo 2, Revisão da Literatura |
| 30/09 a 24/10 | Capítulo 3, Proposta e Procedimentos Metodológicos |
| 25/10 a 24/11 | Capítulo 4, MVP, Projeto Mínimo Viável |

---
