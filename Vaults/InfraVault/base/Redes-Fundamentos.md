# Redes de Computadores - Fundamentos

As redes de computadores são a base da infraestrutura moderna. Compreender como funcionam é essencial para trabalhar com containers, Kubernetes, cloud computing e DevOps.

## 🎯 O que são Redes de Computadores?

Uma rede de computadores é um conjunto de dispositivos interconectados que podem trocar dados e compartilhar recursos. Na infraestrutura moderna, as redes são fundamentais para comunicação entre serviços, containers e sistemas distribuídos.

## 📡 Modelo OSI (Open Systems Interconnection)

O modelo OSI é um framework conceitual que divide as funções de rede em 7 camadas:

### Camada 7 - Aplicação
- **Função**: Interface entre aplicação e rede
- **Protocolos**: HTTP, HTTPS, FTP, SMTP, DNS
- **Exemplos**: Navegadores, clientes de email

### Camada 6 - Apresentação
- **Função**: Formatação e criptografia de dados
- **Protocolos**: SSL/TLS, JPEG, MPEG
- **Exemplos**: Criptografia, compressão

### Camada 5 - Sessão
- **Função**: Gerenciamento de sessões
- **Protocolos**: NetBIOS, RPC
- **Exemplos**: Sessões de login, comunicação entre processos

### Camada 4 - Transporte
- **Função**: Controle de fluxo e confiabilidade
- **Protocolos**: TCP, UDP
- **Exemplos**: Comunicação confiável, streaming

### Camada 3 - Rede
- **Função**: Roteamento e endereçamento
- **Protocolos**: IP, ICMP, OSPF
- **Exemplos**: Roteadores, endereços IP

### Camada 2 - Enlace
- **Função**: Controle de acesso ao meio
- **Protocolos**: Ethernet, WiFi, PPP
- **Exemplos**: Switches, placas de rede

### Camada 1 - Física
- **Função**: Transmissão de bits
- **Protocolos**: Ethernet, WiFi, Bluetooth
- **Exemplos**: Cabos, antenas, sinais

## 🌐 Modelo TCP/IP

O modelo TCP/IP é mais prático e amplamente usado:

### Camada 4 - Aplicação
- **Protocolos**: HTTP, HTTPS, FTP, SMTP, DNS, SSH
- **Função**: Serviços de aplicação

### Camada 3 - Transporte
- **Protocolos**: TCP, UDP
- **Função**: Controle de fluxo e confiabilidade

### Camada 2 - Internet
- **Protocolos**: IP, ICMP, ARP
- **Função**: Roteamento e endereçamento

### Camada 1 - Acesso à Rede
- **Protocolos**: Ethernet, WiFi, PPP
- **Função**: Transmissão física

## 🔌 Protocolos Essenciais

### HTTP/HTTPS
- **HTTP (HyperText Transfer Protocol)**
  - Porta: 80
  - Características: Stateless, request/response
  - Uso: Web browsing, APIs REST

- **HTTPS (HTTP Secure)**
  - Porta: 443
  - Características: HTTP + SSL/TLS
  - Uso: Web seguro, APIs seguras

### TCP vs UDP
- **TCP (Transmission Control Protocol)**
  - Características: Orientado a conexão, confiável
  - Uso: Web, email, transferência de arquivos
  - Vantagens: Confiabilidade, controle de fluxo
  - Desvantagens: Overhead, latência

- **UDP (User Datagram Protocol)**
  - Características: Sem conexão, não confiável
  - Uso: Streaming, DNS, jogos online
  - Vantagens: Baixa latência, baixo overhead
  - Desvantagens: Sem garantia de entrega

### DNS (Domain Name System)
- **Função**: Resolver nomes para endereços IP
- **Tipos de Registros**:
  - **A**: IPv4 address
  - **AAAA**: IPv6 address
  - **CNAME**: Alias
  - **MX**: Mail exchange
  - **TXT**: Text records

## 🌍 Endereçamento IP

### IPv4
- **Formato**: 4 octetos (0-255)
- **Exemplo**: 192.168.1.1
- **Classes**:
  - **Classe A**: 1.0.0.0 - 126.255.255.255
  - **Classe B**: 128.0.0.0 - 191.255.255.255
  - **Classe C**: 192.0.0.0 - 223.255.255.255

### IPv6
- **Formato**: 8 grupos de 4 hexadecimais
- **Exemplo**: 2001:0db8:85a3:0000:0000:8a2e:0370:7334
- **Vantagens**: Maior espaço de endereços, melhor segurança

