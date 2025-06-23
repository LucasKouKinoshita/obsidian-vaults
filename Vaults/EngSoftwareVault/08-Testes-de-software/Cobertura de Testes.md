Mede o percentual de comandos de um programa que são cobertos por testes:

cobertura = numero de comandos executados pelos testes / total de comandos do programa

- Alguns IDE's possuem ferramentas para acompanhar a cobertura de testes.

#### Qual a cobertura ideal? 
- Não existe um número mágico e absoluto para cobertura de teste
	- Varia de projeto para projeto
- Geralmente, não é necessário 100% de cobertura
	- Getters e setters por exemplo não precisam ser testados por serem muito triviais
	- Métodos de interface com o usuário ou métodos comportamento assíncrono podem ser muito desafiadores
- Deve-se monitorar a evolução dos valores de cobertura ao longo do tempo, para verificar se os desenvolvedores, por exemplo, não estão relaxando na escrita de testes.
- Times que valorizam os testes costumam atingir 70% de cobertura facilmente
- Valores inferiores à 50% tendem a ser preocupantes
- Mesmo ao usar [[Desenvolvimento Dirigido por Testes (TDD)]] a cobertura não costuma alcançar 100%, embora geralmente fique acima de 90%

#### Outras definições 
Além da métrica baseada em comandos (C0) podemos também citar:
- Baseada em funções
- Cobertura de chamada de funções
- Cobertura de branches (C1)