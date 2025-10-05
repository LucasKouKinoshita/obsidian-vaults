# 08 - Armazenamento e Persistência

Esta seção aborda armazenamento e persistência em infraestrutura moderna, cobrindo storage classes, backup strategies e gerenciamento de dados.

## Índice de Tópicos

### Fundamentos de Storage
- [[Storage-Introducao|Introdução ao Storage]]
- [[Storage-Types|Tipos de Storage]]
- [[Storage-Protocols|Protocolos de Storage]]
- [[RAID|RAID e Redundância]]
- [[Storage-Performance|Performance de Storage]]

### Kubernetes Storage
- [[PersistentVolumes|PersistentVolumes]]
- [[StorageClasses|Storage Classes]]
- [[Volume-Claims|PersistentVolumeClaims]]
- [[Volume-Snapshots|Volume Snapshots]]
- [[Storage-Provisioning|Storage Provisioning]]

### Cloud Storage
- [[AWS-S3|AWS S3]]
- [[Azure-Blob|Azure Blob Storage]]
- [[GCP-Cloud-Storage|Google Cloud Storage]]
- [[Object-Storage|Object Storage]]
- [[Block-Storage|Block Storage]]

### Backup e Recovery
- [[Backup-Strategies|Estratégias de Backup]]
- [[Disaster-Recovery|Disaster Recovery]]
- [[Backup-Tools|Ferramentas de Backup]]
- [[Recovery-Testing|Testing de Recovery]]
- [[Backup-Automation|Automação de Backup]]

### Distributed Storage
- [[Ceph|Ceph - Distributed Storage]]
- [[GlusterFS|GlusterFS]]
- [[MinIO|MinIO - Object Storage]]
- [[Rook|Rook - Storage Orchestration]]
- [[Longhorn|Longhorn - Kubernetes Storage]]

## Objetivos de Aprendizado

Ao completar esta seção, você estará preparado para:

1. **Compreender Storage**
   - Entender tipos de storage
   - Diferenciar block, file e object storage
   - Compreender performance e custos

2. **Dominar Kubernetes Storage**
   - Configurar PersistentVolumes
   - Implementar StorageClasses
   - Gerenciar VolumeClaims

3. **Trabalhar com Cloud Storage**
   - Configurar S3, Blob Storage, Cloud Storage
   - Implementar object storage
   - Gerenciar lifecycle policies

4. **Implementar Backup**
   - Configurar estratégias de backup
   - Implementar disaster recovery
   - Automatizar backup

5. **Gerenciar Distributed Storage**
   - Configurar Ceph
   - Implementar GlusterFS
   - Gerenciar MinIO

## Percurso de Estudo

### Semana 1: Storage Fundamentals
1. [[Storage-Introducao|Introdução ao Storage]]
2. [[Storage-Types|Tipos de Storage]]
3. [[Storage-Protocols|Protocolos de Storage]]

### Semana 2: Kubernetes Storage
1. [[PersistentVolumes|PersistentVolumes]]
2. [[StorageClasses|Storage Classes]]
3. [[Volume-Claims|PersistentVolumeClaims]]

### Semana 3: Cloud Storage
1. [[AWS-S3|AWS S3]]
2. [[Azure-Blob|Azure Blob Storage]]
3. [[GCP-Cloud-Storage|Google Cloud Storage]]

### Semana 4: Backup e Recovery
1. [[Backup-Strategies|Estratégias de Backup]]
2. [[Disaster-Recovery|Disaster Recovery]]
3. [[Backup-Tools|Ferramentas de Backup]]

### Semana 5: Distributed Storage
1. [[Ceph|Ceph - Distributed Storage]]
2. [[GlusterFS|GlusterFS]]
3. [[MinIO|MinIO - Object Storage]]

## Ferramentas Essenciais

### Kubernetes Storage
- **Rook** - Storage orchestration
- **Longhorn** - Kubernetes storage
- **OpenEBS** - Container storage
- **Portworx** - Enterprise storage

### Cloud Storage
- **AWS S3** - Object storage
- **Azure Blob** - Object storage
- **Google Cloud Storage** - Object storage
- **DigitalOcean Spaces** - Object storage

### Backup Tools
- **Velero** - Kubernetes backup
- **Restic** - Backup tool
- **BorgBackup** - Deduplicating backup
- **Duplicity** - Encrypted backup

### Distributed Storage
- **Ceph** - Distributed storage
- **GlusterFS** - Distributed file system
- **MinIO** - Object storage
- **SeaweedFS** - Distributed storage

## Projetos Práticos

### Projeto 1: Kubernetes Storage
**Objetivo**: Configurar storage no Kubernetes
**Tecnologias**: Kubernetes, Rook, Ceph
**Duração**: 1 semana

**Tarefas**:
- Instalar Rook
- Configurar Ceph
- Criar StorageClasses
- Implementar PersistentVolumes

### Projeto 2: Cloud Storage Setup
**Objetivo**: Configurar cloud storage
**Tecnologias**: AWS S3, Azure Blob, GCP Storage
**Duração**: 1 semana

**Tarefas**:
- Configurar buckets
- Implementar lifecycle policies
- Configurar access controls
- Implementar monitoring

### Projeto 3: Backup Strategy
**Objetivo**: Implementar estratégia de backup
**Tecnologias**: Velero, Restic, Kubernetes
**Duração**: 1 semana

**Tarefas**:
- Configurar Velero
- Implementar backup schedules
- Configurar disaster recovery
- Testar recovery

## Conceitos Avançados

### Storage Performance
- **IOPS** - Input/Output Operations Per Second
- **Throughput** - Data transfer rate
- **Latency** - Response time
- **Bandwidth** - Data transfer capacity

### Data Lifecycle
- **Hot Storage** - Frequently accessed
- **Warm Storage** - Occasionally accessed
- **Cold Storage** - Rarely accessed
- **Archive Storage** - Long-term storage

### Storage Security
- **Encryption at Rest** - Criptografia em repouso
- **Encryption in Transit** - Criptografia em trânsito
- **Access Control** - Controle de acesso
- **Audit Logging** - Log de auditoria

## Próximos Passos

Após dominar storage, você estará preparado para:

1. **[[09-cicd/README|CI/CD]]** - Storage em pipelines
2. **[[10-observabilidade/README|Observabilidade]]** - Monitoramento de storage
3. **[[05-seguranca/README|Segurança]]** - Segurança de dados

## Recursos Adicionais

### Documentação Oficial
- [Kubernetes Storage Documentation](https://kubernetes.io/docs/concepts/storage/)
- [Ceph Documentation](https://docs.ceph.com/)
- [MinIO Documentation](https://docs.min.io/)

### Livros Recomendados
- "Storage Area Networks" - Marc Farley
- "Distributed Systems" - Maarten van Steen
- "Kubernetes Storage" - Kubernetes Community

### Certificações
- **Ceph Certified Associate**
- **Kubernetes Storage Specialist**
- **Cloud Storage Professional**

---

*Storage é fundamental para infraestrutura moderna. Dominar conceitos de armazenamento é essencial para implementar soluções confiáveis e escaláveis.*
