# Sistema de inteligência artificial para personagens não jogáveis utilizando Behavior Trees na Unreal Engine


## Introdução

Este trabalho desenvolveu e analisou um sistema básico de inteligência artificial para perso-nagens não jogáveis (NPCs), utilizando árvores de comportamento na Unreal Engine e ava-liou sua aderência às boas práticas de engenharia de software, comparada a máquina de estados finitos, outra técnica tradicionalmente utilizada para o controle de comportamento em jogos.

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

![Diagrama_Atividades]("")

