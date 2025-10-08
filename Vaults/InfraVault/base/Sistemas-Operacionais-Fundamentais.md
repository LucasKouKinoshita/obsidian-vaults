# Sistemas Operacionais - Fundamentos

Os sistemas operacionais são a base de toda infraestrutura de software. Compreender como funcionam é essencial para trabalhar com containers, virtualização e cloud computing.

## 🎯 O que é um Sistema Operacional?

Um sistema operacional (SO) é um software que atua como intermediário entre o hardware do computador e os programas de aplicação. Ele gerencia recursos do sistema e fornece serviços comuns para programas de computador.

### Componentes Principais

#### 1. Kernel
- **Definição**: Núcleo do sistema operacional
- **Funções**: Gerenciamento de processos, memória, dispositivos
- **Tipos**: Monolítico, Microkernel, Híbrido

#### 2. Shell
- **Definição**: Interface entre usuário e kernel
- **Tipos**: Command Line Interface (CLI), Graphical User Interface (GUI)
- **Exemplos**: Bash, Zsh, PowerShell, Windows Explorer

#### 3. Sistema de Arquivos
- **Definição**: Método de armazenamento e organização de dados
- **Funções**: Gerenciamento de arquivos, diretórios, permissões
- **Exemplos**: ext4, NTFS, APFS, ZFS

## 🖥️ Tipos de Sistemas Operacionais

### Sistemas Monolíticos
- **Características**: Todo o SO em um único espaço de endereçamento
- **Exemplos**: Linux, Windows (parcialmente)
- **Vantagens**: Performance alta, comunicação direta
- **Desvantagens**: Dificuldade de manutenção, instabilidade

### Sistemas Microkernel
- **Características**: Kernel mínimo, serviços em user space
- **Exemplos**: QNX, Minix
- **Vantagens**: Modularidade, estabilidade
- **Desvantagens**: Performance menor, complexidade

### Sistemas Híbridos
- **Características**: Combinação de monolítico e microkernel
- **Exemplos**: macOS, Windows NT
- **Vantagens**: Balance entre performance e modularidade

## 🔧 Funções Principais

### 1. Gerenciamento de Processos
- **Criação e destruição** de processos
- **Suspensão e retomada** de execução
- **Sincronização** entre processos
- **Comunicação** interprocessos (IPC)

### 2. Gerenciamento de Memória
- **Alocação** de memória para processos
- **Proteção** de memória entre processos
- **Virtualização** de memória
- **Paginação** e segmentação

### 3. Gerenciamento de Arquivos
- **Criação e exclusão** de arquivos
- **Organização** em diretórios
- **Controle de acesso** e permissões
- **Backup** e recuperação

### 4. Gerenciamento de Dispositivos
- **Drivers** de dispositivos
- **Abstração** de hardware
- **Gerenciamento de interrupções**
- **Plug and Play**

## 🐧 Linux - Sistema Operacional Dominante em Infraestrutura

### Por que Linux?
- **Open Source**: Código aberto e gratuito
- **Estabilidade**: Alta confiabilidade
- **Performance**: Otimizado para servidores
- **Flexibilidade**: Altamente customizável
- **Comunidade**: Suporte ativo da comunidade

### Distribuições Principais

#### Red Hat Family
- **Red Hat Enterprise Linux (RHEL)**
  - Foco: Enterprise
  - Suporte: Comercial
  - Uso: Servidores corporativos

- **CentOS**
  - Foco: Comunidade
  - Base: RHEL sem suporte comercial
  - Uso: Laboratórios e desenvolvimento

- **Fedora**
  - Foco: Inovação
  - Ciclo: Release rápido
  - Uso: Desktop e desenvolvimento

#### Debian Family
- **Debian**
  - Foco: Estabilidade
  - Filosofia: Software livre
  - Uso: Servidores e desktop

- **Ubuntu**
  - Foco: Usabilidade
  - Base: Debian
  - Uso: Desktop e servidores

#### SUSE Family
- **SUSE Linux Enterprise**
  - Foco: Enterprise
  - Suporte: Comercial
  - Uso: Servidores corporativos

### Comandos Essenciais do Linux

