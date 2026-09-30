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

✅ Capítulo 2 — Revisão da Literatura (completo)

2.1 Sistemas de rastreamento de eventos em conversão de marketing

"Sistemas web voltados à conversão de marketing dependem da capacidade de registrar, de forma estruturada, as ações realizadas pelo visitante ao longo de sua navegação. Esse registro é denominado rastreamento de eventos (event tracking, isto é, o acompanhamento de cada ação individual do usuário no site). Entre os eventos tipicamente monitorados estão os cliques em elementos da página, a profundidade de rolagem (scroll, medida de quanto da página o usuário efetivamente visualizou) e, sobretudo, o evento de conversão propriamente dito, que, no contexto de marketing digital, pode corresponder ao envio de um formulário de captação de lead (quando o visitante solicita contato ou mais informações) ou à realização de um cadastro ou inscrição, como em uma lista de e-mail marketing (newsletter). Esses eventos constituem a base de dados sobre a qual são construídas as métricas de conversão utilizadas nos testes A/B descritos na seção seguinte."

2.2 Testes A/B e o modelo de divisão estática de tráfego

"O teste A/B (A/B test, isto é, o experimento controlado que compara duas versões de um mesmo elemento) é o método consolidado para validar, com base em evidência empírica, qual entre duas ou mais variantes de uma página, por exemplo, dois formulários de captação de lead com layouts distintos, ou duas versões de uma página de inscrição, apresenta melhor taxa de conversão. No modelo tradicional, os visitantes são distribuídos entre as variantes segundo uma divisão estática de tráfego, na qual a proporção de usuários direcionados a cada versão permanece fixa (por exemplo, 50% para cada variante) durante toda a duração do experimento, independentemente dos resultados parciais observados. Segundo Kohavi, Tang e Xu (2020), autores de referência na área de experimentação online controlada, decisões baseadas em análises estatísticas repetidas ao longo do experimento figuram entre os erros mais recorrentes na prática de testes A/B, o que evidencia a rigidez, mas também a previsibilidade estatística, do modelo estático."

2.3 O dilema exploration-exploitation e os algoritmos de bandit

"Como alternativa ao modelo estático, a literatura de aprendizado por reforço (reinforcement learning, ramo do aprendizado de máquina voltado à tomada de decisões sequenciais) propõe os algoritmos de bandit (bandit algorithms; o termo deriva de one-armed bandit, expressão usada para caça-níqueis, cuja analogia representa a tarefa de descobrir, entre diversas opções de recompensa desconhecida, qual delas é a mais vantajosa, minimizando a perda durante esse processo de descoberta). Em vez de manter a divisão de tráfego fixa, esses algoritmos ajustam a alocação de visitantes em tempo real, direcionando gradualmente mais tráfego para a variante que apresenta melhor desempenho observado.

O comportamento desses algoritmos é regido pelo chamado trade-off entre exploration e exploitation (respectivamente, a exploração de variantes ainda pouco testadas, para reduzir a incerteza sobre seu desempenho real, e o aproveitamento da variante já identificada como superior, para maximizar o resultado imediato). A medida formal utilizada para quantificar a ineficiência de uma estratégia é o regret (a diferença entre o resultado que seria obtido caso a melhor variante fosse sempre escolhida desde o início, e o resultado efetivamente obtido). Um teste A/B com divisão estática apresenta regret linear ao longo do tempo, uma vez que uma fração constante do tráfego permanece direcionada a variantes inferiores durante toda a execução; algoritmos de bandit bem projetados, por sua vez, tendem a apresentar regret sublinear, reduzindo progressivamente essa perda à medida que aprendem.

Três famílias de algoritmos de bandit são especialmente relevantes para este trabalho: o Epsilon-Greedy, que direciona a variante com melhor desempenho conhecido na maior parte do tempo, reservando uma fração fixa e pequena das decisões (denominada epsilon) para a exploração aleatória das demais variantes, evitando que o algoritmo se fixe prematuramente em uma alocação subótima; o Upper Confidence Bound (UCB), que seleciona a variante a ser testada com base em um limite superior de confiança estatística sobre seu desempenho estimado, favorecendo, de forma controlada, variantes sobre as quais ainda há maior incerteza; e o Thompson Sampling, que aloca tráfego a cada variante proporcionalmente à probabilidade estimada de que ela seja a melhor opção, atualizada de forma bayesiana a cada nova observação. Segundo Russo et al. (2018), esse último método é amplamente adotado por plataformas de tecnologia de grande escala devido à sua eficiência computacional e a suas propriedades estatísticas favoráveis em termos de minimização de regret."

