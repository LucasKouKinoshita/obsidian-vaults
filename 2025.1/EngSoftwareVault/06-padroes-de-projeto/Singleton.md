problema: Proliferação indesejada de vários objetos com a mesma classe.

Esse padrão de projeto define como implementar classes que terão, como o próprio nome indica, no máximo uma instância.

```
class Logger {
	private Logger(); // proibide clientes de chamar new Logger()
	private static Logger instance; // instancia unica

	public static Logger getInstance() {
		if(!instance) { // 1º vez que chama-se get instance
			instance = new Logger();  
		}
		return instance;
	}

	public void printLn(String msg){
		System.out.printLn(msg)
	}
}

void f() {
	Logger log = Logger.getInstance();
	log.printLn("executando f");
}

void g() {
	Logger log = Logger.getInstance();
	log.printLn("executando g");
}

void h() {
	Logger log = Logger.getInstance();
	log.printLn("executando h");
}
```
