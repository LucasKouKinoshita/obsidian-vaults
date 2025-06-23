"Em vez de iniciar as implantações à meia-noite de sexta-feira e passar o fim de semana trabalhando para concluí-las, as implantações ocorrem em qualquer dia útil, quando todos estão na empresa e sem que os clientes percebam — exceto quando encontram novas funcionalidades e correções de bugs."

Após o sistema estar concluído, ele se encontra pronto para entrar em produção. Esta tarefa é conhecida pelos nomes 
- Implementação (deploy)
- Liberação (release)
- Entrega (delivery)

Não é uma tarefa simples e rápida.
#### Organizações tradicionais
A área de TI era dividida em dois departamentos
- Departamento de sistemas (ou Desenvolvimento) -> devs, programadores, analistas e arquitetos
- Departamento de Suporte (ou Operações) -> Admins da rede, admins do BD, técnicos de suporte, técnicos de infra etc

Na maioria das vezes, a área de suporte tomava conhecimento de um sistema na véspera da sua implantação 
- Implantação podia atrasar meses (e até ser cancelada) devido a vários problemas não identificados
	- Falta de hardware para executar novo sistema/funcionalidade
	- Problemas de desempenho
	- Incompatibilidade com BD
	- Vulnerabilidades de segurança
- Esse modelo precisava de um stakeholder importante, os administradores de sistemas ou sysadmins
	- Conheciam características e requisitos não-funcionais de um novo software na véspera da implantação. 

#### Atualmente
Para solucionar os problemas citados, foi proposto o conceito de DevOps.
- **Movimento que visa unificar as cultuas de desenvolvimento e operação**
	- Implantação mais rápida e ágil
	- Evitar dois silos independentes de devs e ops com pouca/nenhuma interação
		- Sentam juntos para discutir questões sobre a entrega do sistema
	- Não requer um novo profissional, apenas a aproximação dos dois grupos
	- Automatização de todos os passos necessários para colocar um sistema em produção e monitorar o seu correto funcionamento
		- Requer testes automatizados
		- Requer [[Integração Contínua (CI)]]
		- Requer [[Deployment Contínuo (CD)]]