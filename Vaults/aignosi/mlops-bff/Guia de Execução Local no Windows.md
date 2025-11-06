Este guia explica como executar o projeto `sientia-core-mlops-bff` localmente no Windows usando Maven.
## Pré-requisitos

### 1. Java 21

- **Requisito**: Java 21 (JDK)

- **Como verificar**: Abra o PowerShell e execute:

  ```powershell

  java -version

  ```

- **Instalação**:

  - **Opção 1 - Chocolatey (Microsoft OpenJDK)**:

    ```powershell

    choco install microsoft-openjdk --version=21

    ```

    Ou para instalar a versão mais recente do Java 21:

    ```powershell

    choco install microsoft-openjdk21

    ```

  - **Opção 2 - Download direto**:

    - Baixe o JDK 21 de [Adoptium (Eclipse Temurin)](https://adoptium.net/temurin/releases/?version=21) - **Recomendado**

    - Ou [Microsoft OpenJDK](https://learn.microsoft.com/en-us/java/openjdk/download)

    - Ou [Oracle JDK](https://www.oracle.com/java/technologies/downloads/#java21)

  - **Configurar JAVA_HOME**:

    - Após instalar, configure a variável de ambiente `JAVA_HOME` apontando para a instalação do JDK

    - Exemplo: `JAVA_HOME=C:\Program Files\Microsoft\jdk-21.x.x`

    - Adicione `%JAVA_HOME%\bin` ao `PATH`

  

### 2. PostgreSQL

Você tem duas opções:

  

#### Opção A: PostgreSQL Local (Recomendado para desenvolvimento)

1. Instale o PostgreSQL 15:

   - [Download oficial](https://www.postgresql.org/download/windows/)

   - Ou use Chocolatey: `choco install postgresql15`

2. Crie o banco de dados:

   ```sql

   CREATE DATABASE "sientia-core-mlops-bff";

   CREATE USER admin WITH PASSWORD 'secret';

   GRANT ALL PRIVILEGES ON DATABASE "sientia-core-mlops-bff" TO admin;

   ```

  

#### Opção B: PostgreSQL via Docker (Mais fácil)

```powershell

# Criar rede

docker network create sientia-network

  

# Criar container PostgreSQL

docker run --name sientia-postgres -d `

  --net sientia-network `

  -p 5432:5432 `

  -e POSTGRES_USER=admin `

  -e POSTGRES_PASSWORD=secret `

  -e POSTGRES_DB=sientia-core-mlops-bff `

  postgres:15

```

  

### 3. Maven Wrapper (Já incluído)

O projeto já inclui o Maven Wrapper (`mvnw.cmd`), então você **não precisa instalar Maven separadamente**.

  

## Configuração

  

### 1. Variáveis de Ambiente (Opcional)

Se você quiser sobrescrever configurações via variáveis de ambiente, configure:

  

```powershell

# Exemplo de configurações (opcional)

$env:SPRING_DATASOURCE_URL="jdbc:postgresql://localhost:5432/sientia-core-mlops-bff"

$env:SPRING_DATASOURCE_USERNAME="admin"

$env:SPRING_DATASOURCE_PASSWORD="secret"

```

  

### 2. MinIO (Obrigatório para o endpoint run-model)

O projeto precisa do MinIO para fazer upload dos arquivos de treinamento.

  

**Opção 1: Usar port-forward do Kubernetes (Recomendado se já tem OpenLens)**

  

Se você já tem um port-forward do MinIO no OpenLens:

  

1. **Verifique a porta do port-forward** no OpenLens (ex: `localhost:9000` ou outra porta)

  

2. **Ajuste o endpoint no `application.yaml`**:

   ```yaml

   sientia:

     mlops-bff:

       minio:

         endpoint: http://localhost:9000  # Use a porta do seu port-forward

         access-key: model-training-user

         secret-key: modelTrainingUser123

         bucket-name: model-training

   ```

  

3. **Verifique se o port-forward está ativo**:

   - No OpenLens, verifique se o port-forward do serviço MinIO está rodando

   - A porta deve estar acessível em `localhost:<porta>`

  

**Opção 2: Rodar MinIO localmente via Docker**

  

**Método Rápido** - Use o script automatizado:

```powershell

.\scripts\setup-minio.ps1

```

O script vai criar/configurar o MinIO automaticamente e te guiar para criar o bucket.

  

**Método Manual**:

  

```powershell

# Criar a rede se não existir (já criada se você rodou o PostgreSQL)

docker network create sientia-network

  

# Criar container MinIO

docker run --name sientia-minio -d `

  --net sientia-network `

  -p 9000:9000 `

  -p 9001:9001 `

  -e MINIO_ROOT_USER=model-training-user `

  -e MINIO_ROOT_PASSWORD=modelTrainingUser123 `

  minio/minio server /data --console-address ":9001"

```

  

**Após iniciar o MinIO**:

1. Acesse o console: http://localhost:9001

2. Faça login com:

   - Username: `model-training-user`

   - Password: `modelTrainingUser123`

3. Crie o bucket `model-training`:

   - Clique em "Buckets" no menu lateral

   - Clique em "Create Bucket"

   - Nome: `model-training`

   - Deixe as configurações padrão

   - Clique em "Create Bucket"

  

**Verificar se está rodando**:

```powershell

docker ps --filter "name=sientia-minio"

```

  

**Se o container já existir mas estiver parado**:

```powershell

docker start sientia-minio

```

  

### 3. Serviços Externos Adicionais (Opcional para desenvolvimento básico)

O projeto também depende de:

- **MLflow**: Para tracking de experimentos (já configurado remotamente: https://tracking.sientia.ai)

- **Temporal**: Para orquestração de workflows (configurado via port-forward ou endpoint remoto)

  

Para desenvolvimento básico local:

- **MLflow**: Já está configurado para usar o servidor remoto

- **Temporal**: Precisa de port-forward ou endpoint configurado (ver `temporal-architecture.md`)

  

## Executando o Projeto

  

### Método 1: Usando Maven Wrapper (Recomendado)

  

1. **Navegue até o diretório do projeto**:

   ```powershell

   cd C:\aignosi\sientia-core-mlops-bff

   ```

  

2. **Compile o projeto**:

   ```powershell

   .\mvnw.cmd clean compile

   ```

  

3. **Execute o projeto**:

   ```powershell

   .\mvnw.cmd spring-boot:run

   ```

  

   Ou de forma mais direta:

   ```powershell

   .\mvnw.cmd clean spring-boot:run

   ```

  

### Método 2: Buildar JAR e Executar

  

1. **Buildar o JAR**:

   ```powershell

   .\mvnw.cmd clean package

   ```

  

2. **Executar o JAR**:

   ```powershell

   java -jar target\sientia-core-mlops-bff-1.7.0.jar

   ```

  

### Método 3: Executar via IDE (IntelliJ IDEA / VS Code)

  

1. **IntelliJ IDEA**:

   - Abra o projeto

   - Encontre a classe `SientiaCoreMlopsBffApplication.java`

   - Clique com botão direito → "Run 'SientiaCoreMlopsBffApplication'"

  

2. **VS Code**:

   - Instale a extensão "Extension Pack for Java"

   - Abra a classe principal e use F5 ou o botão "Run"

  

## Configurações de Memória (Opcional)

  

Se você encontrar problemas de memória, pode ajustar as opções JVM:

  

```powershell

# Opção 1: Via Maven

$env:MAVEN_OPTS="-Xms320m -Xmx480m -XX:MaxMetaspaceSize=200m"

.\mvnw.cmd spring-boot:run

  

# Opção 2: Ao executar o JAR

java -Xms320m -Xmx480m -XX:MaxMetaspaceSize=200m -jar target\sientia-core-mlops-bff-1.7.0.jar

```

  

## Verificando se está funcionando

  

Após iniciar, você pode verificar:

  

1. **Health Check**:

   ```powershell

   curl http://localhost:8069/api/v1/actuator/health

   ```

  

2. **Swagger UI** (se habilitado):

   ```

   http://localhost:8069/api/v1/swagger-ui.html

   ```

  

3. **Logs**: Verifique o console para mensagens de inicialização do Spring Boot

  

## Troubleshooting

  

### Erro: "Port 8069 already in use"

```powershell

# Verificar qual processo está usando a porta

netstat -ano | findstr :8069

  

# Matar o processo (substitua PID pelo número do processo)

taskkill /PID <PID> /F

```

  

### Erro de conexão com PostgreSQL

- Verifique se o PostgreSQL está rodando: `docker ps` (se usar Docker)

- Verifique as credenciais no `application.yaml`

- Teste a conexão: `psql -h localhost -U admin -d sientia-core-mlops-bff`

  

### Erro de memória

- Ajuste as opções JVM conforme seção "Configurações de Memória"

- Verifique o arquivo `MEMORY_OPTIMIZATION.md` para mais detalhes

  

### Erro: "401 Unauthorized" ao baixar dependências do Maven

**Problema**: O projeto usa um repositório privado do GitHub (`sientia-core-api-common-lib`) que requer autenticação.

  

**Solução - Configurar autenticação Maven**:

  

**Método Rápido (Recomendado)** - Use o script automatizado:

```powershell

.\scripts\setup-maven-auth.ps1

```

O script vai guiá-lo através do processo de configuração.

  

**Método Manual**:

  

1. **Criar um Personal Access Token (PAT) no GitHub**:

   - Acesse: https://github.com/settings/tokens

   - Clique em "Generate new token" → "Generate new token (classic)"

   - Dê um nome (ex: "Maven - sientia-core-mlops-bff")

   - Selecione o escopo: `read:packages` (ou `repo` se for privado)

   - Clique em "Generate token"

   - **Copie o token** (você só verá ele uma vez!)

  

2. **Criar o arquivo settings.xml**:

   ```powershell

   # Criar o diretório .m2 se não existir

   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.m2"

   # Criar o arquivo settings.xml

   @"

   <?xml version="1.0" encoding="UTF-8"?>

   <settings xmlns="http://maven.apache.org/SETTINGS/1.2.0"

             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

             xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.2.0

             http://maven.apache.org/xsd/settings-1.2.0.xsd">

     <servers>

       <server>

         <id>sientia-core-api-common-lib-mvn-repo</id>

         <username>SEU_USUARIO_GITHUB</username>

         <password>SEU_TOKEN_GITHUB</password>

       </server>

     </servers>

   </settings>

   "@ | Out-File -FilePath "$env:USERPROFILE\.m2\settings.xml" -Encoding UTF8

   ```

  

3. **Editar o arquivo criado**:

   - Abra o arquivo: `C:\Users\<SEU_USUARIO>\.m2\settings.xml`

   - Substitua `SEU_USUARIO_GITHUB` pelo seu username do GitHub

   - Substitua `SEU_TOKEN_GITHUB` pelo token que você copiou

  

4. **Verificar se está funcionando**:

   ```powershell

   .\mvnw.cmd clean compile

   ```

  

**Nota**: Se você já tem um `settings.xml` no WSL funcionando, você pode copiar as credenciais de lá:

```powershell

# No WSL, veja o conteúdo do settings.xml:

cat ~/.m2/settings.xml

  

# Copie as credenciais (username e password) e cole no settings.xml do Windows

# Localização no Windows: C:\Users\<SEU_USUARIO>\.m2\settings.xml

```

  

**Dica de Segurança**:

- Nunca commite o arquivo `settings.xml` no repositório Git

- O arquivo está em `C:\Users\<usuario>\.m2\settings.xml` (fora do projeto)

- Considere usar um gerenciador de senhas para armazenar o token do GitHub

  

### Erro: "Process terminated with exit code: 1" no spring-boot:run

  

Este erro geralmente indica que a aplicação falhou ao iniciar. Para ver o erro completo:

  

1. **Executar com verbosidade completa**:

   ```powershell

   .\mvnw.cmd spring-boot:run -e

   ```

   Ou com debug completo:

   ```powershell

   .\mvnw.cmd spring-boot:run -X

   ```

  

2. **Causas comuns e soluções**:

  

   **a) PostgreSQL não está rodando**:

   ```powershell

   # Verificar se o container está rodando

   docker ps

   # Se não estiver, iniciar:

   docker start sientia-postgres

   # Ou criar se não existir:

   docker run --name sientia-postgres -d `

     --net sientia-network `

     -p 5432:5432 `

     -e POSTGRES_USER=admin `

     -e POSTGRES_PASSWORD=secret `

     -e POSTGRES_DB=sientia-core-mlops-bff `

     postgres:15

   ```

  

   **b) Erro de conexão com banco de dados**:

   - Verifique se o PostgreSQL está acessível: `localhost:5432`

   - Verifique as credenciais no `application.yaml`:

     - Username: `admin`

     - Password: `secret`

     - Database: `sientia-core-mlops-bff`

  

   **c) Erro de Flyway (migrations)**:

   - Se houver erro de migração, você pode desabilitar temporariamente:

     ```yaml

     # Em application.yaml, adicione:

     spring:

       flyway:

         enabled: false

     ```

   - Ou verifique os logs para ver qual migration está falhando

  

   **d) MinIO não está rodando** (erro: "Failed to connect to localhost:9000"):

   **Se usar port-forward do Kubernetes**:

   - Verifique se o port-forward está ativo no OpenLens

   - Verifique se a porta no `application.yaml` corresponde à porta do port-forward

   - Teste a conexão: `Test-NetConnection -ComputerName localhost -Port 9000`

   **Se usar Docker local**:

   ```powershell

   # Verificar se o container está rodando

   docker ps --filter "name=sientia-minio"

   # Se não estiver, iniciar:

   docker start sientia-minio

   # Ou criar se não existir:

   docker run --name sientia-minio -d `

     --net sientia-network `

     -p 9000:9000 `

     -p 9001:9001 `

     -e MINIO_ROOT_USER=model-training-user `

     -e MINIO_ROOT_PASSWORD=modelTrainingUser123 `

     minio/minio server /data --console-address ":9001"

   ```

   **Importante**: Após criar o container, você precisa:

   1. Acessar http://localhost:9001

   2. Fazer login com as credenciais acima

   3. Criar o bucket `model-training`

   **e) Temporal não está acessível**:

   - Verifique se o port-forward está ativo (se usar Kubernetes)

   - Verifique o endpoint no `application.yaml`: `sientia.mlops-bff.temporal.endpoint`

   - Veja mais detalhes em `doc/temporal-architecture.md`

  

