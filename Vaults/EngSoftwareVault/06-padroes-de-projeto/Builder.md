É um padrão de projeto que facilita a instanciação de objetos que têm muitos atributos, sendo alguns deles opcionais.

Livro esm = new Livro.Builder().setNome().setEditora().setAno().build();

livro gof = new Livro.Builder().setName().setAutores().setAno().build()