#### Navegação
```bash
# Listar arquivos
ls -la

# Mudar diretório
cd /path/to/directory

# Mostrar diretório atual
pwd

# Criar diretório
mkdir new_directory

# Remover arquivo/diretório
rm file.txt
rm -rf directory
```

#### Gerenciamento de Processos
```bash
# Listar processos
ps aux

# Monitorar processos em tempo real
htop

# Matar processo
kill -9 PID

# Executar em background
command &
```

#### Gerenciamento de Arquivos
```bash
# Copiar arquivo
cp source.txt destination.txt

# Mover/renomear arquivo
mv old_name.txt new_name.txt

# Criar link simbólico
ln -s target link_name

# Verificar permissões
ls -l file.txt
```

#### Redes
```bash
# Verificar interfaces de rede
ip addr show

# Testar conectividade
ping google.com

# Verificar portas abertas
netstat -tulpn

# Download de arquivo
wget https://example.com/file.zip
curl -O https://example.com/file.zip
```

## 🔒 Permissões e Segurança

### Sistema de Permissões Unix/Linux
- **Owner (u)**: Dono do arquivo
- **Group (g)**: Grupo do arquivo
- **Others (o)**: Outros usuários

### Tipos de Permissão
- **Read (r)**: Leitura (4)
- **Write (w)**: Escrita (2)
- **Execute (x)**: Execução (1)

### Exemplos
```bash
# Arquivo com permissões rwxr-xr-x
# Owner: read, write, execute
# Group: read, execute
# Others: read, execute

# Alterar permissões
chmod 755 file.txt
chmod u+x file.txt

# Alterar dono
chown user:group file.txt
```

## 📊 Monitoramento do Sistema

### Comandos de Monitoramento
```bash
# Uso de CPU
top
htop

# Uso de memória
free -h

# Uso de disco
df -h
du -sh /path

# Estatísticas de I/O
iostat

# Logs do sistema
journalctl -f
tail -f /var/log/syslog
```

### Métricas Importantes
- **CPU Usage**: Percentual de uso do processador
- **Memory Usage**: Uso de RAM e swap
- **Disk I/O**: Operações de entrada/saída
- **Network I/O**: Tráfego de rede
- **Load Average**: Carga média do sistema

## 🛠️ Ferramentas Essenciais

### Editores de Texto
- **Vim/Neovim**: Editor modal poderoso
- **Nano**: Editor simples para iniciantes
- **Emacs**: Editor extensível

### Utilitários de Sistema
- **grep**: Busca em arquivos
- **awk**: Processamento de texto
- **sed**: Editor de stream
- **find**: Busca de arquivos
- **tar**: Compactação de arquivos

### Gerenciamento de Pacotes
```bash
# Ubuntu/Debian
apt update
apt install package_name
apt remove package_name

# CentOS/RHEL
yum install package_name
yum remove package_name

# Arch Linux
pacman -S package_name
pacman -R package_name
```

## 🎯 Próximos Passos

Após dominar os fundamentos de sistemas operacionais, você estará preparado para:

1. **[[Processos-e-Threads|Processos e Threads]]** - Entender como o SO gerencia execução
2. **[[Gerenciamento-de-Memoria|Gerenciamento de Memória]]** - Compreender alocação e virtualização
3. **[[Sistema-de-Arquivos|Sistema de Arquivos]]** - Dominar organização e permissões

## 📚 Recursos Adicionais

### Documentação
- [Linux Documentation](https://www.kernel.org/doc/)
- [GNU Coreutils](https://www.gnu.org/software/coreutils/)
- [Bash Reference Manual](https://www.gnu.org/software/bash/manual/)

### Livros Recomendados
- "Operating System Concepts" - Silberschatz
- "Linux System Administration" - Tom Adelstein
- "UNIX and Linux System Administration Handbook"

### Cursos Online
- **Linux Academy** - Linux fundamentals
- **Coursera** - Operating Systems
- **edX** - Introduction to Linux

---

*O conhecimento sólido de sistemas operacionais é fundamental para trabalhar com infraestrutura moderna. Dedique tempo para praticar comandos e entender os conceitos apresentados.*