3. **Alternativa - Executar o JAR diretamente** (Recomendado para ver o erro completo):

   ```powershell

   # Opção 1: Usar o script automatizado

   .\scripts\run-app.ps1

   # Opção 2: Manualmente

   .\mvnw.cmd clean package

   java -jar target\sientia-core-mlops-bff-1.7.0.jar

   ```

   Isso mostrará o erro completo do Spring Boot no console, incluindo o stack trace completo.

  

4. **Verificar logs do Spring Boot no Maven**:

   O Maven pode estar ocultando os logs. Tente executar com output direto:

   ```powershell

   .\mvnw.cmd spring-boot:run 2>&1 | Tee-Object -FilePath spring-boot.log

   ```

   Isso salvará os logs em `spring-boot.log` para análise.

  

### Erro: "java: command not found"

- Verifique se o Java está instalado: `java -version`

- Verifique se `JAVA_HOME` está configurado corretamente

- Reinicie o PowerShell após configurar variáveis de ambiente

  

### Erro: "openjdk21 not installed" no Chocolatey

Se você receber erro ao tentar instalar o Java via Chocolatey:

1. **Verifique pacotes disponíveis**:

   ```powershell

   choco search openjdk

   choco search microsoft-openjdk

   ```

2. **Use o nome correto do pacote**:

   ```powershell

   # Opção 1: Microsoft OpenJDK (recomendado)

   choco install microsoft-openjdk --version=21

   # Opção 2: Versão mais recente disponível

   choco install microsoft-openjdk

   ```