### Subnetting
- **CIDR (Classless Inter-Domain Routing)**
- **Exemplo**: 192.168.1.0/24
- **Máscara**: 255.255.255.0
- **Hosts**: 254 (2^8 - 2)

## 🔧 Dispositivos de Rede

### Switches
- **Função**: Conectar dispositivos na mesma rede
- **Características**: Learning, forwarding, filtering
- **Tipos**: Unmanaged, managed, layer 3

### Roteadores
- **Função**: Conectar redes diferentes
- **Características**: Roteamento, NAT, firewall
- **Protocolos**: OSPF, BGP, RIP

### Load Balancers
- **Função**: Distribuir tráfego entre servidores
- **Tipos**: Layer 4, Layer 7
- **Algoritmos**: Round-robin, least connections, weighted

## 🔒 Segurança de Rede

### Firewalls
- **Função**: Controlar tráfego de rede
- **Tipos**: Stateless, stateful, next-generation
- **Regras**: Allow, deny, log

### VPN (Virtual Private Network)
- **Função**: Conexão segura através de rede pública
- **Tipos**: Site-to-site, remote access
- **Protocolos**: IPsec, OpenVPN, WireGuard

### SSL/TLS
- **Função**: Criptografia de dados em trânsito
- **Certificados**: X.509, CA, self-signed
- **Versões**: TLS 1.2, TLS 1.3

## 📊 Monitoramento de Rede

### Métricas Importantes
- **Bandwidth**: Largura de banda utilizada
- **Latency**: Tempo de resposta
- **Packet Loss**: Perda de pacotes
- **Throughput**: Taxa de transferência

### Ferramentas de Monitoramento
- **ping**: Teste de conectividade
- **traceroute**: Rastreamento de rota
- **netstat**: Estatísticas de rede
- **tcpdump**: Captura de pacotes
- **Wireshark**: Análise de protocolos

## 🐳 Redes em Containers

### Docker Networking
- **Bridge**: Rede padrão do Docker
- **Host**: Usa rede do host
- **Overlay**: Rede distribuída
- **Macvlan**: Interface MAC virtual

### Kubernetes Networking
- **Pod Network**: Comunicação entre pods
- **Service Network**: Descoberta de serviços
- **Ingress**: Entrada externa
- **CNI**: Container Network Interface

## ☁️ Redes em Cloud

### VPC (Virtual Private Cloud)
- **Função**: Rede privada na cloud
- **Características**: Isolamento, controle de tráfego
- **Exemplos**: AWS VPC, Azure VNet, GCP VPC

### CDN (Content Delivery Network)
- **Função**: Distribuir conteúdo globalmente
- **Benefícios**: Baixa latência, alta disponibilidade
- **Exemplos**: CloudFront, Azure CDN, CloudFlare

## 🛠️ Comandos Essenciais

### Teste de Conectividade
```bash
# Ping
ping google.com

# Traceroute
traceroute google.com

# Telnet
telnet hostname port
```

### Configuração de Rede
```bash
# Ver interfaces
ip addr show

# Configurar IP
ip addr add 192.168.1.100/24 dev eth0

# Ver rotas
ip route show

# Adicionar rota
ip route add 192.168.2.0/24 via 192.168.1.1
```

### Monitoramento
```bash
# Estatísticas de rede
netstat -i

# Conexões ativas
netstat -tulpn

# Captura de pacotes
tcpdump -i eth0

# Monitor de tráfego
iftop
```

## 🎯 Próximos Passos

Após dominar os fundamentos de redes, você estará preparado para:

1. **[[Load-Balancing|Load Balancing]]** - Distribuição de carga
2. **[[DNS-e-Resolucao|DNS e Resolução]]** - Sistema de nomes
3. **[[Firewalls-e-Seguranca|Firewalls e Segurança]]** - Segurança de rede

## 📚 Recursos Adicionais

### Documentação Oficial
- [RFC Standards](https://tools.ietf.org/rfc/)
- [IEEE Standards](https://standards.ieee.org/)
- [IETF Documentation](https://www.ietf.org/)

### Livros Recomendados
- "Computer Networks" - Andrew Tanenbaum
- "TCP/IP Illustrated" - W. Richard Stevens
- "Network Security Essentials" - William Stallings

### Cursos Online
- **Coursera** - Computer Networks
- **edX** - Introduction to Networking
- **Linux Academy** - Network fundamentals

### Ferramentas
- **Wireshark** - Protocol analyzer
- **tcpdump** - Packet capture
- **nmap** - Network scanner
- **netstat** - Network statistics

---

*O conhecimento sólido de redes é fundamental para trabalhar com infraestrutura moderna. Dedique tempo para entender os protocolos e praticar com ferramentas de rede.*
