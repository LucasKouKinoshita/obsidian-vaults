# Capítulo 5: Princípios de Projeto de Software

## Introdução

Este capítulo discute os princípios e propriedades fundamentais que orientam o projeto de software de qualidade. O projeto de software é a atividade de definir a arquitetura, componentes, interfaces e outras características de um sistema para satisfazer requisitos específicos. Bons princípios de projeto levam a sistemas mais flexíveis, manuteníveis e extensíveis, reduzindo o custo total de propriedade ao longo do ciclo de vida do software. Serão abordados conceitos essenciais como coesão e acoplamento, além dos princípios SOLID, que constituem a base para o desenvolvimento de software orientado a objetos bem estruturado. Compreender e aplicar esses princípios é crucial para criar sistemas que possam evoluir com as mudanças de requisitos e tecnologias.

- Combater complexidade que caracteriza sistemas modernos
- Dividir para conquistar
- Abstração (representação simplificada de uma entidade)
## Conhecimentos Principais

## Propriedades de projeto
### [[Abstração]]
Processo de identificar aspectos essenciais de uma entidade e ignorar propriedades acidentais, reduzindo a complexidade.
### [[Integridade Conceitual]]

### [[Ocultamento de informação]]

### [[Getters e Setters]]

### [[Coesão e Acoplamento]]
Princípios fundamentais que medem a qualidade de um projeto: alta coesão (foco em uma única responsabilidade) e baixo acoplamento (minimização de dependências).
## Princípios de projeto
### [[Princípio da Responsabilidade Única (SRP)]] - Single Responsibility Principle
Primeiro princípio SOLID: uma classe deve ter apenas uma razão para mudar, ou seja, deve ter apenas uma responsabilidade.

### [[Aberto - Fechado (OCP)]] - Open Closed/Principle
Segundo princípio SOLID: entidades de software devem estar abertas para extensão, mas fechadas para modificação.

### [[Princípio da Substituição de Liskov (LSP)]] - Liskov Substitution Principle
Terceiro princípio SOLID: objetos de uma classe derivada devem poder substituir objetos da classe base sem afetar a corretude do programa.

### [[Princípio da Segregação de Interfaces (ISP)]] - Interface Segregation Principle
Quarto princípio SOLID: clientes não devem ser forçados a depender de interfaces que não utilizam.

### [[Princípio da Inversão de Dependência (DIP)]] - Dependency Inversion Principle
Quinto princípio SOLID: módulos de alto nível não devem depender de módulos de baixo nível; ambos devem depender de abstrações.
### [[Prefira Composição a Herança]]

### [[Lei de Demeter]]
Princípio de "fale apenas com seus amigos imediatos", limitando o conhecimento que um objeto tem sobre a estrutura interna de outros objetos. 