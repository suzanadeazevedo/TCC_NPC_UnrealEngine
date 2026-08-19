# Sistema de inteligência artificial para personagens não jogáveis utilizando Behavior Trees na Unreal Engine


## Introdução

Este trabalho desenvolveu e analisou um sistema básico de inteligência artificial para personagens não jogáveis (NPCs), utilizando árvores de comportamento na Unreal Engine e avaliou sua aderência às boas práticas de engenharia de software, comparada a máquina de estados finitos, outra técnica tradicionalmente utilizada para o controle de comportamento em jogos.

### Contextualização:

Non-Playable Characters [NPCs] são os personagens que não são controlados pelo jogador, torna a experiência mais imersiva, interativa e desafiadora (Rogers, 2013).

Para que os NPCs funcionem de forma autônoma e reativa é necessário que seja desenvolvido um sistema de inteligência artificial

A Unreal Engine dispõe uma ferramenta chamada Behavior Trees [BT] para criar inteligência artificial para personagens não jogáveis, baseada em árvores de comportamento.

Outra técnica de para a criação de IA muito popular é a Finite State Machine [FSM]. (Bourg e Seemann 2004).

### Problema:

Investigar abordagens que permitam estruturar a IA de uma maneira profissional e alinhada às boas práticas de engenharia de software

### Objetivo:

Desenvolver e analisar uma IA para NPCs na Unreal Engine através do sistema de Behavior Trees avaliando sua aplicação e sua aderência às boas práticas de engenharia de software




## Material e Método


### Pesquisa:
Aplicada, de natureza quantitativa e exploratória

### Metodologia:

Mapeamento da literatura, com o intuito de identificar trabalhados relacionados ao uso de árvores de comportamento, máquinas de estados finitos, inteligência artificial.

Levantamento e análise de requisitos

Modelagem e Implementação da Inteligência Artificial

Desenvolvimento do Protótipo




## Levantamento e Análise de Requisitos

### Requisitos Funcionais:

Estão relacionados às ações que o NPC deve ser capaz de executar no ambiente do jogo

- O NPC deve patrulhar o cenário.

- O NPC deve detectar o jogador por meio do sistema de percepção.

- Ao detectar o jogador, o NPC deve iniciar uma perseguição.

- Caso perca o alvo, o NPC deve retornar à patrulha.

### Requisitos Não Funcionais:

Estão associados à qualidade e organização da solução

- A IA baseada em árvores de comportamento deve ser implementada utilizando a funcionalidade Behavior Trees.

- A solução deve seguir boas práticas de modularidade e baixo acoplamento.

- O sistema deve permitir fácil manutenção e extensão.

- A navegação deve utilizar NavMesh da Unreal Engine.




## Modelagem e Implementação da Inteligência Artificial

### Diagrama de Atividades:

