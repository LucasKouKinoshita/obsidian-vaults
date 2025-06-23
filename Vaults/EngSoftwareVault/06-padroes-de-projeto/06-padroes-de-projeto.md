# Capítulo 6: Padrões de Projeto

## Introdução

Este capítulo explora os padrões de projeto GoF (Gang of Four) e sua aplicação na resolução de problemas comuns de design de software. Os padrões de projeto são soluções testadas e comprovadas para problemas recorrentes no desenvolvimento de software, representando as melhores práticas acumuladas por desenvolvedores experientes ao longo do tempo. Eles fornecem um vocabulário comum que facilita a comunicação entre desenvolvedores e promovem a reutilização de arquiteturas bem-sucedidas. Ao estudar e aplicar esses padrões, os engenheiros de software podem evitar "reinventar a roda" e aproveitar soluções elegantes que já foram refinadas pela comunidade. Este capítulo apresenta os principais padrões de projeto, suas categorias, estruturas e contextos de aplicação.

## Conhecimentos Principais

### [[Introdução aos Padrões de Projeto]]
Conceito, história e benefícios dos padrões de projeto, incluindo a categorização em padrões criacionais, estruturais e comportamentais.

### [[Padrões Criacionais]]
Padrões que lidam com mecanismos de criação de objetos, como Singleton, Factory Method, Abstract Factory, Builder e Prototype.

### [[Padrões Estruturais]]
Padrões que focam na composição de classes e objetos, como Adapter, Bridge, Composite, Decorator, Facade, Flyweight e Proxy.

### [[Padrões Comportamentais]]
Padrões que definem como os objetos interagem e distribuem responsabilidades, como Observer, Strategy, Command, Template Method, Iterator, State e Visitor.

### [[Singleton]]
Padrão que garante que uma classe tenha apenas uma instância e fornece um ponto global de acesso a ela.

### [[Factory Method]]
Padrão que define uma interface para criar um objeto, mas deixa as subclasses decidirem qual classe instanciar.

### [[Observer]]
Padrão que define uma dependência um-para-muitos entre objetos, de modo que quando um objeto muda de estado, todos os seus dependentes são notificados e atualizados automaticamente.

### [[Strategy]]
Padrão que define uma família de algoritmos, encapsula cada um deles e os torna intercambiáveis, permitindo que o algoritmo varie independentemente dos clientes que o utilizam.

### [[Composite]]
Padrão que compõe objetos em estruturas de árvore para representar hierarquias parte-todo, permitindo que clientes tratem objetos individuais e composições de objetos de maneira uniforme.

### [[Anti-padrões]]
Soluções comuns que parecem adequadas, mas que na prática levam a problemas e devem ser evitadas. 