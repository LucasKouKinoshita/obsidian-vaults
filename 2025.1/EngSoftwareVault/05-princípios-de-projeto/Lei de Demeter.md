O Princípio de Demeter — também chamado de Princípio do Menor Privilégio (Principle of Least Privilege) — defende que a implementação de um método deve invocar apenas os seguintes outros métodos:
- de sua própria classe
- de objetos passados como parâmetros
- de objetos criados pelo próprio método
- de atributos da classe do método
```
class PrincipioDemeter { 
	T1 attr; 
	void f1() { 
		... 
	} 
	void m1(T2 p) { // método que segue Demeter 
		f1(); // caso 1: própria classe 
		p.f2(); // caso 2: parâmetro 
		new T3().f3(); // caso 3: criado pelo método 
		attr.f4(); // caso 4: atributo da classe 
		} 
		
	void m2(T4 p) { // método que viola Demeter
		p.getX().getY().getZ().doSomething(); 
	} 
}
```

Costuma-se dizer que o Princípio de Demeter recomenda que os métodos de uma classe devem falar apenas com seus amigos, isto é, com métodos da própria classe ou então com métodos de objetos que eles recebem como parâmetro ou que eles criam. Por outro lado, não é recomendável falar com os amigos dos amigos.