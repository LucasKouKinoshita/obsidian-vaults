MVC = (Visão + Controladores) + Modelo = Interface Gráfica + Modelo
![[Pasted image 20250525222918.png]]

**Interfaces gráficas podem depender do modelo mas o modelo nunca depende da interface gráfica
Podemos entender a interface gráfica como observadora do Modelo**
#### Model
Classes que armazenam os dados manipulados pela aplicação e que têm a ver com o domínio do sistema em construção. Não possuem qualquer conhecimento ou dependência para classes de visão e controladoras. Também podem conter métodos que alteram o estado dos objetos de domínio.
#### View
Classes responsáveis pela apresentação da interface gráfica do sistema. (UI)
#### Controllers
Classes que tratam e interpretam eventos gerados por dispositivos de entrada, como mouse e teclado. Podem solicitar uma alteração no estado do modelo ou da visão.

#### Vantagens
- MVC favorece a especialização do trabalho de desenvolvimento (front/back end)
- MVC permite que classes de Modelo sejam usadas por diferentes Visões
- MVC favorece testabilidade -> é mais fácil testar objetos não-visuais, por isso, separar objetos de apresentação e objetos de modelo é uma boa prática.

#### Diferença entre MVC e três camadas.
- MVC surgiu para implementar interfaces gráficas.
- Um MVC pode, por exemplo, ser usado para implementação da camada de interface de uma aplicação nativa em Windows, mesmo que a aplicação como um todo siga uma arquitetura em três camadas ([[Arquitetura em Camadas]])

![[Pasted image 20250525223625.png]]
