"A palavra japonesa kanban significa cartão visual ou cartão de sinalização.
Desde a década de 50, o nome também é usado para denotar o processo de
produção just-in-time usado em fábricas japonesas, principalmente naquelas
da Toyota, onde ele foi usado pela primeira vez. O processo também é
conhecido como Sistema de Produção da Toyota (TPS) ou, mais
recentemente, por manufatura lean. Em uma linha de montagem, os cartões
são usados para controlar o fluxo de produção."

- Sistema de pull

- Ajuda times a trabalhar em ritmo sustentável
	- Elimina desperdicio
	- Entrega valor com frequência
	- Fomenta cultua de melhorias contínuas
- Times devem ser auto-organizáveis 
- Times cross-funcionais
- Mais simples do que o Scrum
	- Não usa eventos 
	- Não define papeis de forma rígida
	- Não usa artefatos com exceção do quadro de tarefas
		- Quadro kanban 
			- 1º coluna -> backlog
			- Demais colunas são passos que devem ser seguidos para transformar uma história do usuário em uma funcionalidade executável.
				- Especificação, implementação, revisão de código.
				- Cada coluna é divida em duas subcolunas
					- Execução
					- Concluída

![[Pasted image 20250406192419.png]]

- Uma história (H) deve ser quebrada em tarefas (T) durante a fase de especificação.
- Limites WIP
	- Evitar work overload
	- Limitar o máximo de cartões presentes em cada Step (contando aqueles em fase toDo e Done) com exceção do último passo, no qual o limite WIP aplica-se apenas ao toDo.
		- H2 conta como um cartão
		- T6, T7, T8, T9 contam como um segundo cartão por terem sido especificado da mesma história
		- T4 e T5 contam como 2 cartões
	- Cálculo
		- Aplicação da lei de little
			- Resultado da teoria de filas
			- "O numero de itens em um sistema de filas é igual à taxa de chegada desses itens multiplicado pelo tempo que cada item fica nos sistema"
				- WIP: número de tarefas em um dado passo de um processo Kanban.
				- Throughput (TP): taxa de chegada dessas tarefas nesse passo.
				- Lead Time (LT): tempo que cada tarefa fica nesse passo
		- Existem mais de uma alternativa mas o algoritmo proposto por Eric Brechner (eng da microsoft) é
			- Definir Lead time (LT), tempo médio que uma tarefa vai ficar em cada passo.
				- LT inclui tempo de fila (tempo que a tarefa vai ficar em Done)
				- LT_ Especificação -> 5 dias
				- LT_Implementação -> 12 dias
				- LT_Revisão -> 6 dias
			- Definir o throughput (TP), número de tarefas produzidas por dia no passo com maior LT (geralmente implementação) 
				- 8 tarefas por mes -> 0.38 tarefas/dia (21 dias uteis)
			- Limit WIP
				- WIP_passo = TP * LT_passo
				- WIP_esp = 0.38 * 5
				- WIP_imp = 0.38 * 12
				- WIP_rev = 0.38 * 6
			- Adicionar margem de erro de 50%