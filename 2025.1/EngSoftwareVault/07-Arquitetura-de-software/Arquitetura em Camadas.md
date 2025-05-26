- Em sistemas que seguem esse padrão, as classes são organizadas em módulos de maior tamanho, chamados de camadas.
- As camadas são dispostas de forma hierárquica
	- Uma camada somente pode usar serviços — isto é, chamar métodos, instanciar objetos, estender classes, declarar parâmetros, lançar exceções, etc. — da camada imediatamente inferior
- Um dos padrões mais usados
- Exemplo:
	- Implementação de protocolos de rede:
		- HTTP usa serviços de um protocolo de transporte (TCP)
			- TCP usa serviços de um protocolo de rede (IP)
				- IP usa serviços de um protocolo de comunicação (Ethernet)

#### Vantagens
- Uma arquitetura em camadas particiona a complexidade envolvida no desenvolvimento de um sistema em componentes menores
- Disciplina as dependências entre essas camadas


#### Arquitetura em três camadas
Geralmente é uma arquitetura distribuída, ou seja, a camada de interface executa na máquina dos clientes, a camada de aplicação em um servidor e, por fim, temos um banco de dados.

##### Interface com o usuário (camada de apresentação)
Responsável por toda interação com o usuário. Exibição de informação, coleta e processamento de inputs e eventos de interface.
##### Lógica de negócio (camada de aplicação)
Implementa regras de negócio do sistema.
- Pode possuir diversos módulos, incluindo uma [[Facade]] para facilitar o acesso ao sistema pelos clientes e um módulo de persistência com a função de isolar o banco de dados dos demais módulos
##### Banco de dados
Armazena os dados manipulados pelo sistema

![[Pasted image 20250525221927.png]]

#### Arquitetura em duas camadas
- Camadas de aplicação e interface unidas em uma única camada que executa no cliente.
- Banco de dados

Desvantagem: todo processamento ocorre nos clientes, o que requer maior necessidade de poder computacional.