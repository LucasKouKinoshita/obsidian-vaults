Não é raro encontrar um método implementado na classe errada. 
Movimentação de um método da classe A que usa mais serviços/ possui mais dependências para elementos de B.
Avaliar a possibilidade de mover o método de A para B
- Melhora coesão da classe A
- Diminui acoplamento de A e B
- Melhora legibilidade
- Melhora modularização do sistema overall

```
class A {
	B b = new B();
	void f {...}
}

class B { ... }

class Cliente {
	A a = new A();
	void g() {
		a.f();
		...
	}
}
```

```
class A {
	B b = new B();
	void f{
		b.f(); // delega cahmada para B
	}
}

class B {
	void f{...}
}

class Cliente {
	A a = new A();
	void g() {
		a.f();
		...
	}
}
```

O código da classe cliente nao precisou ser alterado
- Quando ocorre em uma mesma hierarquia de classes, Movimentação de Métodos ganha nomes especiais. Por exemplo, quando o refactoring move um método de subclasses para uma superclasse, ele é chamado de Pull Up Method. 
- Por outro lado, quando um método é movido para baixo na hierarquia de classes, isto é, de uma superclasse para uma subclasse, dizemos que foi realizado um Push Down Method.