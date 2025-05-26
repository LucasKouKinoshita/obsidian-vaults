- Acoplamento é a força (strength) da conexão entre duas classes.

#### Acoplamento aceitável
- A classe A usa apenas métodos públicos de B
- A interface provida por B é estável do ponto de vista sintático e semântico. Isto é, as assinaturas dos métodos públicos de B não mudam com frequência; e o mesmo acontece com o comportamento externo de tais métodos. Por isso, mudanças em B raramente terão impacto em A.

#### Acoplamento ruim
- A classe realiza acesso direto a um arquivo ou banco de dados da classe B
- As classes A e B compartilham uma variável ou estrutura de dados global.
- Quando a interface da classe B não é estável, por exemplo, os métodos públicos de B são renomeados com frequência


**Acoplamento estrutural** entre A e B ocorre quando uma classe A possui uma referência explícita em seu código para uma classe B. Por exemplo, o acoplamento entre Estacionamento e Hashtable é estrutural.
- Pode ser aceitável a depender da estabilidade da classe de destino

**Acoplamento evolutivo (ou lógico)** entre A e B ocorre quando mudanças na classe B tendem a se propagar para a classe A. No exemplo mencionado, no qual a classe A depende de um inteiro armazenado em um arquivo interno de B, não existe acoplamento estrutural entre A e B, pois A não declara nenhuma variável do tipo B, mas existe acoplamento evolutivo. Por exemplo, mudanças no formato do arquivo criado por B terão impacto em A.
- Sempre ruim