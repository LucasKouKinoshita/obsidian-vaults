#### 1º Definição
Arquitetura preocupa-se com projeto em mais alto nível. Ou seja, o foco deixa de ser a organização e interfaces de classes individuais e passa a ser em unidades de maior tamanho, sejam elas pacotes, componentes, módulos, subsistemas, camadas ou serviços — o nome não importa tanto neste primeiro momento. De forma genérica, os termos que acabamos de mencionar devem ser entendidos como conjuntos de classes relacionadas.

#### Componentes arquiteturais
- Devem ser relevantes para que um sistema atenda a seus objetivos.
	- Modulo de persistência que faz interface com o BD de um sistema de informações. -> Componente arquitetural
	- Modulo de persistência de um sistema de IA para diagnosticar doenças que armazena dados de doenças diagnosticadas -> Simples e não relevante para o objetivo principal do sistema -> não faz parte de sua arquitetura.


#### 2º Definição
Arquitetura não é apenas um conjunto de módulos, mas um conjunto de decisões. É verdade que dentre essas decisões, inclui-se a definição dos módulos principais de um sistema. Mas outras decisões também são contempladas, como a escolha da linguagem de programação e do banco de dados que serão usados no desenvolvimento.
Decisões importantes que, uma vez tomadas, dificilmente poderão ser revertidas futuramente.


#### Aprofundamento
Alguns autores — como Taylor et al. (link) — fazem uma distinção entre padrões e estilos arquiteturais. Segundo eles, padrões focam em soluções para problemas específicos de arquitetura; enquanto estilos arquiteturais propõem que os módulos de um sistema devem ser organizados de uma determinado modo, o que não necessariamente ocorre visando resolver um problema específico.
- [[Arquitetura MVC]] é um padrão arquitetural que resolve o problema de separar apresentação e modelo em sistemas de interface gráficas, mas por outro lado, [[Pipes e filtros]] constituem um estilo arquitetural.
