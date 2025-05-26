é um padrão de projeto que padroniza uma interface para caminhar sobre uma estrutura de dados. Normalmente, essa interface inclui métodos como hasNext() e next(), como mostrado no seguinte exemplo

```
List<String> list = Arrays.asList("a","b","c");
Itarator it = list.iterator();
while(it.hasNext()){
	String s = (String) it.next();
	System.out.println(s);
}
```

Um iterador permite percorrer uma estrutura de dados sem conhecer o seu tipo concreto. Em vez disso, basta conhecer os métodos da interface Iterator.