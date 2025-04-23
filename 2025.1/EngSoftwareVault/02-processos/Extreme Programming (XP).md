"Segundo seu autor, XP é um método leve recomendado para desenvolver
software com requisitos vagos ou sujeitos a mudanças."

"XP — como outros métodos ágeis — recomenda o envolvimento dos
clientes com o projeto"

- Possui todas as características de um método ágil  (checar [[Manifesto Ágil]])
- Não prescritivo (não define um passo a passo)
- Definido por meio de um conjunto de valores, princípios e práticas de desenvolvimento
	- Valores: Comunicação, simplicidade, feedback, coragem, respeito e qualidade de vida
	- Princípios: Humanidade, economicidade, benefícios mútuos, melhorias contínuas, falhas acontecem, baby steps e responsabilidade pessoal
	- Práticas: 
		- Práticas sobre o Processo de Desenvolvimento: representante dos clientes, histórias dos usuários, iterações, releases, planejamento de releases, planejamento de iterações, planning poker, slack
		- Práticas de programação: design incremental, programação pareada, desenvolvimento dirigido por testes (TDD), build automatizado, integração contínua
		- Práticas de gerenciamento de projetos: Métricas, ambiente de trabalho, contratos com escopo aberto

#### Valores 
XP defende que o desenvolvimento de projetos de software seja norteado
por três valores principais: comunicação, simplicidade e feedback. Na
verdade, argumenta-se que esses valores são universais, para convívio
humano. Ou seja, eles não servem apenas para guiar projetos de
desenvolvimento, mas a própria vida em sociedade. Uma boa comunicação
é importante em qualquer projeto, não apenas para evitar, mas também para
aprender com erros. O segundo valor de XP é simplicidade, pois em todo
sistema complexo e desafiador existem sistemas ou subsistemas mais
simples, que às vezes não são considerados. Por último, existem riscos em
todos os projetos de software: os requisitos mudam, a tecnologia muda, a
equipe de desenvolvimento muda, o mundo muda, etc. Um valor que ajuda a
controlar tais riscos é estar aberto ao feedback dos stakeholders, a fim de
que correções de rota sejam implementadas o quanto antes. Em outras
palavras, é difícil desenvolver o sistema de software certo em uma primeira
e única tentativa. Frederick Brooks tem uma frase conhecida sobre esse
fenômeno:
Planeje-se para jogar fora partes de seu sistema, pois você fará isso.
Por isso, feedback é um valor essencial para garantir que as partes ou
versões que serão descartadas sejam identificadas o quanto antes, de forma a
diminuir prejuízos e retrabalho. Além dos três valores mencionados, XP
também defende outros valores, como coragem, respeito e qualidade de
vida

#### Princípios
- Ponte entre práticas e valores
	Humanidade: O principal recurso de uma empresa de software são seus colaboradores, "peopleware". A gestão de pessoas é fundamental para o sucesso de projetos de sotware
	
	Economicidade: Software não é uma obra de arte, mas algo que tem que gerar resultados econômicos, como defendido por esse princípio de XP.

	Benefícios mútuos: As decisões de projeto devem beneficiar múltiplos stakeholders. "Todo negócio tem que ser bom para os dois lados".

	Melhorias contínuas: Design e implementações devem ser incrementais e melhorar o sistema cada iteração. Inclusive, as próprias práticas de sistema devem ser aprimoradas, o time deve reservar tempo para refletir sobre estas.

	Baby steps: Um progresso testado, validado e seguro é preferível a grandes implementações com riscos de serem descartadas, o mesmo vale para testes, integração de código e refatorações.

	Responsabilidade pessoal: Desenvolvedores devem ter uma ideia clara de eu papel e responsabilidade na equipe.


#### Práticas sobre o processo de desenvolvimento
O representante dos clientes deve entender do domínio do sistema que será construído e tem como uma de suas funções o papel de escrever as [[Histórias de Usuário]]
#### Práticas de programação
- Design incremental
- Programação em pares: toda tarefa de codificação deve ser realizada por dois devs, um líder (driver) e um navegador 
	- Melhor qualidade do código e design
	- Disseminar conhecimento
	- Treinamento de desenvolvedores menos experientes

	- Maior custo econômico
	- Falta de confortabilidade -> XP tenta evitar isso com a alternância de funções entre os devs
- Propriedade coletiva do código: Qualquer dev pode modificar qualquer parte do código, seja para implementar novas features, corrigir bugs ou aplicar refactorings.
- Testes automatizados: Implementação de programas para executar pequenas unidades de um sistema e verificar as saídas produzidas. (Checar [[07-testes]])
- Desenvolvimento dirigido por testes (TDD): test-first programming
	- Evita que a escrita de testes seja sempre deixada para amanhã, pois são a primeira coisa a ser implementada.
	- ao escrever um teste, o dev se coloca no papel de cliente 
- Build automatizado: Geração de uma versão de um sistema que seja executável e possa ser posta em produção de forma automatizada. O processo de build deve ser o mais rápido possível, com limite de 10 minutos (no entanto, a depender das características do sistema, pode ser que seja difícil que esse limite seja atendido.).
- Integração contínua: Apoio de sistemas de controle de versões (como o git). Desenvolvedores devem integrar seu código sempre, se possível todos os dias com o intuito de diminuir chances e o tamanho/complexidade dos conflitos.
#### Práticas de gerenciamento de projetos
- Ambiente de trabalho: 
	- Times pequenos, com menos de 10 devs.
	- Todos dedicados ao projeto, sem times fracionados.
	- Trabalhem na mesma sala, facilitando comunicação e feedback.
	- Espaço de trabalho deve ser informativo, com cartazes mostrando as histórias da iteração e seus estados.
	- Jornadas de trabalho sustentáveis (40h max)
- Contratos com escopo aberto:
	- Requisitos são mutáveis
	- Pagamento por hora trabalhada
	- Colaboração com o cliente
- Métricas de processo: A XP recomenda duas métricas principais
	- Número de bugs (Poucos por ano)
	- intervalo de tempo entre o início e do desenvolvimento  e o momento em que o projeto começa a gerar os seus primeiros resultados financeiros.