[[Tecnologia e serviços da nuvem]]
O **Amazon RDS** é um serviço gerenciado para bancos de dados **relacionais**, permitindo a configuração, operação e escalabilidade de bancos populares com mínima administração. Suporta bancos como **MySQL**, **PostgreSQL**, **MariaDB**, **Oracle**, **Microsoft SQL Server** e **Amazon Aurora**.

### Características Técnicas

- **Bancos de Dados Suportados**:
    
    - **Amazon Aurora**: Versão otimizada para alta performance e escalabilidade do MySQL e PostgreSQL.
    - **MySQL, PostgreSQL, MariaDB**: Opções open-source amplamente usadas.
    - **Oracle e SQL Server**: Suporte para soluções comerciais.
- **Gerenciamento de Infraestrutura**:
    
    - Backup automatizado com **point-in-time recovery**.
    - **Snapshots manuais**: Permite criação e restauração de backups personalizados.
    - Atualizações automáticas e patches de segurança.
- **Alta Disponibilidade e Escalabilidade**:
    
    - **Multi-AZ Deployments**: Réplicas automáticas em outra zona de disponibilidade para failover automático.
    - **Read Replicas**: Melhora a escalabilidade de leitura com réplicas em uma ou mais regiões.
    - Escalabilidade vertical ajustando a capacidade da instância com um clique.
- **Segurança**:
    
    - Integração com **AWS Identity and Access Management (IAM)**.
    - Suporte a **criptografia em repouso** usando KMS e em trânsito usando TLS.
    - Isolamento de rede com **Amazon VPC**.
- **Monitoramento**:
    
    - Integração com **Amazon CloudWatch** para métricas e alarmes.
    - Logs de banco de dados podem ser exportados para **CloudWatch Logs**.

### Informações Extras

- **Amazon Aurora** oferece até 5x a performance do MySQL e 3x do PostgreSQL com escalabilidade automática de armazenamento até 128 TB.
- Os backups automáticos não afetam a performance do banco de dados.
- **Read Replicas** podem ser usadas para failover manual em cenários onde o Multi-AZ não está ativado.
- Suporte a instâncias reservadas com descontos significativos para workloads estáveis.

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **RDS** abrange:

- **Amazon Aurora**: Versão avançada e otimizada de MySQL/PostgreSQL.
- **Multi-AZ**: Alta disponibilidade e recuperação de desastres.
- **Read Replicas**: Para escalar leituras horizontalmente.
- **Backup e Snapshots**: Gerenciamento de backups automáticos e manuais.
- **IAM**: Gerenciamento granular de permissões.

### Custos

- **Modelo de Custos**:
    - Cobrança por hora com base no tipo e tamanho da instância.
    - Custos adicionais para **armazenamento provisionado**, **backups** além do gratuito e **transferência de dados**.
    - **Multi-AZ Deployments** e **Read Replicas** têm custos adicionais.
    - Instâncias reservadas oferecem até 75% de desconto comparado ao preço sob demanda.

### Casos de Uso Comuns no Exame

- Identificar quando usar **Multi-AZ** para alta disponibilidade e **Read Replicas** para escalabilidade.
- Diferenciar **Amazon Aurora** de outros bancos suportados pelo RDS.
- Reconhecer que backups são automáticos e não afetam a performance do banco de dados.
- Selecionar o tipo de instância com base em custos e requisitos de performance.
- Entender os níveis de segurança, como isolamento de rede com **VPC** e criptografia usando **KMS**.