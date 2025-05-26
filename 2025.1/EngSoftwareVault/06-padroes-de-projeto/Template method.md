Ele especifica como implementar o esqueleto de um algoritmo em uma classe abstrata X, mas deixando pendente alguns passos — ou métodos abstratos. Esses métodos serão implementados nas subclasses de X. Em resumo, um Template Method permite que subclasses customizem um algoritmo, mas sem mudar a sua estrutura geral implementada na classe base.

- fundamental para frameworks
- inversão de controle

```
abstract class Funcionario {
	double salario;
	...
	// abstratos
	abstract double calcDescontosPrevidencia();
	abstract double calcDescontosPanoSaude();
	abstract double calcOutrosDescontons();

	public double calcSalarioLiquido(){ // template -> NAO É UM MÉTODO ABSTRATO
		double prev = calcDescontonsPrevidencia();
		double saude = calcDescontosPanoSaude();
		double outros = calcOutrosDescontos();
		return salario - prev - saude - outros;
	}
	// o template padroniza que precisam ser calculados os 3 descontos que serão posteriormente subtraídos do salario bruto.
	// O calculo do desconto no entanto varia de acordo com o tipo de funcionario
}

class FuncionarioPublico extends Funcionario {
// herda o método calcSalarioLiquido() 

// implementa
	double calcDescontosPrevidencia(){...};
	double calcDescontosPanoSaude(){...};
	double calcOutrosDescontons(){...};
}

class FuncionarioCLT extends Funcionario {
// herda o método calcSalarioLiquido() 

// implementa
	double calcDescontosPrevidencia(){...};
	double calcDescontosPanoSaude(){...};
	double calcOutrosDescontons(){...};
}
```