Parametrizar alguma característica dos objetos criados, por exemplo:
- Protocolo de objetos TCP/IP ou UDP em um sistema distribuído

**Um método fábrica estático funciona como um aspirador de métodos new**

#### Simple static factory
```
class ChannelFactory{
	public static Channel createTCP(){
		return new TCPChannel();
	}
	
	public static Channel createUDP(){
		return new UDPChannel();
	}
}

void f() {
	Channel c = ChannelFactory.createTCP();
	...
}

void g() {
	Channel c = ChannelFactory.createUDP();
	...
}
```

#### Abstract factory
```
abstract class ProtocolFactory {
	abstract Channel createChannel();
	abstract Port createPort();
}

class TCPProtocolFactory extends ProtocolFactory {
	
}

class UDPProtocolFactory extends ProtocolFactory{

}

void f(ProcolFactory pf){
	Channel c = pf.createChannel();
	Port p = pf.createPort();
}
```

OBS: Uma classe abstrata é um "molde", contendo método abstratos que devem ser implementados por subclasses concretas.