Quando existem problemas como;
- O escopo do teste ficar maior do que uma única unidade de código 
- O teste ficar lento pois depende de um serviço externo

Cria-se um objeto que emula o objeto real, mas apenas para permitir o teste do programa, chamado mock (ou stub).
- Não precisa acessar um serviço externo lento
- Testar a lógica do método de forma isolada e independente

#### Frameworks e mocks
- Mock são comuns em testes de unidade 
	- Existem frameworks para facilitar sua criação (ex:  mockito)
		- Não é mais necessário criar manualmente os mocks

#### Mocks vs Stubs
Alguns autores fazem distinção entre mocks e stubs.
- Mocks devem verificar não apenas o estado do Sistema sob Testes (SUT), mas também o seu comportamento.
- Se os mocks verificam apenas o estado, eles deveriam ser chamados de stubs
- Segundo Gerard Meszaros, mocks e stubs são casos especiais de objetos dublê (double).
	- Objetos Dummy são objetos que são passados como argumento para um método, mas que não são usados. Trata-se, portanto, de uma forma de dublê usada apenas para satisfazer o sistema de tipos da linguagem.
	- Objeto Fake são objetos que possuem uma implementação mais simples do que o objeto real. Por exemplo, um objeto que simula em memória principal, por meio de tabelas hash, um objeto de acesso a bancos de dados.