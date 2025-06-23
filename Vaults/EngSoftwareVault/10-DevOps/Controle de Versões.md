- Software é desenvolvido em equipe
	- É necessário um server para armazenar o código fonte do sistema que está sendo implementado.
		- Desenvolvedores podem colaborar entre si de forma organizada
		- Operadores sabem precisamente qual versão do sistema deve ser colocada em produção
		- Histórico de versões mantido


#### Sistema de controle de versões (VCS)
- Repositório para armazenar a versão mais recente do código fonte de um sistema (e seus arquivos relacionados)
- Permite recuperar versões antigas de qualquer arquivo caso necessário. 
- História
	- 70's: SCCS
	- 80's: CVS
	- 2000's: svn
	- ![[Pasted image 20250621225716.png]]
		- Existe um único repo no nodo servidor
	- Inicio dos 2000's surgiram sistemas de controle de versões distribuídos (DVCS) com arquitetura peer-to-peer
		- BitKeeper
		- Mercurial
		- [[Git]]
		- Cada desenvolvedor possui em sua máquina um servidor completo de controle de versões que se comunica com servidores de outras máquinas (descentralizado)
		- ![[Pasted image 20250621225921.png]]


#### Multirepos vs Monorepos
Um VCS gerencia repositórios. Assim, uma organização precisa decidir os repositórios que vai criar em seu VCS.
- **Multirepos**: um VCS gerencia vários repositórios. Normalmente, um repositório por projeto ou sistema
- **Monorepos**: VCS gerencia um único repositório. Projetos são diretórios desse repositório.
	- Vantagens:
		- Fonte centralizada e ÓBVIA das versões do código fonte
		- Incentivam reuso e compartilhamento de código
		- Mudanças são sempre atômicas.
			- Multirepos as podem requirir multiplos commits para uma única mudança caso ela afete 2 sistemas diferentes.
		- Facilita execução de refactorings em larga escala
	- Desvantagens:
		- Requerem ferramentas para navegar em grandes code bases
			- Funcionários do Google foram obrigados a implementar internamente um plug-in para a IDE Eclipse que facilita o trabalho com uma base de código gigantesca.