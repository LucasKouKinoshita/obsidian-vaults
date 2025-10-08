# Cloud Computing - Conceitos Fundamentais

Cloud computing revolucionou a forma como organizamos e gerenciamos infraestrutura de TI. É a base para a infraestrutura moderna e essencial para entender containers, microserviços e DevOps.

## 🎯 O que é Cloud Computing?

Cloud computing é a entrega de recursos de computação (servidores, armazenamento, bancos de dados, rede, software, analytics) pela internet ("a nuvem") com modelo de preços pay-as-you-go.

### Características Essenciais (NIST)
1. **On-demand self-service**: Recursos sob demanda
2. **Broad network access**: Acesso via rede
3. **Resource pooling**: Pool de recursos compartilhados
4. **Rapid elasticity**: Escalabilidade rápida
5. **Measured service**: Serviços medidos

## 🏗️ Modelos de Serviço

### IaaS - Infrastructure as a Service
**O que é**: Fornece recursos de computação virtualizados pela internet.

#### Características
- **Controle**: Máximo controle sobre recursos
- **Responsabilidade**: Cliente gerencia SO, middleware, aplicações
- **Exemplos**: AWS EC2, Azure VMs, Google Compute Engine
- **Uso**: Migração de data centers, desenvolvimento

#### Recursos Típicos
- Máquinas virtuais
- Armazenamento
- Redes
- Load balancers
- Firewalls

### PaaS - Platform as a Service
**O que é**: Fornece ambiente de desenvolvimento e deployment de aplicações.

#### Características
- **Controle**: Controle sobre aplicações e dados
- **Responsabilidade**: Provider gerencia infraestrutura e plataforma
- **Exemplos**: AWS Elastic Beanstalk, Azure App Service, Google App Engine
- **Uso**: Desenvolvimento de aplicações, APIs

#### Recursos Típicos
- Runtime environments
- Middleware
- Development tools
- Database management
- Business intelligence

### SaaS - Software as a Service
**O que é**: Software hospedado e entregue pela internet.

#### Características
- **Controle**: Apenas sobre configurações
- **Responsabilidade**: Provider gerencia tudo
- **Exemplos**: Salesforce, Office 365, Gmail, Slack
- **Uso**: Aplicações de usuário final

#### Recursos Típicos
- Web-based applications
- Email services
- CRM systems
- Collaboration tools

## 🏢 Modelos de Deployment

### Public Cloud
- **Definição**: Recursos compartilhados entre múltiplos clientes
- **Características**: Economia de escala, baixo custo
- **Exemplos**: AWS, Azure, Google Cloud
- **Uso**: Startups, desenvolvimento, aplicações públicas

### Private Cloud
- **Definição**: Recursos dedicados a uma organização
- **Características**: Maior controle, segurança
- **Exemplos**: VMware vSphere, OpenStack
- **Uso**: Empresas grandes, compliance rigoroso

### Hybrid Cloud
- **Definição**: Combinação de public e private cloud
- **Características**: Flexibilidade, portabilidade
- **Exemplos**: AWS + On-premises, Azure Arc
- **Uso**: Migração gradual, workloads específicos

### Multi-Cloud
- **Definição**: Uso de múltiplos provedores de cloud
- **Características**: Evita vendor lock-in, otimização de custos
- **Exemplos**: AWS + Azure + GCP
- **Uso**: Redundância, especialização por workload

## ☁️ Principais Provedores de Cloud

### Amazon Web Services (AWS)
- **Market Share**: ~32% (líder mundial)
- **Forças**: Ecossistema completo, pioneiro
- **Serviços Principais**: EC2, S3, Lambda, RDS
- **Uso**: Empresas de todos os tamanhos

### Microsoft Azure
- **Market Share**: ~20%
- **Forças**: Integração com Microsoft, enterprise
- **Serviços Principais**: Virtual Machines, App Service, SQL Database
- **Uso**: Empresas Microsoft, governo

### Google Cloud Platform (GCP)
- **Market Share**: ~9%
- **Forças**: AI/ML, data analytics, Kubernetes
- **Serviços Principais**: Compute Engine, BigQuery, AI Platform
- **Uso**: Data science, startups tech

### Outros Provedores
- **IBM Cloud**: Foco em enterprise e AI
- **Oracle Cloud**: Database e enterprise applications
- **DigitalOcean**: Simplicidade e desenvolvedores
- **Alibaba Cloud**: Mercado asiático

## 💰 Modelos de Preços

### Pay-as-you-go
- **Características**: Pague apenas pelo que usar
- **Vantagens**: Baixo custo inicial, flexibilidade
- **Desvantagens**: Custos podem crescer rapidamente
- **Uso**: Desenvolvimento, workloads variáveis

### Reserved Instances
- **Características**: Compromisso de longo prazo
- **Vantagens**: Desconto significativo (até 75%)
- **Desvantagens**: Menos flexibilidade
- **Uso**: Workloads estáveis, produção

### Spot Instances
- **Características**: Preço baseado em oferta/demanda
- **Vantagens**: Custo muito baixo (até 90% desconto)
- **Desvantagens**: Pode ser interrompido
- **Uso**: Workloads tolerantes a falhas, batch processing

