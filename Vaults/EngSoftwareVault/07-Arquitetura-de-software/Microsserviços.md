Como discutido em [[Manifesto Ágil]], métodos ágeis preconizam iterações rápidas, com entregas frequentes de novas releases. Mesmo que uma empresa adote um método ágil como [[Scrum]] ela ainda vai enfrentar um gargalo arquitetural.
Esse gargalo ocorre porque sistemas, via de regra, seguem em tempo de execução uma arquitetura monolítica. Ou seja, mesmo que o desenvolvimento tenha sido particionado em módulos M1, M2, M3, …, Mn, em tempo de execução esses módulos são executados, pelo sistema operacional, como um processo único.
- Mudanças em Mi podem ter efeito colateral em Mj

#### Solução: arquitetura baseada em **microsserviços**
- Certos grupos de módulos são executados em processos independentes, sem compartilhamento de memória.
- Ou seja, o sistema é decomposto em módulos não apenas em tempo de desenvolvimento, mas também em tempo de execução.  Assim, não há possibilidade que um módulo acesse recursos internos de outro.
- Toda comunicação ocorre via interfaces públicas de cada módulo
- Microsserviços não implementam funcionalidades complexas.
- Cada microsserviço é desenvolvido por times pequenos de acordo com a filosofia proposta em [[Manifesto Ágil]]
- Arquiteturas baseadas em microsserviços tornaram-se possíveis devido ao aparecimento de plataformas de **computação em nuvem**.
##### Vantagens
- Facilita o desenvolvimento e modificação de módulos
- Escalabilidade
![[Pasted image 20250525224741.png]]
![[Pasted image 20250525224803.png]]
Monolito com escalabilidade horizontal vs Escalabilidade de microserviços
- Como os microsserviços são autônomos e independentes eles podem ser implementados em tecnologias diferentes, incluindo linguagens de programação, frameworks e bancos de dados.
- Quando se usa um monolito, falhas são totais. Se o banco de dados cair, todos os serviços ficam fora do ar. Por outro lado, em arquiteturas baseadas em microsserviços podemos ter **falhas parciais**.

#### Gerenciamento de dados
Pelo menos na sua forma pura, microsserviços devem ser autônomos também do ponto de vista de dados. Isto é, eles devem gerenciar os dados de que precisam para prover o seu serviço.
![[Pasted image 20250525225104.png]]
Não é recomendado que microsserviços comparitlhem o mesmo banco de dados

Idelamente M1 e M2 devem ser independentes
![[Pasted image 20250525225138.png]]
#### Quando não usar
- Complexidade - quando dois módulos executam em um mesmo processo, a comunicação entre eles é por meio de chamadas de métodos. Quando esses módulos estão em máquinas diferentes, a comunicação entre eles deve usar algum protocolo de comunicação, como **HTTP/REST**. Ou seja, os desenvolvedores terão que dominar e usar um conjunto de tecnologias para comunicação em redes.
- Latência - Comunicação entre microsserviços envolve um atraso
- Transações distribuídas - Difícil garantir que operações que operam em dois ou mais bancos de dados sejam atômicas.