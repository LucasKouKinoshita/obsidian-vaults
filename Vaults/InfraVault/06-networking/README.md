# 06 - Networking e Conectividade

Esta seção aborda redes e conectividade em infraestrutura moderna, cobrindo load balancers, service mesh, DNS e networking avançado.

## Índice de Tópicos

### Fundamentos de Networking
- [[Networking-Introducao|Introdução ao Networking]]
- [[Load-Balancing|Load Balancing]]
- [[DNS-Fundamentos|Fundamentos de DNS]]
- [[CDN|Content Delivery Networks]]
- [[Network-Topologies|Topologias de Rede]]

### Service Mesh
- [[Service-Mesh-Introducao|Introdução ao Service Mesh]]
- [[Istio|Istio - Service Mesh]]
- [[Linkerd|Linkerd - Service Mesh]]
- [[Consul-Connect|Consul Connect]]
- [[Service-Mesh-Comparison|Comparação de Service Meshes]]

### Load Balancing
- [[Load-Balancer-Types|Tipos de Load Balancers]]
- [[HAProxy|HAProxy]]
- [[NGINX|NGINX Load Balancer]]
- [[AWS-ALB|AWS Application Load Balancer]]
- [[Load-Balancing-Algorithms|Algoritmos de Load Balancing]]

### DNS e Service Discovery
- [[DNS-Advanced|DNS Avançado]]
- [[Service-Discovery|Service Discovery]]
- [[Consul|HashiCorp Consul]]
- [[etcd|etcd]]
- [[CoreDNS|CoreDNS]]

### Network Security
- [[Network-Security|Segurança de Rede]]
- [[VPN|Virtual Private Networks]]
- [[Tunneling|Tunneling e Proxies]]
- [[Network-Segmentation|Segmentação de Rede]]
- [[Zero-Trust-Networking|Zero Trust Networking]]

## Objetivos de Aprendizado

Ao completar esta seção, você estará preparado para:

1. **Compreender Networking**
   - Entender arquiteturas de rede
   - Implementar load balancing
   - Configurar DNS e service discovery

2. **Dominar Service Mesh**
   - Implementar service mesh
   - Configurar Istio
   - Gerenciar tráfego entre serviços

3. **Configurar Load Balancing**
   - Implementar load balancers
   - Configurar algoritmos de balanceamento
   - Monitorar performance

4. **Gerenciar DNS**
   - Configurar DNS avançado
   - Implementar service discovery
   - Gerenciar registros DNS

5. **Implementar Segurança**
   - Configurar network security
   - Implementar VPN
   - Aplicar zero trust

## Percurso de Estudo

### Semana 1: Fundamentos
1. [[Networking-Introducao|Introdução ao Networking]]
2. [[Load-Balancing|Load Balancing]]
3. [[DNS-Fundamentos|Fundamentos de DNS]]

### Semana 2: Service Mesh
1. [[Service-Mesh-Introducao|Introdução ao Service Mesh]]
2. [[Istio|Istio - Service Mesh]]
3. [[Service-Mesh-Comparison|Comparação de Service Meshes]]

### Semana 3: Load Balancing
1. [[Load-Balancer-Types|Tipos de Load Balancers]]
2. [[HAProxy|HAProxy]]
3. [[NGINX|NGINX Load Balancer]]

### Semana 4: DNS e Discovery
1. [[DNS-Advanced|DNS Avançado]]
2. [[Service-Discovery|Service Discovery]]
3. [[Consul|HashiCorp Consul]]

### Semana 5: Network Security
1. [[Network-Security|Segurança de Rede]]
2. [[VPN|Virtual Private Networks]]
3. [[Zero-Trust-Networking|Zero Trust Networking]]

## Ferramentas Essenciais

### Load Balancers
- **HAProxy** - High availability proxy
- **NGINX** - Web server e load balancer
- **Traefik** - Modern load balancer
- **Envoy** - High performance proxy

### Service Mesh
- **Istio** - Service mesh platform
- **Linkerd** - Lightweight service mesh
- **Consul Connect** - Service mesh
- **Kuma** - Universal service mesh

### DNS e Discovery
- **CoreDNS** - DNS server
- **Consul** - Service discovery
- **etcd** - Distributed key-value store
- **Zookeeper** - Coordination service

### Network Security
- **Calico** - Network security
- **Cilium** - Network security
- **WireGuard** - VPN protocol
- **OpenVPN** - VPN solution

## Projetos Práticos

### Projeto 1: Load Balancer Setup
**Objetivo**: Configurar load balancer
**Tecnologias**: HAProxy, NGINX, Docker
**Duração**: 1 semana

**Tarefas**:
- Configurar HAProxy
- Implementar health checks
- Configurar SSL termination
- Implementar monitoring

### Projeto 2: Service Mesh
**Objetivo**: Implementar service mesh
**Tecnologias**: Istio, Kubernetes
**Duração**: 1 semana

**Tarefas**:
- Instalar Istio
- Configurar traffic management
- Implementar security policies
- Configurar observability

### Projeto 3: DNS e Discovery
**Objetivo**: Configurar service discovery
**Tecnologias**: Consul, CoreDNS
**Duração**: 1 semana

**Tarefas**:
- Configurar Consul
- Implementar service registration
- Configurar health checks
- Implementar service discovery

## Conceitos Avançados

### Service Mesh Benefits
- **Traffic Management** - Gerenciamento de tráfego
- **Security** - Segurança entre serviços
- **Observability** - Observabilidade
- **Policy Enforcement** - Aplicação de políticas

### Load Balancing Algorithms
- **Round Robin** - Distribuição sequencial
- **Least Connections** - Menor número de conexões
- **Weighted Round Robin** - Round robin com pesos
- **IP Hash** - Hash do IP do cliente
- **Least Response Time** - Menor tempo de resposta

### DNS Record Types
- **A** - IPv4 address
- **AAAA** - IPv6 address
- **CNAME** - Canonical name
- **MX** - Mail exchange
- **TXT** - Text records
- **SRV** - Service records

## Próximos Passos

Após dominar networking, você estará preparado para:

1. **[[07-automacao/README|Automação]]** - Automação de networking
2. **[[08-storage/README|Storage]]** - Storage networking
3. **[[09-cicd/README|CI/CD]]** - Networking em CI/CD

## Recursos Adicionais

### Documentação Oficial
- [Istio Documentation](https://istio.io/docs/)
- [HAProxy Documentation](https://www.haproxy.org/docs/)
- [NGINX Documentation](https://nginx.org/en/docs/)

### Livros Recomendados
- "Istio in Action" - Christian Posta
- "NGINX Cookbook" - Derek DeJonghe
- "Service Mesh Patterns" - Lee Calcote

### Certificações
- **Istio Certified Associate**
- **NGINX Certified Engineer**
- **HashiCorp Consul Associate**

---

*Networking é fundamental para infraestrutura moderna. Dominar conceitos de rede é essencial para implementar soluções escaláveis e confiáveis.*
