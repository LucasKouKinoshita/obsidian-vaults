"Você deve integrar e testar o seu código em intervalos menores do que algumas horas. Programação em times não é um problema do tipo dividir-e-conquistar. Na verdade, é um problema que requer dividir, conquistar e integrar. A duração de uma tarefa de integração é imprevisível e pode facilmente levar mais tempo do que a tarefa original de codificação. Assim, quanto mais tempo você demorar para integrar, maiores e mais imprevisíveis serão os custos."
- Evitar conflitos gerados durante merges de branches 
	- Merges menores e portanto mais simples.

#### Boas práticas
##### Build automatizado
- O build não deve incluir nenhum passo manual
- O mais rápido possível (limite de 10 minutos)
##### Testes automatizados
- Garantir que o sistema compile sem erros após cada novo commit
- Garantir que o comportamento esperado foi mantido
	- CI requer boa cobertura de testes, principalmente [[Testes de Unidade]].
##### Servidores de integração contínua
- Builds e testes automatizados devem ser executados com frequência
	- Servidores de CI:
		- Funcionamento:
			- Após um novo commit, o sistema de controle de versões avisa o servidor, que clona o repo e executa um build e seus testes
			- Após execução, server notifica o usuário
				-  Um desenvolvedor somente deve avançar para uma próxima tarefa de programação após receber o resultado do servidor
		- Objetivo:
			- Evita integração de código problemático
				- Commits faltantes
				- Dependências incorretas
			- "Nada em uma empresa de software tem maior prioridade do que a correção de um build quebrado" (nem que seja reverter o código)

##### Desenvolvimento baseado no Trunk (ou master/main)
Como vimos, ao adotar CI, branches devem durar no máximo um dia de trabalho. Logo, o custo/benefício de criá-los pode não compensar. Por isso, quando migram para CI, é comum que as organizações usem também desenvolvimento baseado no trunk.
- **Todo desenvolvimento ocorre no branch principal, também conhecido com trunk ou master.**
##### Programação em pares
Programação em Pares (Pair Programming) pode ser considerada uma forma contínua de revisão de código.
Recomendado em CI mas não obrigatório

#### Quando não usar CI
- Quando é difícil seguir a limitação de integrações na master (ao menos uma por dia por desenvolvedor)
	- Este limite não é uma lei da natureza tho
- Projetos de código livre.
	- Devs voluntários não tem disponibilidade para trabalhar diariamente