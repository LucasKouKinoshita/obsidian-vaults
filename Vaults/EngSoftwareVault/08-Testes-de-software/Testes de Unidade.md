- Verificam automaticamente pequenas partes de um código (uma classe apenas)
- A maior parte dos testes estão nessa categoria
- Simples
- Fácil implementação
	- Uso de frameworks como xUnit (existem versões de frameworks xUnit para as principais linguagens.)
	- Estrutura:
		- Fixture (contexto do teste) -> Instanciar objetos que se pretende testar e, se for o caso, inicializá-los.
		- Em seguida, o teste deve chamar um dos métodos da classe que está sendo testada
		- Por fim, testar se o resultado do método é igual o esperado. No JUnit usam-se o assert(), assertTrue() etc etc..
- Rápidos


- Um teste de unidade é um programa que chama métodos de uma classe e verifica se eles retornam os resultados esperados. Assim, quando se usa testes de unidades, o código de um sistema pode ser dividido em dois grupos: um conjunto de classes — que implementam os requisitos do sistema — e um conjunto de testes.

#### Implementação
- Uso de frameworks como xUnit (existem versões de frameworks xUnit para as principais linguagens.)
	- Estrutura:
		- Fixture (contexto do teste) -> Instanciar objetos que se pretende testar e, se for o caso, inicializá-los.
		- Em seguida, o teste deve chamar um dos métodos da classe que está sendo testada
		- Por fim, testar se o resultado do método é igual o esperado. No JUnit usam-se o assert(), assertTrue() etc etc..
##### Definições 
**Teste**: Método que implementa um teste, o nome deriva da anotação @Test
**Fixture**: Estado do sistema que será testado por um ou mais métodos de teste, incluindo dados, objetos etc..
**Test case**: Classe com métodos de teste. O nome tem origem nas primeiras versões do JUnit. Nessas versões, os métodos de testes eram implementados em classes que herdavam de uma classe TestCase.
**Test Suite**: conjunto de casos de teste, os quais são executados pelo framework de testes de unidade (que no nosso caso é o JUnit).
**Sistema sob teste (system under test, SUT)**: sistema que está sendo testado

#### Quando escrever testes de unidade
- Primeiro, pode-se escrever os testes após implementar uma pequena funcionalidade
- Pode-se escrever os testes primeiro, antes de qualquer código de produção. [[Desenvolvimento Dirigido por Testes (TDD)]]
- Quando um usuário reportar um bug, pode-se começar sua análise escrevendo um teste que reproduz o bug e que, portanto, vai falhar.
- Pode-se escrever testes também quando se estiver depurando um trecho de código.
- **NÃO** é recomendável é deixar para implementar todos os testes após o sistema ficar pronto 

#### Benefícios
- O principal benefício de testes de unidade é encontrar bugs, ainda na fase de desenvolvimento e antes que o código entre em produção
	- Custos de correção e prejuízos baixos.
- Rede de proteção contra regressões nos código
- Auxiliam na documentação e especificação do código de produção.