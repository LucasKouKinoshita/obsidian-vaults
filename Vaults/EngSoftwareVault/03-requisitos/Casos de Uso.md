"São documentos textuais de especificação de
requisitos. Como veremos nesta seção, eles incluem descrições mais
detalhadas do que histórias de usuários"

- Descritos na fase de especificações de requisitos (waterfall)
- Escritos pelos desenvolvedores do sistema (engenheiros de requisito)
- Devem ser lidos, entendidos e validados pelos usuários antes da fase de design e implementação terem início
- Escritos da perspectiva de um ator que deseja usar o sistema.
	- Fluxo normal (caminho feliz)
		- Evitar comandos de decisão
			- Quando for necessário, pense em defini-la como exceção
	- Extensões do fluxo normal
		- Detalhar algum passo
		- Tratar erros, exceções, cancelamentos
		- Caminhos alternativos
- Todo caso de uso deve ter um nome (cuja primeira palavra deve estar no infinitivo)
- Deve informar um ator principal do caso de uso
- Pode incluir outro caso de uso (menciona-se o nome do caso de uso a ser incluído sublinhado)

#### Boas práticas
- Linguagem simples e direta - "Como no ensino fundamental"
- Pequenos, com poucos passos, principalmente no fluxo normal
- Casos de uso NÃO são pseudo-código. 
- NÃO devem tratar de aspectos tecnológicos ou de design
- Evite casos de uso muito simples (como CRUD)
- Vocabulário adotado deve ser padronizado ao longo dos casos

[[Diagramas de Caso de Uso]]
