![[108651385-67ccda80-74a0-11eb-9390-80df6ea6fd8c.png]]
Este arquivo armazenará as instruções para criação de uma [[Imagem Docker]]

No Dockerfile, você precisa incluir cinco instruções

- `FROM`: tecnologia que será a base de criação da imagem.
- `WORKDIR`: diretório da imagem na qual os comandos serão executados.
- `COPY`: comando para copiar o código fonte para a imagem.
- `RUN`: comando para instalação de dependências.
- `CMD`: comando para executar o seu código quando o container for criado.