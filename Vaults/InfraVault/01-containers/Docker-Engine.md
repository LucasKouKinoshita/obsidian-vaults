### Arquitetura

Por trás da Docker API existem [[Containerd]] e [[Runc]], mas a interação básica consiste de um cliente levando a API para um server. Por debaixo deste exterior/ user interface simples, o Docker utiliza intensamente mecanismos do [[Kernel]] como [[Iptables]], [[Virtual Bridging]], [[Cgroups]], [[Namespaces]] e outros [[Filesystem]] drivers.

#### Modelo Cliente/Servidor

É facil de pensar no Docker como um sistema que consiste de duas partes: o cliente e o servidor/daemon. Opcionalmente, existe um terceiro componente chamado de [[Registry |registrador]] que é responsável por guardar imagens docker e suas metadata.

O **server** é responsável por realizar o trabalho de building, running e manuseio de containers. Enquanto que o **cliente** é usado para informar o servidor o que deve ser feito. O Docker daemon pode ser executado em um número qualquer de servidores de infraestrutura, enquanto que um cliente único pode se referir a um número qualquer de servidores.

**Clientes** comandam toda comunicação, mas os servidores podem conversar diretamente com os registradores de imagens (quando requisitado pelo cliente).

![[Pasted image 20251007234014.png]]