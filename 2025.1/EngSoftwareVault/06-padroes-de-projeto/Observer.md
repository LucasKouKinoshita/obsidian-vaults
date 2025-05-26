Esse padrão define como implementar uma relação do tipo um-para-muitos entre objetos sujeito e observadores. Quando o estado de um sujeito muda, seus observadores devem ser notificados.
![[Pasted image 20250525192316.png]]
- Os sujeitos não conhecem os observadores, de forma genérica, os sujeitos publicam um evento anunciando uma mudança e os observadores interessados são notificados.
	- Facilita reuso dos sujeitos em diversos cenários 
	- Facilita implementação de diversos observadores para o mesmo tipo de sujeito
- O padrão observer disponibiliza um mecanismo de notificação que pode ser reuso por diferentes pares ainda. Basta reusar a classe Subject e a interface Observer.

```
void main() {
	Temperatura t = new Temperatura() // Sujeito
	t.addObserver(new TermometroCelsius());
	t.addOberver(bew TermometroFahrenheit());
	t.setTemp(100.0);
}

// Subject é uma classe com método addObserver e notifyObservers
class Temperatura extends Subject { // sujeito

	private double temp;
	public double getTemp(){
		return temp;
	}
	public void setTemp(double temp){
		this.tempo = temp;
		notifyObservers(); // notifyObservers chama o método update() dos objetos que se registraram como observadores de uma instância de temperatura
		// update() faz parte da interface Observer que é implementada pelos observadores
	}
	
}

class TermometroCelsius implements Observer {

	public void update(Subject s){
		double temp = ((Temperatura) s).get Temp();
		System.out.println("Temperatura em Celsius: " + temp);
	}

}

class TermometroFahrenheit implements Observer {

	public void update(Subject s){
		double temp = ((Temperatura) s).get Temp();
		temp = celsiusToFahrenheit(temp)
		System.out.println("Temperatura em Fahrenheit: " + temp);
	}

	private celsiusToFahrenheit(double temp){...}
}

```