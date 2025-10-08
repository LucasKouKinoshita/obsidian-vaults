"Onde você escreve a receita"
- Arquivo que carrega as instruções para a construção da [[Docker-Images |imagem]]
Observações:
- Todo dockerfile começa com "FROM" de onde decidimos a imagem base
- O app não é executado com algo como RUN npm start 
	- RUN é usado para compilar e buildar a imagem
	- CMD é usado para de fato iniciar um container após o processo de building
	- Imagens são construídas com o comando "docker build -t _image_name_ _path_" (ex: docker build -t shit-code .) 
		- -t significa "tag"
	- Para executar um container usamos "docker run -p _port_ _image_name_" (ex: docker run -p 9000:9000 shit-code)
		- -p significa "port fowarding"
		- 9000:9000, na esquerda a porta para o computador, na direita a porta para o container
#### Example
```
# Uses node version 22 as base image
FROM node:22

# Goes to app directory (like a cd terminal command)
WORKDIR /app

# Copy package.json and package-lock (if available)
COPY package*.jxon ./

# Install dependencies
RUN npm install

# Copy the rest of the app into the container
COPY . . 

# Set port env var
ENV PORT=9000

# Expose port so our computer can access it
EXPOSE 9000

# Run app
CMD ["npm", "start"]
```

- `FROM`: tecnologia que será a base de criação da imagem.
- `WORKDIR`: diretório da imagem na qual os comandos serão executados.
- `COPY`: comando para copiar o código fonte para a imagem.
- `RUN`: comando para instalação de dependências.
- `CMD`: comando para executar o seu código quando o container for criado.

![[108651385-67ccda80-74a0-11eb-9390-80df6ea6fd8c.png]]

[[Layer Caching]]
[[Dockerignore]]