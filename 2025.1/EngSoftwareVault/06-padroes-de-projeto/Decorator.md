O Padrão Decorador representa uma alternativa a herança quando se precisa adicionar novas funcionalidades em uma classe base.

O uso de herança é muitas vezes inviável, pois ela gera uma explosão combinatória do número de subclasses relacionadas a uma classe. Pensando no exemplo dos canais UDP e TCP (mencionado em [[Abstract Factory]]), caso o usuário precise de um canal UDP com buffer e compactação, precisamos implementar

UDPBufferedZipChannel, que é uma subclasse de UDPZipChannel, que é uma subclasse de UDPChannel.

```

channel = new ZipChannel(new TCPChanell());
// canal tcp com compactação
channel = new BufferChannel(new TCPChannel());
// canal tcp com buffer
channel = new BufferChannel(new UDPChannel());
// canal udp com buffer
channel = new BufferChannel(new ZipChannel( new TCPChannel()));
// canal tcp com compactação e buffer associado

// Sem necessidade de criar trocentas subclasses de UDPChannel e TCPChannel,
// a configuração de um Channel é feita no momento da sua instanciação
// por meio de uma sequência aninhada de operadores new.
// O new mais interno sempre cria uma classe base

interface Channel{ // interface base
	void send(String msg);
	String receive();
}

// classe é uma channel, ou seja, ela implementa a interface e seus dois métodos
// Possui um objeto tipo Channel para o qual delega as chamadas aos métodos da interface
// (que é um decorador)
class ChannelDecorator implements Channel {
	private Channel channel;
	public ChannelDecorator(Channel channel){ // construtor
		this.channel = channel;
	}

	public void send(String msg){
		channel.send(msg)
	}

	public String receive(){
		return channel.receive();
	}
}

// Agora as funcionalidades são implementadas como subclasses do decorador
class ZipChannel extends ChannelDecorator {
	public ZipChannel(Channel c){
		super(c);
	}
	public void send(String msg){
		"compacta msg"
		super.send(msg) // delega a mensagem compactada para o decorador base
	}
	public String receive(){
		String msg = super.reeceive();
		"descompacta msg"
		return msg
	}
}

void main {
	Channel c = new ZipChannel(new TCPChannel());
	c.send("Hi!")
}
// 1º executa-se ZipChannel.send que compacta a msg
// 2º ZipChannel.send chama super.send pois ChannelDecorator é superclasse de ZipChannel
// 3º ChannelDecorator.send apenas repassa a chamada para o Channel referenciado (no caso um TCPChannel)
// 4º TCPChannel.send transmite a mensagem via protoclo TCP.

```