3. **Alternativa: Download manual**:

   - Baixe diretamente do [Adoptium](https://adoptium.net/temurin/releases/?version=21)

   - Execute o instalador e configure `JAVA_HOME` manualmente

  

## Diferenças entre WSL e Windows

  

### Caminhos de arquivos

- Windows usa `\` enquanto Linux/WSL usa `/`

- O Maven Wrapper já trata isso automaticamente

  

### Permissões

- No Windows, você geralmente não precisa de `chmod +x`

- O `mvnw.cmd` já é executável por padrão

  

### Variáveis de ambiente

- No PowerShell: `$env:VARIAVEL="valor"`

- No CMD: `set VARIAVEL=valor`

- No WSL: `export VARIAVEL=valor`

  

## Próximos Passos

  

1. **Verificar dependências**:

   ```powershell

   .\scripts\check-dependencies.ps1

   ```

  

2. **Configurar MinIO** (necessário para o endpoint `run-model`):

   - **Se usar port-forward do Kubernetes**: Apenas verifique se o port-forward está ativo no OpenLens e ajuste a porta no `application.yaml` se necessário

   - **Se rodar localmente**: Execute `.\scripts\setup-minio.ps1` e depois acesse http://localhost:9001 para criar o bucket `model-training`

  

3. **Configurar Temporal** (se necessário para testar workflows):

   - Se usar Kubernetes, configure o port-forward para `temporal-frontend`

   - Verifique o endpoint no `application.yaml`: `sientia.mlops-bff.temporal.endpoint`

   - Veja mais detalhes em `doc/temporal-architecture.md`

  

4. **Executar testes**: `.\mvnw.cmd test`

  

5. **Verificar documentação da API**: Swagger UI em `http://localhost:8069/api/v1/swagger-ui.html`

  

6. **Testar o endpoint run-model**:

   - Endpoint: `POST /api/v1/soft-sensor/run-model`

   - Body: `form-data` com:

     - `file`: arquivo CSV

     - `experimentRun`: JSON com os dados do experimento

   - Veja o Swagger UI para o formato exato do JSON

  

## Comandos Úteis

  

```powershell

# Limpar e compilar

.\mvnw.cmd clean compile

  

# Executar testes

.\mvnw.cmd test

  

# Buildar sem executar testes

.\mvnw.cmd clean package -DskipTests

  

# Verificar versão do Maven Wrapper

.\mvnw.cmd --version

  

# Atualizar Maven Wrapper (se necessário)

.\mvnw.cmd -N wrapper:wrapper -Dmaven=3.9.11

```