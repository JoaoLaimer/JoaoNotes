[[Tecnologia e serviços da nuvem]]
AWS Database Migration Service (DMS) é um serviço gerenciado que facilita a migração de bancos de dados entre ambientes locais, outras nuvens e a AWS. Ele suporta migrações homogêneas (ex.: Oracle para Oracle) e heterogêneas (ex.: Oracle para Aurora).
- **Suporte Multi-Engine**: Compatível com bancos de dados relacionais (ex.: Oracle, MySQL, PostgreSQL, SQL Server) e NoSQL (ex.: MongoDB, DynamoDB).
- **Migrações Homogêneas e Heterogêneas**: Permite transferir dados entre bancos de dados com diferentes estruturas ou mecanismos.
- **Replicação Contínua**: Suporte para replicação contínua de dados, permitindo manter o banco de origem sincronizado com o destino durante a migração.
- **Alta Disponibilidade**: Suporte a failover automático para garantir que a migração não seja interrompida em caso de falha.
- **Transformação de Dados**: Permite alterações simples no esquema ou formato dos dados durante a migração.'
- **Monitoramento de Migração**: Integração com Amazon CloudWatch para rastrear progresso, status e métricas detalhadas de desempenho.
- **Escalabilidade Automática**: Ajusta recursos automaticamente para lidar com diferentes volumes de dados durante a migração.
- **Segurança**: Criptografia de dados em trânsito e controle de acesso detalhado com AWS IAM.
- **Integração com SCT**: Trabalha em conjunto com o **AWS Schema Conversion Tool** para simplificar migrações heterogêneas ao converter esquemas e procedimentos armazenados.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no tempo de execução da instância de replicação usada no processo de migração.
    - Custos adicionais para armazenamento, transferências de dados e uso do AWS Schema Conversion Tool (SCT).

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS DMS como uma solução para migração de bancos de dados entre ambientes locais, outras nuvens e a AWS.
- Reconhecer o suporte a migrações homogêneas e heterogêneas como um diferencial importante.
- Compreender como ele reduz a complexidade e o tempo necessário para migrações de dados.