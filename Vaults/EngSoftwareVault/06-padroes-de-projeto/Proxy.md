O padrão de projeto Proxy defende a inserção de um objeto intermediário, chamado proxy, entre um objeto base e seus clientes. Assim, os clientes não terão mais uma referência direta para o objeto base, mas sim para o proxy. Por sua vez, o proxy possui uma referência para o objeto base. Além disso, o proxy deve implementar as mesmas interfaces do objeto base.
	Mediar o acesso a um objeto base, agregando-lhe funcionalidades, sem que ele tome conhecimento disso

![[Pasted image 20250523222527.png]]

```
classe BookSearchProxy implements BookSearchInterface {
	private BookSearchInterface base;
	BookSearchProxy(BookSearchInterface base) {
		this.base = base;
	}

	Book getBook(String ISBN) {
		if("IBSN no cache"){
			return "livro no cache"
		} else {
			Book book = base.getBook(ISBN);
			if(book != null){
				"adicione book no cache"
			}
			return book;
		}
	}
}

classe BookSearch implements BookSearchInterface { // mesma interface
	getBook(String ISBN){
		return book;
	}
}

void wrong_main(){ // NÃO é capaz de acessar o livro no cache
	BookSearch bs = new BookSearch();
	View view = new View(bs)
}

void main() {
	BookSearch bs = new BookSearch(); // declara base
	BookSearchProxy pbs; // declara proxy
	pbs = new BookSearchProxy(bs); // aponta proxy pra base
	..
	View view = new View(pbs) // view agora apontada para a proxy
	..
}
```