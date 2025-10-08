Questões importantes para a implementação de testes que tenham qualidade e que possam ser facilmente mantidos e entendidos
#### Princípio FIRST
**Fast**: é importante que eles sejam executados rapidamente (desenvolvedores devem executar testes de unidades frequentemente)
**Independents**: A ordem de execução dos testes de unidade não é importante.
**Repeatable**: Determinísticos, testes de unidade devem ter sempre o mesmo resultado.
**Self-checking**: O resultado de um teste de unidades deve ser facilmente verificável.  Para interpretar o resultado do teste, o desenvolvedor não deve, por exemplo, ter que abrir e analisar um arquivo de saída ou fornecer dados manualmente.
**Timely**: Se possível antes mesmo do código que vai ser testado. ([[Desenvolvimento Dirigido por Testes (TDD)]]).

#### Test smells
Representam estruturas e características preocupantes no código de testes de unidade, as quais, a princípio deveriam ser evitadas. Adaptação, no contexto de testes, do conceito de [[Code Smells]]. Ao identificar um test smell, os desenvolvedores devem refletir sobre se não é possível ter um teste mais simples e menor, com um código linear e sem duplicação de comandos

**Teste obscuro**: É um teste longo, complexo e difícil de entender
**Teste com Lógica Condicional**: inclui código que pode ou não ser executado. Isto é, são testes com comandos if ou laços, enquanto que o ideal é que os testes de unidade sejam lineares.
**Duplicação de código em testes**: ocorre, como o próprio nome sugere, quando temos código repetido em diversos métodos de teste.

#### Numero de asserts por teste
Alguns autores recomendam o máximo de um único assert por teste. No entanto, não devemos ser dogmáticos no emprego dessa regra, já que existem casos nos quais justifica-se ter mais de um assert por método (quando um método retorna um objeto com vários membros por exemplo ou quando um método simples pode ser testado por vários asserts de forma resumida).

```
@Test public void testRepeat() { 
	String input = "20"; 
	assertEquals("", Strings.repeat(input,0)); 
	assertEquals("20", Strings.repeat(input,1)); 
	assertEquals("2020", Strings.repeat(input,2)); 
	assertEquals("202020", Strings.repeat(input,3)); 
	... 
}
```

```
@Test public void testBookService() { 
	BookService bs = new BookService(); 
	Book b = bs.getBook(1234); 
	assertEquals("Engenharia Software Moderna", b.getTitle());
	assertEquals("Marco Tulio Valente", b.getAuthor()); 
	assertEquals("2020", b.getYear()); assertEquals("ASERG/DCC/UFMG", b.getPublisher()); 
}
```