## 🔧 Serviços Essenciais por Categoria

### Computação
- **Virtual Machines**: EC2, Azure VMs, Compute Engine
- **Serverless**: AWS Lambda, Azure Functions, Cloud Functions
- **Containers**: ECS, AKS, GKE
- **Kubernetes**: EKS, AKS, GKE

### Armazenamento
- **Object Storage**: S3, Blob Storage, Cloud Storage
- **Block Storage**: EBS, Azure Disks, Persistent Disks
- **File Storage**: EFS, Azure Files, Filestore
- **Archive Storage**: Glacier, Archive Storage, Coldline

### Rede
- **Virtual Networks**: VPC, Virtual Network, VPC
- **Load Balancers**: ALB, Load Balancer, Cloud Load Balancing
- **CDN**: CloudFront, Azure CDN, Cloud CDN
- **DNS**: Route 53, Azure DNS, Cloud DNS

### Banco de Dados
- **Relational**: RDS, SQL Database, Cloud SQL
- **NoSQL**: DynamoDB, Cosmos DB, Firestore
- **Data Warehouse**: Redshift, Synapse, BigQuery
- **Cache**: ElastiCache, Redis Cache, Memorystore

## 🔒 Segurança em Cloud

### Responsabilidade Compartilhada
- **Provider**: Infraestrutura física, hypervisor, rede
- **Cliente**: Dados, aplicações, configurações, acesso

### Princípios de Segurança
- **Identity and Access Management (IAM)**
  - Autenticação multi-fator
  - Princípio do menor privilégio
  - Rotação de credenciais

- **Network Security**
  - Segmentação de rede
  - Firewalls e security groups
  - VPN e conexões privadas

- **Data Protection**
  - Criptografia em trânsito e em repouso
  - Backup e disaster recovery
  - Compliance e auditoria

### Ferramentas de Segurança
- **AWS**: IAM, CloudTrail, GuardDuty, WAF
- **Azure**: Active Directory, Security Center, Sentinel
- **GCP**: Cloud IAM, Security Command Center, Cloud Armor

## 📊 Monitoramento e Observabilidade

### Métricas Essenciais
- **Performance**: CPU, memória, latência
- **Availability**: Uptime, downtime
- **Cost**: Gastos por serviço, projeções
- **Security**: Tentativas de acesso, vulnerabilidades

### Ferramentas de Monitoramento
- **AWS**: CloudWatch, X-Ray, CloudTrail
- **Azure**: Monitor, Application Insights, Log Analytics
- **GCP**: Cloud Monitoring, Cloud Trace, Cloud Logging

### Best Practices
- **Logging Centralizado**: Coleta e análise de logs
- **Alertas Proativos**: Notificações de problemas
- **Dashboards**: Visualização de métricas
- **Cost Optimization**: Monitoramento de custos

## 🚀 Benefícios do Cloud Computing

### Para Desenvolvedores
- **Rapid Deployment**: Deploy rápido de aplicações
- **Scalability**: Escala automática
- **Global Reach**: Presença global
- **Innovation**: Acesso a tecnologias emergentes

### Para Empresas
- **Cost Reduction**: Redução de custos de TI
- **Agility**: Maior agilidade de negócio
- **Reliability**: Alta disponibilidade
- **Security**: Segurança enterprise-grade

### Para Startups
- **Low Barrier to Entry**: Baixo custo inicial
- **Global Scale**: Escala global
- **Focus on Core Business**: Foco no negócio
- **Rapid Growth**: Crescimento rápido

## 🎯 Próximos Passos

Após dominar os conceitos de cloud computing, você estará preparado para:

1. **[[IaaS-PaaS-SaaS|IaaS, PaaS e SaaS]]** - Modelos detalhados
2. **[[AWS-Fundamentos|AWS Fundamentals]]** - Líder de mercado
3. **[[Azure-Fundamentos|Azure Fundamentals]]** - Microsoft cloud
4. **[[GCP-Fundamentos|GCP Fundamentals]]** - Google cloud

## 📚 Recursos Adicionais

### Documentação Oficial
- [AWS Documentation](https://docs.aws.amazon.com/)
- [Azure Documentation](https://docs.microsoft.com/en-us/azure/)
- [Google Cloud Documentation](https://cloud.google.com/docs)

### Livros Recomendados
- "Cloud Computing: Concepts, Technology & Architecture" - Thomas Erl
- "AWS Well-Architected Framework" - Amazon
- "Architecting Microsoft Azure Solutions" - Microsoft

### Cursos Online
- **AWS Training** - Cursos oficiais AWS
- **Microsoft Learn** - Treinamento Azure
- **Google Cloud Training** - Cursos GCP
- **Linux Academy** - Cloud computing

### Certificações
- **AWS Certified Solutions Architect**
- **Microsoft Azure Solutions Architect**
- **Google Cloud Professional Architect**

---

*Cloud computing é a base da infraestrutura moderna. Compreender seus conceitos é essencial para trabalhar com tecnologias como containers, Kubernetes e DevOps.*
