O uso de padrões também tem um custo.
Exemplos:
- Uma [[Abstract Factory]] requere a implementação de uma classe a mais no sistema

A adoção de padrões de projeto exige uma análise cuidadosa.
Exemplos:
- Antes de usar uma [[Abstract Factory]], devemos fazer (e responder) a seguinte pergunta: vamos mesmo precisar criar objetos de tipos diferentes no nosso sistema? Existem boas chances de que tais objetos sejam, de fato, necessários? Se sim, então vale a pena usar uma Fábrica para encapsular a criação de tais objetos. Caso contrário, é melhor criar os objetos usando o operador new, que é a solução nativa para criação de objetos em linguagens como Java.
- De forma semelhante, antes de incluir o padrão [[Strategy]] em uma certa classe devemos nos perguntar: vamos mesmo precisar de parametrizar os algoritmos usados na implementação dessa classe? Existem, de fato, usuários que vão precisar de algoritmos alternativos? Se sim, vale a pena usar o padrão [[Strategy]]. Caso contrário, é preferível implementar o algoritmo diretamente no corpo da classe

Em muitos sistemas observa-se um uso exagerado de padrões de projeto, em situações nas quais os ganhos de flexibilidade e extensibilidade são questionáveis. Existe até um termo para se referir a essa situação: paternite, isto é, uma inflamação associada ao uso precipitado de padrões de projeto.