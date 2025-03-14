[[Tecnologia e serviços da nuvem]]
Amazon DynamoDB é um banco de dados NoSQL gerenciado que fornece armazenamento rápido e flexível para aplicações que requerem baixa latência e alta escalabilidade. Ele é ideal para workloads com alta demanda de leitura e gravação em tempo real.
- **Modelo NoSQL**: Usa um esquema flexível baseado em tabelas, projetado para suportar estruturas de dados como chave-valor e documentos.
- **Escalabilidade Automática**: Ajusta a capacidade de leitura e gravação dinamicamente com o recurso de **Auto Scaling**.
- **Desempenho de Baixa Latência**: Respostas em milissegundos, mesmo em altas cargas de trabalho.
- **Modo de Capacidade Flexível**:
    - **Sob Demanda**: Cobra apenas pelas leituras e gravações realizadas.
    - **Capacidade Provisionada (Reservada)**: Permite reservar capacidade para cargas de trabalho previsíveis.
- **Alta Disponibilidade**: Replicação automática de dados entre múltiplas Regiões com **DynamoDB Global Tables** para garantir baixa latência global e resiliência.
- **Indexação Secundária**: Suporte para índices globais e locais que melhoram consultas sem impactar a tabela principal.
- **Suporte a Transações**: Permite operações ACID (Atomicidade, Consistência, Isolamento, Durabilidade) para manipulações complexas de dados.
- **Backup e Recuperação**: Oferece backups contínuos com recuperação point-in-time e backups sob demanda.
- **Segurança Integrada**: Suporte a criptografia de dados em repouso, controle de acesso detalhado com IAM e integração com VPC para isolamento de rede.
- **Integração com Outros Serviços AWS**: Funciona bem com Lambda, API Gateway, Glue e Kinesis para construir aplicações serverless e pipelines de dados.
- **Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada em leituras e gravações realizadas (modo Sob Demanda) ou capacidade provisionada.
    - Custos adicionais para armazenamento, backups, replicação global e transferências de dados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o DynamoDB como uma solução para bancos de dados NoSQL de alta performance.
- Reconhecer a escalabilidade automática e os modos de capacidade como recursos importantes.
- Compreender o suporte para replicação global e transações ACID como diferenciais para workloads críticas.