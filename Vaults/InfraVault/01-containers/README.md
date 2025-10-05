# 01 - Containers e Virtualização

Esta seção aborda containerização moderna, com foco em Docker e tecnologias relacionadas. Os containers revolucionaram a forma como desenvolvemos, empacotamos e executamos aplicações.

## 📚 Índice de Tópicos

### 🐳 Docker Fundamentals
- [[Docker-Introducao|Introdução ao Docker]]
- [[Docker-Engine|Docker Engine e Arquitetura]]
- [[Dockerfile-Basico|Dockerfile Básico]]
- [[Docker-Images|Docker Images e Registries]]
- [[Docker-Compose|Docker Compose]]

### 🔧 Docker Avançado
- [[Docker-Networking|Docker Networking]]
- [[Docker-Volumes|Docker Volumes e Storage]]
- [[Docker-Security|Docker Security]]
- [[Docker-Multi-Stage|Multi-stage Builds]]
- [[Docker-Optimization|Otimização de Containers]]

### 🛠️ Ferramentas Relacionadas
- [[Podman|Podman - Docker Alternative]]
- [[Buildah|Buildah - Container Building]]
- [[Skopeo|Skopeo - Container Operations]]
- [[Docker-Desktop|Docker Desktop]]

### 📊 Monitoramento de Containers
- [[Container-Monitoring|Monitoramento de Containers]]
- [[Docker-Logs|Docker Logs]]
- [[Container-Metrics|Métricas de Containers]]

## 🎯 Objetivos de Aprendizado

Ao completar esta seção, você deve ser capaz de:

1. **Compreender Containerização**
   - Diferenciar containers de VMs
   - Entender namespaces e cgroups
   - Compreender isolamento de processos

2. **Dominar Docker**
   - Instalar e configurar Docker
   - Criar e gerenciar containers
   - Escrever Dockerfiles eficientes
   - Trabalhar com Docker Compose

3. **Gerenciar Imagens**
   - Criar e otimizar imagens
   - Trabalhar com registries
   - Implementar multi-stage builds
   - Aplicar security best practices

4. **Configurar Networking**
   - Entender Docker networking
   - Configurar portas e redes
   - Implementar service discovery

5. **Gerenciar Storage**
   - Trabalhar com volumes
   - Configurar persistent storage
   - Implementar backup strategies

## 🚀 Percurso de Estudo

### Semana 1: Docker Fundamentals
1. [[Docker-Introducao|Introdução ao Docker]]
2. [[Docker-Engine|Docker Engine e Arquitetura]]
3. [[Dockerfile-Basico|Dockerfile Básico]]

### Semana 2: Docker Intermediário
1. [[Docker-Images|Docker Images e Registries]]
2. [[Docker-Compose|Docker Compose]]
3. [[Docker-Networking|Docker Networking]]

### Semana 3: Docker Avançado
1. [[Docker-Volumes|Docker Volumes e Storage]]
2. [[Docker-Security|Docker Security]]
3. [[Docker-Multi-Stage|Multi-stage Builds]]

### Semana 4: Ferramentas e Otimização
1. [[Podman|Podman - Docker Alternative]]
2. [[Docker-Optimization|Otimização de Containers]]
3. [[Container-Monitoring|Monitoramento de Containers]]

## 🛠️ Ferramentas Essenciais

### Container Runtime
- **Docker** - Container runtime padrão
- **Podman** - Docker-compatible alternative
- **containerd** - Low-level container runtime
- **CRI-O** - Kubernetes container runtime

### Container Building
- **Dockerfile** - Container image definition
- **Buildah** - Container image building
- **Kaniko** - Building containers in Kubernetes
- **BuildKit** - Advanced build features

### Container Registries
- **Docker Hub** - Public registry
- **Amazon ECR** - AWS container registry
- **Azure Container Registry** - Microsoft registry
- **Google Container Registry** - GCP registry

### Container Orchestration
- **Docker Compose** - Local orchestration
- **Docker Swarm** - Docker native orchestration
- **Kubernetes** - Production orchestration
- **Nomad** - Workload orchestrator

## 📊 Projetos Práticos

### Projeto 1: Containerização de Aplicação Web
**Objetivo**: Containerizar uma aplicação web simples
**Tecnologias**: Docker, Dockerfile, Docker Compose
**Duração**: 1 semana

**Tarefas**:
- Criar Dockerfile para aplicação web
- Configurar multi-container com Docker Compose
- Implementar health checks
- Configurar volumes para persistência

### Projeto 2: Registry Privado
**Objetivo**: Configurar registry privado para imagens
**Tecnologias**: Docker Registry, Nginx, SSL
**Duração**: 1 semana

**Tarefas**:
- Deploy de registry privado
- Configurar autenticação
- Implementar SSL/TLS
- Configurar backup

### Projeto 3: CI/CD com Containers
**Objetivo**: Automatizar build e deploy de containers
**Tecnologias**: Jenkins, Docker, Git
**Duração**: 2 semanas

**Tarefas**:
- Configurar pipeline de CI/CD
- Implementar automated testing
- Configurar deployment automático
- Implementar rollback strategies

## 🔒 Segurança em Containers

### Container Security Best Practices
- **Use Official Images**: Imagens oficiais e verificadas
- **Minimal Base Images**: Imagens base mínimas
- **Non-root Containers**: Containers sem privilégios root
- **Image Scanning**: Scan de vulnerabilidades
- **Secrets Management**: Gerenciamento seguro de secrets

### Ferramentas de Segurança
- **Docker Bench Security**: Auditoria de segurança
- **Clair**: Análise de vulnerabilidades
- **Trivy**: Scanner de vulnerabilidades
- **Falco**: Runtime security monitoring

## 📈 Monitoramento e Observabilidade

### Métricas Importantes
- **Container Health**: Status e health checks
- **Resource Usage**: CPU, memória, I/O
- **Network Traffic**: Tráfego de rede
- **Log Aggregation**: Coleta centralizada de logs

### Ferramentas de Monitoramento
- **Docker Stats**: Métricas básicas
- **Prometheus**: Coleta de métricas
- **Grafana**: Visualização de dados
- **ELK Stack**: Log management

## 🎯 Próximos Passos

Após dominar containers, você estará preparado para:

1. **[[02-orquestracao/README|Orquestração de Containers]]** - Kubernetes e ferramentas de orquestração
2. **[[03-cloud-computing/README|Cloud Computing]]** - Deploy de containers na nuvem
3. **[[04-monitoramento/README|Monitoramento]]** - Observabilidade de aplicações containerizadas

## 📚 Recursos Adicionais

### Documentação Oficial
- [Docker Documentation](https://docs.docker.com/)
- [Podman Documentation](https://podman.io/docs/)
- [containerd Documentation](https://containerd.io/docs/)

### Livros Recomendados
- "Docker: Up & Running" - Karl Matthias
- "Docker in Action" - Jeff Nickoloff
- "Kubernetes: Up and Running" - Kelsey Hightower

### Cursos Online
- **Docker Training** - Cursos oficiais Docker
- **Linux Academy** - Container fundamentals
- **Coursera** - Container technologies

### Certificações
- **Docker Certified Associate (DCA)**
- **Kubernetes Certified Administrator (CKA)**
- **Red Hat Certified Specialist in Containers**

---

*Os containers são a base da infraestrutura moderna. Dominar Docker é essencial para trabalhar com Kubernetes, cloud computing e DevOps.*