![DiagramaAtividade](https://github.com/suzanadeazevedo/TCC_NPC_UnrealEngine/blob/main/TCC_BT%20-%20REVISADO%20-%20Projeto%20Base/img/Diagrama%20de%20Atividade.png)

### Diagrama de Classes:

![DiagramaClasses](https://github.com/suzanadeazevedo/TCC_NPC_UnrealEngine/blob/main/TCC_BT%20-%20REVISADO%20-%20Projeto%20Base/img/UML%20CLASSES.png)


## Testes e Resultados
Siglas:
- NPC BT: NPC Behavior Tree, modelo baseado em arvores de comportamento.
- NPC FSM: NPC Finite State Machine, modelo baseado em maquina de estados finitos.
- DP: Desvio Padrão.

### Teste Um:
Eficiência de detecção do jogador: Métrica → Tempo médio de detecção; 

.      | NPC BT| NPC FSM
------ | ------| -------
Média  |46,1s  |29,0s
DP     |35,6   |35,9

O modelo baseado em máquina de estados finitos apresentou menor tempo médio para detecção do jogador em comparação ao modelo em árvore de comportamento, nas condições avaliadas, ambos os modelos apresentaram desvios-padrão semelhantes.


### Teste Dois:

Taxa de sucesso na detecção do jogador: Métrica → Taxa de sucesso.

.          | NPC BT| NPC FSM
------     | ------| -------
Sucessos   |4      |8
Falhas     |6      |2

O NPC FSM obteve melhor desempenho no teste de busca do jogador. Esse comportamento é coerente com os resultados observados no Teste Um (Eficiência de Detecção).

### Teste Três:

Eficácia em Perseguição: Métrica → Taxa de sucesso em perseguições

Sucesso em Alcancce (%)    | NPC BT| NPC FSM
------                     | ------| -------
Média                      |57     |22,8
DP                         |19,8   |22,1

Alcances por Execução      | NPC BT| NPC FSM
------                     | ------| -------
Média                      |2,70   |0,7
DP                         |0,67   |0,67

Fugas por Execução         | NPC BT| NPC FSM
------                     | ------| -------
Média                      |2,30   |2,20
DP                         |1,25   |0,92

A análise dos resultados do terceiro teste, Tabela 4, observou-se que o modelo o NPC BT apresentou desempenho superior ao NPC FSM. Esse resultado indica que, nas condições avaliadas, o NPC controlado por arvore de comportamento conseguiu alcançar o jogador com maior frequência durante as perseguições. Essa diferença também é observada na média de alcances por execução, evidenciando maior efetividade do modelo BT em concluir a perseguição com sucesso. Além disso, o desvio-padrão da taxa de sucesso foi ligeiramente inferior no NPC BT comparação ao NPC FSM, indicando comportamento um pouco mais consistente entre as execuções.

Em relação às fugas por execução, ambos os modelos apresentaram médias semelhantes, apontando frequência equivalente de eventos de fuga ao longo dos testes. Entretanto, o NPC FSM apresentou menor desvio-padrão em comparação ao NPC BT, sugerindo menor variação entre as execuções. Apesar dessa diferença na dispersão, as médias muito próximas indicam que ambos os modelos produziram quantidade semelhante de eventos de fuga.

Comparando os resultados deste teste com os obtidos nos experimentos anteriores, observa-se um comportamento complementar entre as arquiteturas. Enquanto o NPC FSM apresentou melhor desempenho na localização inicial do jogador, conforme observado nos testes de detecção e busca, o NPC BT demonstrou maior eficiência na etapa de perseguição, obtendo um número maior de alcances e maior taxa de sucesso. Esses resultados revelam que o desempenho das arquiteturas varia conforme a tarefa desempenhada, não sendo possível afirmar que uma abordagem seja superior em todos os aspectos avaliados.

### Teste Quatro:

Desempenho: Métrica → Quantidade de frames por segundo [FPS], tempo de frame em milissegundos [ms], tempo de renderização do Graphics Processing Unit [GPU] em ms e uso de memória.
O teste foi realizado com 1,5 e 10 NPCs ativos. 

#### **Um NPC ativo**:

NPC BT                     | FPS   | Frame(ms)| GPU(ms)| Memória(GB)   
------                     | ------|   -------| -------|    -------
Média                      |79,3   |12,55     |9,39    |1,69
DP                         |2,66   |0,24      |0,52    |0,02

NPC FSM                    | FPS   | Frame(ms)| GPU(ms)| Memória(GB)
------                     | ------|   -------| -------|    -------
Média                      |65,3   |14,75     |10,27   |2,39
DP                         |7,39   |1,25      |1,74    |0,08


Além das diferenças nas médias, o NPC BT apresentou menores desvios-padrão em todas as métricas analisadas. Esses resultados indicam que o desempenho da arvore de comportamento permaneceu mais estável ao longo das dez execuções, ao passo que a máquina de estados finito apresentou maior variabilidade. Considerando conjuntamente FPS, tempo de quadro, tempo de GPU e consumo de memória, observa-se que, nas condições avaliadas e com apenas um NPC ativo, o modelo baseado em árvore de comportamento apresentou melhor desempenho computacional e maior estabilidade de execução quando comparado ao modelo baseado em máquina de estados finitos.



#### **Cinco NPCs ativos**:

NPC BT                     | FPS   | Frame(ms)| GPU(ms)| Memória(GB)   
------                     | ------|   -------| -------|    -------
Média                      |79,7   |12,59     |9,06    |1,63
DP                         |3,30   |0,32      |0,99    |0,03

NPC FSM                    | FPS   | Frame(ms)| GPU(ms)| Memória(GB)
------                     | ------|   -------| -------|    -------
Média                      |65,6   |14,94     |9,36    |2,17
DP                         |4,30   |0,81      |1,32    |0,02

O NPC BT apresentou maior taxa média de quadros por segundo, menor tempo de processamento por quadro, menor tempo médio de processamento na GPU e menor consumo de memória. Os desvios-padrão indicam que o modelo em arvore de comportamento também apresentou maior estabilidade nas métricas de FPS, tempo de quadro e processamento da GPU ao longo das execuções. Apenas no consumo de memória o modelo em máquina de estados finitos apresentou dispersão ligeiramente menor, diferença que se mostrou pouco significativa diante da pequena variação observada entre ambos. Esses resultados apontam que, mesmo com o aumento da quantidade de agentes simultâneos, o modelo baseado em árvore de comportamento manteve menor custo computacional e comportamento mais estável durante a execução.


#### **Dez NPCs ativos**:

NPC BT                     | FPS   | Frame(ms)| GPU(ms)| Memória(GB)   
------                     | ------|   -------| -------|    -------
Média                      |72,6   |13,73     |10,34   |1,56
DP                         |4,14   |0,76      |1,72    |0,03

NPC FSM                    | FPS   | Frame(ms)| GPU(ms)| Memória(GB)
------                     | ------|   -------| -------|    -------
Média                      |67,0   |14,69     |8,51    |2,62
DP                         |5,09   |0,88      |0,94    |0,50

Ambos os modelos apresentaram redução na taxa média de quadros por segundo em relação aos cenários anteriores, comportamento esperado em função do aumento da carga computacional. Ainda assim, o NPC BT manteve maior média de FPS e menor tempo médio por quadro, indicando melhor desempenho geral durante a execução. Em relação ao consumo de memória, o BT permaneceu utilizando menos recursos do que o NPC FSM, mantendo também menor variabilidade entre as execuções.

Diferentemente dos cenários anteriores, o modelo em máquina de estados finitos apresentou menor tempo médio de processamento na GPU, além de menor desvio-padrão nessa métrica. Esse resultado sugere que, com maior quantidade de agentes simultâneos, parte do processamento gráfico associado ao modelo em máquina de estados finitos tornou-se relativamente mais eficiente. Entretanto, essa vantagem não foi suficiente para superar o desempenho geral do BT nas demais métricas analisadas.




### Teste Cinco:

Boas práticas em engenharia de software: Métrica → Atendimento a critérios; modularidade, modificabilidade, escalabilidade

Critério                   | Não Atende (0)   | Atende Parcialmente (1)| Atende Totalmente(2)   
------                     | ------           |   -------              | -------
Modularidade               |Lógica concentrada e fortemente acoplada  |Há alguma separação, mas parte relevante da lógica permanece concentrada                                                           |Comportamentos distribuídos em componentes independentes e com responsabilidades definidas    
Modificabilidade           |Alteração exige mudanças amplas e interdependentes   | Alteração exige modificações em mais de um componente| Alteração localizada, com baixo impacto sobre componentes existentes
Escalabilidade             |Inclusão de comportamentos aumenta significativamente a complexidade estrutural | Novos comportamentos podem ser adicionados, mas exigem alterações estruturais relevantes| Novos comportamentos podem ser incorporados sem reestruturação significativa
Reutilização               |Componentes dependem diretamente da implementação específica |Alguns componentes podem ser reaproveitados com adaptações |Componentes podem ser reutilizados em diferentes comportamentos/personagens
Organizaação               |Lógica concentrada, com baixa separação visual/funcional |Há separação parcial das responsabilidades |Responsabilidades claramente separadas e estrutura facilmente identificável


 #### **Avaliação**:

Critérios           | Arvore de Comportamento (BT)| Maquina de Estados Finitos (FSM)
------              | ------                      | -------
Modularidade        |2                            |1
Modificabilidade    |1                            |1
Escalabilidade      |2                            |0
Reutilização        |2                            |2 
Organização         |2                            |0
**Pontuação**       |9                            |4   

Em relação a avaliação de boas práticas em engenharia de software, foi possível concluir:

*   Modularidade: a árvore de comportamento apresentou maior modularidade, uma vez que suas decisões estão distribuídas em arquivos independentes, permitindo isolamento funcional e menor acoplamento entre comportamentos. Estruturalmente, cada comportamento ocupa seu próprio artefato, resultando em 5 arquivos com responsabilidade única cada. Na FSM, embora o código seja separado por estado, a lógica se concentra em fluxos condicionais dentro de um único Blueprint com aproximadamente 21 nós, reduzindo a flexibilidade modular. 

*	Modificabilidade: ambas as abordagens receberam pontuação equivalente nesse critério, pois a alteração exige modificações estruturais em componentes já existentes ou a criação e integração de novos componentes. A avaliação considerou o impacto estrutural necessário para modificar o comportamento existente ou adicionar um novo comportamento. Na arvore de comportamento, a inclusão de um novo comportamento exige a criação de uma nova tarefa ou serviço e sua inserção na árvore, enquanto na máquina de estados finitos é necessário incluir o novo estado no Enum e modificar a lógica responsável pela criação e tratamento dos estados que esta totalmente concentrada no Blueprint AI Controller.  Além disso, a necessidade de alterações diretas no código para modificação do comportamento pode impactar negativamente o fluxo de desenvolvimento, especialmente em projetos de maior escala.

*	Escalabilidade: a árvore de comportamento demonstrou ser vantajosa nesse quesito, permitindo adição de novos comportamentos por meio de subárvores sem necessidade de reestruturação significativa do sistema. Dessa forma, o crescimento funcional do sistema pode ocorrer pela adição ou combinação de componentes, reduzindo a necessidade de alterações nos componentes existentes. Essa característica é particularmente relevante à medida que a quantidade e a complexidade dos comportamentos dos NPCs aumentam. Em uma arquitetura modular, o acréscimo de funcionalidades tende a ocorrer pela composição de componentes existentes e pela criação de novos componentes, em vez da expansão contínua de um único bloco de lógica. Essa relação entre modularidade e capacidade de evolução está alinhada aos princípios de engenharia de software apresentados por Pressman (2016), que destaca a importância da modularidade e da organização das responsabilidades para o desenvolvimento de sistemas que possam ser modificados e evoluídos ao longo de seu ciclo de vida. Na máquina de estados finitos a inclusão de novos comportamentos expande o código no mesmo arquivo, exigindo blocos de comentários para identificar cada grupo de nós; o crescimento rápido aumenta a complexidade do grafo de estados, impactando diretamente a legibilidade do Blueprint. Ressalta-se que essa conclusão está relacionada à arquitetura implementada neste trabalho e não implica que árvores de comportamento sejam universalmente superiores às máquinas de estados finitos em termos de escalabilidade. A vantagem observada decorre principalmente da forma como as responsabilidades foram distribuídas e dos mecanismos de composição utilizados na implementação analisada.

*	Reutilização: ambas as abordagens apresentaram capacidade de reutilização de componentes, atendendo ao princípio de reutilização de componentes e por isso receberam pontuação equivalente nesse critério embora por mecanismos arquiteturais distintos. Na implementação baseada em máquina de estado finito, o AI Controller permite que a mesma implementação seja associada a diferentes personagens sem necessidade de duplicação da lógica. Variações de comportamento podem ser obtidas por meio da parametrização do controlador ou, quando necessário, pela especialização de sua classe. Na Behavior Tree, a reutilização ocorre principalmente por meio de tarefas e serviços independentes, que podem ser empregados em diferentes árvores e personagens. De acordo com Millington (2019), o comportamento definido em árvore de comportamento pode ser reutilizado por diferentes personagens, uma vez que essas estruturas permitem a composição e instanciamento de comportamentos a partir de tarefas previamente definidas.

*	Organização: a árvore de comportamento apresentou maior organização estrutural devido à separação explícita entre os componentes responsáveis pela tomada de decisão e aqueles responsáveis pela execução dos comportamentos. Essa organização está relacionada ao princípio de separação de responsabilidades, pois diferentes elementos possuem funções específicas dentro da arquitetura. Na FSM analisada, maior parte da lógica está concentrada no Blueprint AI Controller, resultando em um grafo mais extenso e visualmente mais denso à medida que novos comportamentos são incorporados.


Apesar das vantagens observadas na abordagem baseada em árvore de comportamento relacionadas aos princípios de engenharia de software, a máquina de estados finitos ainda se mostra adequada para cenários mais simples, onde o número de estados e transições é limitado, como comportamento simples e pouco vaiáveis. Nesses casos, sua implementação direta pode resultar em soluções mais rápidas e com menor sobrecarga estrutural.

É importante destacar que os testes foram realizados em ambiente controlado, com número limitado de execuções e cenário simplificado. Dessa forma, os resultados não de-vem ser generalizados para todos os contextos de desenvolvimento de jogos, mas servem como evidência inicial comparativa entre as abordagens analisadas.

## Considerações Finais

Após o desenvolvimento e análise do prototipo foi possível avaliar que é possível criar inteligência artificial para personagens não jogáveis [NPC] utilizando boas práticas de engenharia de software. Como visto nesse trabalho a abordagem baseada em árvore de comportamento é compatível a essa proposta e a Unreal Engine oferece uma boa ferramenta que permite a criação e execução dessa arquitetura de forma modular, flexível e escalável.

Comparando a árvore de comportamento e a máquina de estados finitos é possível concluir que ambas as abordagens atingiram os objetivos dos testes de funcionalidade, tendo comportamentos de patrulha e perseguição efetivos. Isso reforça o que já é apresentado na literatura, que a escolha da técnica a ser realizada depende do contexto e objetivos do projeto a quais serão aplicadas.

Como limitação, ressalta-se que os testes foram conduzidos em ambiente controlado, com dois comportamentos básicos e cenário simplificado, o que restringe a generalização dos resultados. 

Para trabalhos futuros, recomenda-se a expansão do protótipo com comportamentos adicionais, como ataque e recebimento de dano, bem como a realização de testes em cenários mais complexos e com maior número de execuções, a fim de ampliar a validade dos resultados obtidos. Adicionalmente, sugere-se a inclusão de outros modelos de inteligência artificial para uma comparação mais abrangente.


## Referencias Bibliograficas Utilizada no Projeto:

_ANDRADE, M. M. de. 2012. Introdução à metodologia do trabalho científico: elaboração de trabalhos na graduação, 10ª edição. Rio de Janeiro: Atlas. E-book. p.112. ISBN 9788522478392. Disponível em: https://app.minhabiblioteca.com.br/reader/books/ 9788522478392/. Acesso em: 07 fev. 2026.

‌BOURG, D. M.; SEEMANN, G.  2004. AI for game developers. Beijing; Cambridge: O’reilly

EPIC GAMES. 2025.Unreal Engine 5. Disponível em: <https://www.unrealengine.com/pt-BR/ unreal-engine-5 >. Acesso em: 23 out. 2025. 

FERREIRA, J. V. P; KISHIMOTO. 2024 A. Aplicação de Behavior Tree para IA de NPCs inimigos em jogos de survival horror. Trabalho de Conclusão de Curso. Faculdade de Com-putação e Informática, Universidade Presbiteriana Mackenzie, São Paulo, SP, Brasil. Disponível em: https://dspace.mackenzie.br/items/8ebf626d-9ddc-4ea4-8796-5137c4b334e0 Acesso em: 03 jan. 2026.

MILLINGTON, I. 2019. Artificial Intelligence for Games. 3ed. CRC Press, Reino Unido.

INTERNATIONAL ORGANIZATION FOR STANDARDIZATION.  2023. ISO/IEC 25010:2023: Systems and software engineering — Systems and Software Quality Requirements and Evaluation (SQuaRE) — Product quality model. Geneva: ISO. Disponível em: https://www.iso.org/standard/78176.html  Acesso em: 10 mar  2026

MACCORMACK, A.; STURTEVANT, D. J. 2016. Technical debt and system architecture. In: Journal of Systems and Software. 2016. Boston, Miami, Estados Unidos. v. 120, p. 257–273. Disponível em: https://www.hbs.edu/ris/Publication%20Files/2016-JSS%20Technical%20Debt_d793c712-5160-4aa9-8761-781b444cc75f.pdf Acesso em: 10 mar 2026

MIZUTANI, W. K.; DAROS, V. K.; KON, F. 2021. Software architecture for digital game mechanics: a systematic literature review. In: Entertainment Computing, v. 38, 100421, 2021. Disponível em: https://doi.org/10.1016/j.entcom.100421. Acesso em: 10 mar  2026

PREMOLI , Breno de Oliveira; SILVA , Victor Amaral. 2024. Estudo sobre o comportamento de npcs e inimigos em jogos digitais utilizando a inteligência artificial. Trabalho de Conclusão de Curso em Tecnólogo em Análise e Desenvolvimento de Sistemas. Faculdade de Tecnologia de Presidente Prudente, Presidente Prudente, SP. Brasil
Disponivel em: https://ric.cps.sp.gov.br/handle/123456789/23495. Acesso em: 03 jan. 2026

PRESSMAN, R. S. 2016. Engenharia de Software: Uma Abordagem Profissional. McGraw Hill, Porto Alegre, PR, Brasil.

ROGERS, S. 2013. Level Up Um Guia Para O Design De Grandes Jogos. Blucher, São Paulo, SP, Brasil.

ZHANG, J. 2025 Implementation and Research of Artificial Intelligence Characters Based on Unreal Engine 5. Asia-Europe Conference on Cybersecurity, Internet of Things and Soft Computing (CITSC), Rimini, Italy, 2025. p. 73-77.  Disponível em: https://ieeexplore.ieee.org/document/10936510. Acesso em: 03 jan. 2026.

VALADARES, Gabriel Pacini O.; RIBEIRO, Marcos Wagner S.. Técnicas de Inteligência Artificial na Criação de Personagens Não Jogáveis: uma Revisão de Literatura. In: TRILHA DE ARTES & DESIGN – ARTIGOS COMPLETOS - SIMPÓSIO BRASILEIRO DE JOGOS E ENTRETENIMENTO DIGITAL (SBGAMES), 21. , 2022, Natal/RN. Anais [...]. Porto Alegre: Sociedade Brasileira de Computação, 2022 . p. 208-217. Disponivel em: https://doi.org/10.5753/sbgames_estendido.2022.226106. Acesso em: 03 jan. 2026

## Anexo:

Os personagens utilizados neste projeto foram criados pelo Kenney.

Disponível em:
 
https://kenney.nl/assets/animated-characters-survivors. Acesso em: 20 dez. 2025.

https://kenney.nl/assets/animated-characters-retro. Acesso em: 01 jul. 2026.

As animações dos personagens foram feitas através do Mixamo.

Disponível em:

https://www.mixamo.com/#/. Acesso em: 20 dez. 2025.

