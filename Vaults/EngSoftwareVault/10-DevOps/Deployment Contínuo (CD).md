Com [[Integração Contínua (CI)]] o código novo é frequentemente integrado à main branch.
- Código não necessariamente precisa estrar pronto para deploy
- Próximo passo proposto por DevOps é o deploy.
	- **Quando usa-se CD, todo novo commit que  chega ao master entra rapidamente em produção**
		- Fluxo de trabalho:
			- Desenvolvedor desenvolve e testa localmente
			- Realiza o commit e o servidor CI executa build e testes
			- Algumas vezes ao dia, o servidor de CI realiza os testes mais exaustivos com os novos commits que ainda não estão em produção.
				- [[Testes de Integração]]
				- [[Testes de Sistema]]
				- Testes de desempenho
			- Se todos os testes passarem, os commits entram em produção e os usuários já interagem com a nova versão
		- Vantagens:
			- Reduz tempo de entrega de novas features
			- Torna novas releases um "não-evento", não existe mais um dia D ou deadline de entrega para novas releases.
				- A perda de um deadline poderia fazer com que uma feature só entrasse em produção no próximo ciclo de desenvolvimento (meses depois)
				- Reduz stress causado por deadlines
			- Experimentação de um estilo de desenvolvimento orientado por dados e feedback dos usuários.

#### Entrega contínua
- Deployment contínua não é recomendável para certos tipos de sistemas, incluindo sistemas desktop, aplicações móveis e aplicações embutidas em hardware.
	- Utilização de uma versão mais fraca do CD -> entrega contínua
		- Quando se usa entrega contínua, todo commit **pode** entrar em produção imediatamente
			- O deployment depende de uma autorização manual.
- **Deployment**: é o processo de liberar uma nova versão de um sistema para seus usuários.
- **Delivery**: é o processo de liberar uma nova versão de um sistema para ser objeto de deployment

#### Feature Flags ou Feature Toggles
Nem sempre todo commit estará pronto para entrar imediatamente em produção

	"Se novas releases são liberadas quase todo dia, como evitar que minhas implementações parciais, que ainda não foram devidamente testadas ou que têm problemas de desempenho, cheguem até os usuários finais?"

- Não integrá-las no branch principal de desenvolvimento 
	- Leva ao indesejado Integration hell
- Integre continuamente o código parcial da funcionalidade X, mas com ela desabilitada, isto é, qualquer código relativo a X estará guardado por uma variável booleana (flag)
```
featureX = false
if (featureX){
...
}
```
