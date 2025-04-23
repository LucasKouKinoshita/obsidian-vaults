# Capítulo 5: Princípios de Projeto de Software

## Introdução

Este capítulo discute os princípios e propriedades fundamentais que orientam o projeto de software de qualidade. O projeto de software é a atividade de definir a arquitetura, componentes, interfaces e outras características de um sistema para satisfazer requisitos específicos. Bons princípios de projeto levam a sistemas mais flexíveis, manuteníveis e extensíveis, reduzindo o custo total de propriedade ao longo do ciclo de vida do software. Serão abordados conceitos essenciais como coesão e acoplamento, além dos princípios SOLID, que constituem a base para o desenvolvimento de software orientado a objetos bem estruturado. Compreender e aplicar esses princípios é crucial para criar sistemas que possam evoluir com as mudanças de requisitos e tecnologias.

## Conhecimentos Principais

### [[Coesão e Acoplamento]]
Princípios fundamentais que medem a qualidade de um projeto: alta coesão (foco em uma única responsabilidade) e baixo acoplamento (minimização de dependências).

### [[Princípio da Responsabilidade Única (SRP)]]
Primeiro princípio SOLID: uma classe deve ter apenas uma razão para mudar, ou seja, deve ter apenas uma responsabilidade.

### [[Princípio Aberto/Fechado (OCP)]]
Segundo princípio SOLID: entidades de software devem estar abertas para extensão, mas fechadas para modificação.

### [[Princípio da Substituição de Liskov (LSP)]]
Terceiro princípio SOLID: objetos de uma classe derivada devem poder substituir objetos da classe base sem afetar a corretude do programa.

### [[Princípio da Segregação de Interfaces (ISP)]]
Quarto princípio SOLID: clientes não devem ser forçados a depender de interfaces que não utilizam.

### [[Princípio da Inversão de Dependência (DIP)]]
Quinto princípio SOLID: módulos de alto nível não devem depender de módulos de baixo nível; ambos devem depender de abstrações.

### [[Encapsulamento]]
Princípio de esconder os detalhes internos de implementação e expor apenas o necessário através de interfaces bem definidas.

### [[Abstração]]
Processo de identificar aspectos essenciais de uma entidade e ignorar propriedades acidentais, reduzindo a complexidade.

### [[Modularidade]]
Divisão de um sistema em módulos independentes que podem ser desenvolvidos, testados e mantidos separadamente.

### [[Lei de Demeter]]
Princípio de "fale apenas com seus amigos imediatos", limitando o conhecimento que um objeto tem sobre a estrutura interna de outros objetos. 