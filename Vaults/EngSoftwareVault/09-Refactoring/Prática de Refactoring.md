- Depende da existência de bons testes, principalmente unitários

#### Refactorings oportunistas
São realizados no meio de uma tarefa de programação, quando se descobre que um trecho de código não está bem implementado e que, portanto, pode ser melhorado. 

	"Para cada mudança que você tiver que realizar em um sistema, primeiro torne essa mudança fácil (aviso: isso pode ser difícil), então realize a mudança facilmente."

A ideia de fundo dessa recomendação é que um desenvolvedor pode estar enfrentando dificuldades para implementar uma mudança exatamente porque o código não está preparado para acomodá-la. Assim, primeiro ele deve dar um passo atrás, isto é, refatorar o código de forma oportunista, para tornar a mudança em questão fácil.
#### Refactorings planejados
Normalmente, eles são mudanças mais profundas, demoradas e complexas, que não valem a pena encaixar no meio de uma outra tarefa de desenvolvimento.
- Quebra de um pacote em dois ou mais subpacotes
	- Exigi atualizações em diversas partes do sistema
- Grande quantidade de refactorings pendentes
	- Melhor que sejam planejados para um período de tempo específico