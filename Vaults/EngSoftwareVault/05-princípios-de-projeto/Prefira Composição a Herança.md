#### Herança de classes
 (exemplo: class A extends B), que é aquela que envolve reúso de código. Não apenas neste capítulo, mas em todo o livro, quando mencionarmos apenas o termo herança estaremos nos referindo a herança de classes.
 (reuso em caixa-branca)

#### Herança de interfaces
(exemplo: interface I extends J), que não envolve reúso de código. Essa forma de herança é mais simples e não suscita preocupações. Quando precisarmos de nos referir a ela, iremos usar o nome completo: herança de interfaces.
(reuso em caixa-preta)

- Herança tende a introduzir problemas na manutenção e evolução das classes de um sistema
	- Esses problemas têm sua origem no forte acoplamento que existe entre subclasses e superclasses
- Recomenda-se: se existirem duas soluções de projeto, uma baseada em herança e outra em composição, a solução por meio de composição, normalmente, é a melhor.
	- Existe uma relação de composição entre duas classes A e B quando a classe A possui um atributo do tipo B.
	- Em uma composição, a relação entre as classes não é estática

```
// Herança
class Stack extends ArrayList { ... }

// Composição
class Stack { private ArrayList elementos; ... }
```