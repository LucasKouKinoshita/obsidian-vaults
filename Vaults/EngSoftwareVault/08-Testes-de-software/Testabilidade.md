Medida do quão fácil é implementar testes para um dado sistema
- "Design for testability"

Código que seguem as [[Propriedades de projeto]] e os [[Princípios de projeto]] tendem a apresentar boa testabilidade

#### exemplo: Servlet
Servlet é uma tecnologia de Java para implementação de páginas Web dinâmica

```
public class IMCServlet extends HttpServlet { 
	public void doGet(HttpServletRequest req, HttpServletResponse res) {
		res.setContentType("text/html"); 
		PrintWriter out = res.getWriter(); 
		String peso = req.getParameter("peso"); 
		String altura = req.getParameter("altura"); 
		try { 
			double p = Double.parseDouble(peso); 
			double a = Double.parseDouble(altura); 
			double imc = p / (a * a);
			out.println("Índice de Massa Corporal (IMC): "+imc); 
		} catch (NumberFormatException e) { 
			out.println("Dados devem ser numéricos"); 
		} 
	} 
}
```

- Não é simples escrever um teste para IMCServlet
	- Dpende de diversos tipos do pacote de Servlets de Java
		- não é trivial instanciar um objeto do tipo IMCServlet e depois chamar doGet
		- teríamos que criar também objetos dos tipos HTTPServletRequest e HTTPServletResponse
		- No entanto, esses dois tipos podem depender de outros tipos e assim sucessivamente.
- Uma alternativa para testar o exemplo mostrado seria extrair a sua lógica de domínio para uma classe separada

```
class IMCModel { 
	public double calculaIMC(String p1, String a1) throws NumberFormatException { 
		double p = Double.parseDouble(p1); 
		double a = Double.parseDouble(a1); 
		return p / (a * a); 
	} 
} 

public class IMCServlet extends HttpServlet { 
	IMCModel model = new IMCModel(); 
	public void doGet(HttpServletRequest req, HttpServletResponse res) {
		res.setContentType("text/html"); 
		PrintWriter out = res.getWriter(); 
		String peso = req.getParameter("peso"); 
		String altura = req.getParameter("altura"); 
		try { double imc = model.calculaIMC(peso, altura);
			out.println("Índice de Massa Corporal (IMC): " + imc); 
		} catch (NumberFormatException e) { 
			out.println("Dados devem ser numéricos"); 
		} 
	} 
}
```

- É mais fácil instanciar um objeto da classe IMCModel do que da classe IMCServlet
- É verdade que com essa refatoração não vamos testar o código completo, mas é melhor testar a parte de domínio do sistema do que deixar o código inteiramente descoberto de testes.