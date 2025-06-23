Ou wrapper, é um padrão que busca converter a interface de uma classe para outra interface esperada pelos seus clientes.

```
class ProjetorSamsung {
	public void turnOn(){...}
}

class ProjetorLG{
	public void enable(int timer){...}
}

// 2 interfaces diferentes para controlar projetores de marcas diferentes
interface Projetor(){ // interface desejada
	void liga();
}

class AdaptadorProjetorSamsung implements Projetor{
	private ProjetorSamsung projetor; // declara variável projetor do tipo projetorSamsung

	AdaptadorProjetorSamsung (ProjetorSamsung projetor) {
		this.projetor = projetor
	}
	
	public void liga() {
		projetor.turnOn();
	}
}

class AdaptadorProjetorLG implements Projetor{
	private ProjetorLG projetor; // declara variável projetor do tipo projetorLG

	AdaptadorProjetorLG (ProjetorLG projetor) { // construtor
		this.projetor = projetor
	}
	
	public void liga() { 
		projetor.enable();
	}
}

// Ambas as classes possuem sua interface "adaptada"
// Agora ambas os tipos de projetores podem ser ligados à partir de liga() por meio dos adaptadores.
```