2.4 O peeking problem e a confiabilidade estatística das métricas de conversão

"A análise estatística clássica de um teste A/B pressupõe que o tamanho da amostra seja definido antecipadamente e que o resultado seja avaliado uma única vez, ao término do experimento. Quando essa condição não é respeitada, isto é, quando os resultados parciais são observados e uma decisão é tomada antes do encerramento planejado, configura-se o que a literatura denomina peeking problem (do inglês to peek, espiar; refere-se à prática de verificar repetidamente o resultado de um experimento antes do momento estatisticamente apropriado). Conforme demonstrado por Johari, Koomen, Pekelis e Walsh (2017), a verificação repetida dos resultados de um teste, seguida da interrupção do experimento assim que a significância estatística nominal é atingida, infla substancialmente a taxa de falsos positivos em relação ao nível de significância originalmente estabelecido.

Esse problema possui relação direta com os algoritmos de bandit descritos na seção 2.3: por definição, tais algoritmos atualizam a alocação de tráfego continuamente, com base em observações parciais, comportamento estruturalmente equivalente ao peeking. Se, por um lado, essa característica é o que permite aos algoritmos de bandit reduzir o regret e direcionar tráfego com maior eficiência para a variante de melhor desempenho, por outro, ela compromete a validade estatística tradicional das métricas de conversão coletadas, uma vez que as decisões de alocação são tomadas repetidamente sobre dados ainda incompletos. Como resposta a essa limitação, Johari, Pekelis e Walsh (2021) propõem a inferência sempre válida (always valid inference; método estatístico que permite o monitoramento contínuo dos resultados de um experimento sem inflar a taxa de erro do tipo I, ao contrário da inferência estatística clássica), cuja formulação constitui uma das principais abordagens acadêmicas para conciliar monitoramento contínuo com confiabilidade estatística."

2.5 Síntese e delimitação do problema de pesquisa

"A revisão realizada evidencia que a literatura sobre otimização dinâmica de tráfego e a literatura sobre inferência estatística válida em experimentos sequenciais têm se desenvolvido, em grande medida, de forma paralela: os trabalhos voltados a algoritmos de bandit concentram-se predominantemente na minimização do regret e na eficiência da alocação de tráfego, ao passo que os trabalhos voltados à validade estatística concentram-se em métodos de correção do peeking problem, frequentemente aplicados a testes A/B com divisão estática de tráfego. A avaliação empírica conjunta desses dois aspectos (eficiência de alocação dinâmica versus confiabilidade estatística das métricas de conversão) em um mesmo sistema de rastreamento de eventos, especialmente aplicado a cenários de conversão de marketing, permanece pouco explorada, o que evidencia a lacuna de pesquisa que este trabalho busca investigar."

✅ Referências (Capítulo 2)

JOHARI, Ramesh; KOOMEN, Pete; PEKELIS, Leonid; WALSH, David. Peeking at A/B Tests: Why it matters, and what to do about it. In: ACM SIGKDD INTERNATIONAL CONFERENCE ON KNOWLEDGE DISCOVERY AND DATA MINING, 23., 2017, Halifax. Anais [...]. New York: ACM, 2017. p. 1517-1525.

JOHARI, Ramesh; PEKELIS, Leo; WALSH, David J. Always Valid Inference: Continuous Monitoring of A/B Tests. Operations Research, v. 70, n. 3, 2021.

KOHAVI, Ron; TANG, Diane; XU, Ya. Trustworthy Online Controlled Experiments: A Practical Guide to A/B Testing. Cambridge: Cambridge University Press, 2020.

RUSSO, Daniel J.; VAN ROY, Benjamin; KAZEROUNI, Abbas; OSBAND, Ian; WEN, Zheng. A Tutorial on Thompson Sampling. Foundations and Trends in Machine Learning, v. 11, n. 1, p. 1-96, 2018.

---

✅ Cronograma e Plano de Ação (3.5)

| Período | Atividade |
|---|---|
| 01/08 a 01/09 | Capítulo 1, Definição do Projeto |
| 02/09 a 29/09 | Capítulo 2, Revisão da Literatura |
| 30/09 a 24/10 | Capítulo 3, Proposta e Procedimentos Metodológicos |
| 25/10 a 24/11 | Capítulo 4, MVP, Projeto Mínimo Viável |

---



