Esse padrão define como adicionar uma operação em uma família de objetos (por exemplo uma [[lista polimórfica]]), sem que seja preciso modificar as classes dos mesmos. Além disso, o padrão Visitor deve funcionar mesmo em linguagens com single dispatching de métodos, como Java.


```
abstract class Veiculo {
	abstract public void accept(Visitor v);
}

class Carro extends Veiculo {
	...
	public void accept(Visitor v){
		v.visit(this)
	}
	...
}

class Onibus extends Veiculo {
	...
	public void accept(Visitor v){
		v.visit(this)
	}
	...
}

class Motocicleta extends Veiculo {
	...
	public void accept(Visitor v){
		v.visit(this)
	}
	...
}

PrintVisitor = new PrintVisitor();
foreach(Veiculo veiculo: listaVeiculos){
	veiculo.accept(visitor)
}
```