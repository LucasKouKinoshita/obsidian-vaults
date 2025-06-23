Diversas IDEs oferecem suporte para automatizar a realização de refactorings
- Renomeação automática

Antes de aplicar o refactoring, a IDE verifica se as suas pré-condições 
- Não trivial
- Exemplo de erro:
```
// arquivo A.java package P1; public class A { void n() { new B().m("abc"); // executa m(String) de B } } // arquivo B.java package P1; public class B { public void m(Object o) {...} void m(String s) {...}
```

```
// arquivo B.java package P2; // novo pacote de B public class B { public void m(Object o) {...} void m(String s) {...} }
```

Ao mover B para um novo pacote P2, a chamada m("abc) resulta na execução de m(Object) e não de m(String), já que B não está mais no mesmo pacote de A

(um método público de uma classe pública, como m(Object), pode ser chamado em qualquer parte do código. Mas métodos sem modificador de visibilidade, como m(String), somente podem ser chamados por código do mesmo pacote)

**Em resumo, o exemplo de Movimentação de Classes que apresentamos não é um refactoring, pois ele não preserva o comportamento do programa.**