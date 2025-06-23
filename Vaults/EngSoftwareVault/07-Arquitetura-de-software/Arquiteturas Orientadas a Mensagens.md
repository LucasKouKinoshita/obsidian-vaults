![[Pasted image 20250525225520.png]]
Neste tipo de arquitetura, a comunicação entre clientes e servidores é mediada por um terceiro serviço que tem a única função de prover uma **fila de mensagens**.

Clientes -> Produtores de informações
Servidor -> Consumidor de mensagem -> retiram mensagens da fila e processam a informação contida nelas.
Mensagem -> registro  ou objeto com um conjunto de dados
Fila -> estrutura FIFO

- Comunicação do lado do cliente torna-se assíncrona
	- É importante que o serviço seja instalado em uma máquina estável e com alto poder de processamento. 
	- A fila deve ser persistente (se o servidor que a gerencia cair, os dados não podem ser perdidos)
	- O formato das mensagens deve permanecer estável ao longo do desenvolvimento e do tempo em produção.

#### Vantanges
- Desacoplamento no espaço -> Clientes e servidores não precisam se conhecer
	- Facilidade de desenvolvimento 
- Desacoplamento no tempo -> Clientes e servidores não precisam estar simultaneamente disponíveis para se comunicarem
	- Robustez contra falhas
- Escalabilidade em sistemas distribuídos
	- Basta configurar múltiplos servidores consumindo uma mesma fila
![[Pasted image 20250525230129.png]]