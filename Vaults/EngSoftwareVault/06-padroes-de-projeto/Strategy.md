O objetivo do padrão é parametrizar os algoritmos usados por uma classe. Ele prescreve como encapsular uma família de algoritmos e como torná-los intercambiáveis. Assim, seu uso é recomendado quando uma classe é usuária de um certo algoritmo (de ordenação, no nosso exemplo). Porém, como existem diversos algoritmos com esse propósito, não se quer antecipar uma decisão e implementar apenas um deles no corpo da classe.

```
class MyList{
	... // dados de uma lista
	... // métodos da lista: add, delete, search

	private SortStrategy strategy; // tipo de estratégia de ordenação
	public MyList(){
		strategy = new QuickSortStrategy();
	}
	public void setSortStrategy(SortStrategy strategy){
		this.strategy = strategy;
	}

	public void sort(){
		strategy.sort(this)
	}
}

abstract class SortStrategy {
	abstract void sort(MyList list); // método de ordenação a ser implementado pelas classes concretas
}

class QuickSortStrategy extends SortStrategy{
	void sort(MyList list){.. quick sort code ..}
}

class ShellSortStrategy extends SortStrategy {
	void sort(MyList list){.. shell sort code ..}
}

void main {
	MyList list = new MyList();
	list.add() = [...dados..]

	QuickSortStrategy qss = new QuickSortStrategy();
	list.setSortStrategy(qss);

	list = list.sort() 
}
```