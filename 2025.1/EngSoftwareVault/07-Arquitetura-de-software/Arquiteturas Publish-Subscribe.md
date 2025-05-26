![[Pasted image 20250525231017.png]]

- Arquitetura orientada a eventos
- O serviço de publish/subscribe pode ser chamado de broker de eventos.
	- Funciona como um barramento por onde devem trafegar todos os eventos.
- Funcionamento semelhante ao [[Observer]], mas é uma solução de implementação de sistemas distribuídos, ou seja, produtores e assinantes são processos distintos e, na maioria das vezes, distribuídos, enquanto que o [[Observer]] não foi proposto no contexto de arquiteturas distribuídas.
##### Publicadores
Produzem eventos e os publicam em serviços de publish/subscribe que normalmente executam em máquina separada.
- Caso os eventos sejam organizados em tópicos, o publicador deve informar o tópico ao publicar um evento.
##### Assinantes
Assinantes devem assinar eventos de seu interesse e quando um evento é publicado, os assinantes interessados são notificados.
##### Eventos
Registro  ou objeto com um conjunto de dados a ser processado.
- Podem ser organizados em tópicos que funcionam como categorias de eventos.

#### Vantanges
- Desacoplamento no espaço e no tempo, semelhante à [[Arquiteturas Orientadas a Mensagens]]

#### Diferença entre publish/subcribe e fila de mensagens
- Em publish/subscribe, um evento gera notificações em todos os seus assinantes. Por outro lado, em filas de mensagens, as mensagens são sempre consumidas — isto é, retiradas da fila — por um único servidor. Portanto, em publish/subscribe temos um estilo de comunicação de 1 para _n_, também conhecido como **comunicação em grupo**. Já em filas de mensagens, a comunicação é 1 para 1, também chamada de **comunicação ponto-a-ponto**.
- Em publish/subscribe, os assinantes são notificados assincronamente. Primeiro, eles assinam certos eventos e, então, continuam seu processamento. Quando o evento de interesse ocorre, eles são notificados por meio da execução de um determinado método. Por outro lado, quando se usa uma fila de mensagens, os servidores — isto é, os consumidores das mensagens — têm que puxar (_pull_) as mensagens da fila.
