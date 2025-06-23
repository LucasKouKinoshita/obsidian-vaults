- Aplicação da ideia de [[Coesão]]
- Caso particular da ideia de [[Princípio da Responsabilidade Única (SRP)]] com foco em interfaces

- Interfaces devem ser pequenas e coesas, mas mais importante, específicas para cada tipo de cliente.
	- O objetivo é evitar que clientes dependam de interfaces com métodos que eles não vão usar.
- Uma interface geral pode ser "segregada" em interfaces mais específicas.
``
```
// Bem segregada
interface Funcionario { 
	double getSalario(); 
	... 
} 
interface FuncionarioCLT extends Funcionario { 
	double getFGTS(); 
	... 
} 
interface FuncionarioPublico extends Funcionario { 
	int getSIAPE(); 
	... 
}

// Não segregada
interface Funcionario { 
	double getSalario();
	double getFGTS();// apenas funcionários CLT 
	int getSIAPE();// apenas funcionários públicos 
	... 
}

