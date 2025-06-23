#### Código duplicado
**Clone tipo 1**: Quando A e B possuem diferenças apenas de comentários e espaços
**Clone tipo 2**: Quando A e B são clones do tipo 1 mas as variáveis usadas em A e B também possuem nomes diferentes
**Clone tipo 3**: Quando A e B são clones do tipo 2 mas com pequenas mudanças em comandos
**Clone tipo 4**: Quando A e B são semanticamente equivalentes mas suas implementações são baseadas em algoritmos diferentes (2 formas diferentes de calcular fatorial por exemplo).
#### Métodos longos
- Tornam o código dificil de ler e manter
- Considerar possibilidade de usar [[Extração de método]]
- Tendência moderna é de escrever métodos com menos de 20 linhas
#### Classes grandes
- Assim como métodos, classes não devem possuir muitas responsabilidades
	- Baixa coesão
- Tornam o código dificil de entender e manter
- Dificultam reuso em outros pacotes ou sistema
- Considerar extração de classe para extrair um A' de uma classe A grande, de forma que A passa ater um atributo do tipo A'
#### Feature Envy
- Quando um método acessa mais atributos e métodos de outra classe
	- O método acessa mais a classe B do que sua própria classe A
- Acoplamento indesejado
- Considerar [[Movimentação de método]]
#### Método com muitos parâmetros
- Métodos, na medida do possível, devem ter poucos parâmetros.
- Deve-se verificar se um dos parâmetros pode ser obtido diretamente pelo método chamado
- Existe a possibilidade de criar um tipo que agrupe alguns dos parâmetros de um método.
#### Variáveis globais
- [[Acoplamento]] ruim indesejado
- Dificultam entendimento de um módulo de forma independente dos demais módulos do sistema.
#### Obsessão por tipos primitivos
- Tipos como int, float,  String etc.. são usados no lugar de classes.
	- Exemplo: 
```
// ruim
CEP: String = '';
// bom
CEP: Cep = new Cep();

class Cep(){
	validate(){...}
	...
}
```

- Uma classe pode oferecer métodos para manipular valores que a variável vai armazenar 
	- A classe assume responsabilidades e, consequentemente, evita que elas sejam uma preocupação de seus clientes
#### Objetos mutáveis
- Um objeto mutável é aquele cujo estado pode ser modificado
	- Para viabilizar a criação de objetos imutáveis, classes devem declarar todos os seus atributos como privados e final (um atributo final somente pode ser usado para leitura
	- A classe também deve ser declarada final, para proibir a criação de subclasses
	- Se precisarmos alterar um objeto imutável, a única alternativa consiste em criar uma nova instância do objeto com o estado desejado.
- Sempre que possível devemos criar objetos imutáveis, pois eles podem ser compartilhados de forma livre e segura com outras funções.
	- Garantia da manutenção do conteúdo de um objeto
	- Thread-safe
#### Data classes
- Classe inútil, só possui atributos e nenhum método
#### Comentários
- Não comente código ruim, reescreva-o