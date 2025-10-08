# 05 - Segurança em Infraestrutura

Esta seção aborda segurança em infraestrutura moderna, cobrindo segurança de containers, redes, sistemas e compliance.

## Índice de Tópicos

### Fundamentos de Segurança
- [[Seguranca-Introducao|Introdução à Segurança]]
- [[Principios-Seguranca|Princípios de Segurança]]
- [[Threat-Modeling|Threat Modeling]]
- [[Vulnerability-Assessment|Avaliação de Vulnerabilidades]]
- [[Security-Frameworks|Frameworks de Segurança]]

### Segurança de Containers
- [[Container-Security|Segurança de Containers]]
- [[Image-Security|Segurança de Imagens]]
- [[Runtime-Security|Segurança em Runtime]]
- [[Container-Scanning|Container Scanning]]
- [[Pod-Security|Pod Security Policies]]

### Segurança de Rede
- [[Network-Security|Segurança de Rede]]
- [[Firewalls|Firewalls e Security Groups]]
- [[Network-Policies|Network Policies]]
- [[VPN-e-Tunneling|VPN e Tunneling]]
- [[DDoS-Protection|Proteção contra DDoS]]

### Identity and Access Management
- [[IAM-Fundamentos|Fundamentos de IAM]]
- [[RBAC|Role-Based Access Control]]
- [[Multi-Factor-Auth|Autenticação Multi-Fator]]
- [[Secrets-Management|Gerenciamento de Secrets]]
- [[Certificate-Management|Gerenciamento de Certificados]]

### Compliance e Auditoria
- [[Compliance-Fundamentos|Fundamentos de Compliance]]
- [[GDPR|GDPR - General Data Protection Regulation]]
- [[SOC2|SOC 2 Compliance]]
- [[ISO27001|ISO 27001]]
- [[PCI-DSS|PCI DSS]]

## Objetivos de Aprendizado

Ao completar esta seção, você estará preparado para:

1. **Compreender Segurança**
   - Entender princípios de segurança
   - Aplicar threat modeling
   - Implementar security frameworks

2. **Segurança de Containers**
   - Implementar container security
   - Configurar image scanning
   - Aplicar runtime security

3. **Segurança de Rede**
   - Configurar network security
   - Implementar firewalls
   - Aplicar network policies

4. **Gerenciar Identidades**
   - Configurar IAM
   - Implementar RBAC
   - Gerenciar secrets

5. **Compliance**
   - Entender frameworks de compliance
   - Implementar auditoria
   - Configurar logging de segurança

## Percurso de Estudo

### Semana 1: Fundamentos
1. [[Seguranca-Introducao|Introdução à Segurança]]
2. [[Principios-Seguranca|Princípios de Segurança]]
3. [[Threat-Modeling|Threat Modeling]]

### Semana 2: Container Security
1. [[Container-Security|Segurança de Containers]]
2. [[Image-Security|Segurança de Imagens]]
3. [[Runtime-Security|Segurança em Runtime]]

### Semana 3: Network Security
1. [[Network-Security|Segurança de Rede]]
2. [[Firewalls|Firewalls e Security Groups]]
3. [[Network-Policies|Network Policies]]

### Semana 4: IAM e Secrets
1. [[IAM-Fundamentos|Fundamentos de IAM]]
2. [[RBAC|Role-Based Access Control]]
3. [[Secrets-Management|Gerenciamento de Secrets]]

### Semana 5: Compliance
1. [[Compliance-Fundamentos|Fundamentos de Compliance]]
2. [[GDPR|GDPR - General Data Protection Regulation]]
3. [[SOC2|SOC 2 Compliance]]

## Ferramentas Essenciais

### Container Security
- **Trivy** - Vulnerability scanner
- **Clair** - Container vulnerability analysis
- **Falco** - Runtime security monitoring
- **OPA Gatekeeper** - Policy enforcement

### Network Security
- **iptables** - Linux firewall
- **nftables** - Modern firewall
- **Calico** - Network security
- **Cilium** - Network security

### IAM e Secrets
- **HashiCorp Vault** - Secrets management
- **AWS IAM** - Identity and access management
- **Azure AD** - Identity management
- **Google Cloud IAM** - Identity management

### Compliance
- **OpenSCAP** - Security compliance
- **Lynis** - Security auditing
- **Docker Bench** - Container security
- **kube-bench** - Kubernetes security

## Projetos Práticos

### Projeto 1: Container Security
**Objetivo**: Implementar segurança em containers
**Tecnologias**: Docker, Trivy, Falco
**Duração**: 1 semana

**Tarefas**:
- Configurar image scanning
- Implementar runtime monitoring
- Configurar security policies
- Implementar secrets management

### Projeto 2: Network Security
**Objetivo**: Configurar segurança de rede
**Tecnologias**: Kubernetes, Calico, Network Policies
**Duração**: 1 semana

**Tarefas**:
- Configurar network policies
- Implementar service mesh
- Configurar ingress security
- Implementar DDoS protection

### Projeto 3: Compliance Setup
**Objetivo**: Implementar compliance
**Tecnologias**: Vault, Audit logging, Compliance tools
**Duração**: 2 semanas

**Tarefas**:
- Configurar audit logging
- Implementar compliance scanning
- Configurar reporting
- Implementar remediation

## Princípios de Segurança

### Defense in Depth
- **Múltiplas camadas** de segurança
- **Redundância** em controles
- **Diversidade** de ferramentas
- **Fail-safe** defaults

### Zero Trust
- **Never trust, always verify**
- **Least privilege** access
- **Continuous verification**
- **Micro-segmentation**

### Security by Design
- **Security** desde o início
- **Threat modeling** contínuo
- **Secure coding** practices
- **Regular security** reviews

## Frameworks de Segurança

### NIST Cybersecurity Framework
- **Identify** - Identificar riscos
- **Protect** - Implementar controles
- **Detect** - Monitorar ameaças
- **Respond** - Responder a incidentes
- **Recover** - Recuperar de incidentes

### OWASP Top 10
- **Injection** - Injection attacks
- **Broken Authentication** - Autenticação quebrada
- **Sensitive Data Exposure** - Exposição de dados
- **XML External Entities** - XXE attacks
- **Broken Access Control** - Controle de acesso

### CIS Controls
- **Basic** - Controles básicos
- **Foundational** - Controles fundamentais
- **Organizational** - Controles organizacionais

## Próximos Passos

Após dominar segurança, você estará preparado para:

1. **[[06-networking/README|Networking]]** - Segurança de rede avançada
2. **[[07-automacao/README|Automação]]** - Automação de segurança
3. **[[08-storage/README|Storage]]** - Segurança de armazenamento

## Recursos Adicionais

### Documentação Oficial
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [OWASP Documentation](https://owasp.org/)
- [CIS Controls](https://www.cisecurity.org/controls/)

### Livros Recomendados
- "The Web Application Hacker's Handbook" - Dafydd Stuttard
- "Security Engineering" - Ross Anderson
- "Threat Modeling" - Adam Shostack

### Certificações
- **CISSP** - Certified Information Systems Security Professional
- **CISM** - Certified Information Security Manager
- **CISA** - Certified Information Systems Auditor

---

*Segurança é fundamental para infraestrutura moderna. Dominar princípios de segurança é essencial para proteger sistemas e dados.*
