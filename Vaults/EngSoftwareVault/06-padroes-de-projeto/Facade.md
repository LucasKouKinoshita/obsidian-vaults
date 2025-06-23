 Uma Fachada é uma classe que oferece uma interface mais simples para um sistema. O objetivo é evitar que os usuários tenham que conhecer classes internas desse sistema; em vez disso, eles precisam interagir apenas com a classe de Fachada. As classes internas ficam encapsuladas por trás dessa Fachada.

``` 

class InterpretadorX {
	private String arq;
	
	InterpretadorX(arq) { construtor 
		this.arq = arq;
	}

	void eval(){ // lógica antes acessada diretamente pelos desenvolvedores
		Scanner s = new Scanner(arq);
		Parser p = new Parser(s);
		AST ast = p.parse();
		CodeGenerator code = new CodeGenerator(ast);
		code,eval();
	}
}

// desta forma, os desenvolvedores não precisam mais compreender/acessar/instanciar toda a lógica complexa de um evaluator.
// podendo simplesmente faze-lo por meio de 

new InterpretadorX("prog1.x").eval();

```