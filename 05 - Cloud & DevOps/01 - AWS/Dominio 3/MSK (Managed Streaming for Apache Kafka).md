[[Tecnologia e serviços da nuvem]]
Amazon MSK é um serviço gerenciado que facilita a execução de clusters Apache Kafka para transmitir e processar dados em tempo real. Ele automatiza tarefas administrativas, como provisionamento, manutenção de hardware e atualizações de software, permitindo que você foque no desenvolvimento de aplicativos.
- **Compatibilidade Completa com Kafka**: Suporte nativo a APIs e ferramentas Apache Kafka, facilitando a migração de aplicações existentes.
- **Alta Disponibilidade**: Suporte para replicação entre zonas de disponibilidade (AZs) para maior resiliência e confiabilidade.
- **Segurança Integrada**: Oferece criptografia de dados em trânsito e em repouso, autenticação SASL/SCRAM e controle de acesso com IAM.
- **Escalabilidade Automática**: Ajusta os recursos automaticamente para atender a cargas de trabalho variáveis.
- **Monitoramento Simplificado**: Integração com Amazon CloudWatch, AWS CloudTrail e métricas Kafka nativas para rastrear o desempenho do cluster.
- **Gerenciamento Automatizado**: Automatiza tarefas como provisionamento, recuperação de falhas, backups e upgrades de software.
- **Integração com Serviços AWS**: Funciona com AWS Lambda, Kinesis, Glue, S3, e Redshift para criar pipelines de dados robustos.
- **Streams de Dados Duráveis**: Suporte para retenção de dados com logs distribuídos, garantindo disponibilidade para leitura e reprocessamento.
**Ideal para**:

- Empresas que processam grandes volumes de dados em tempo real, como logs, cliques, sensores IoT e eventos de aplicativos.
- Ambientes que precisam de soluções resilientes e seguras para streaming de dados distribuídos.
- Organizações que desejam gerenciar menos infraestrutura e focar no desenvolvimento de pipelines de dados.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no número e tipo de instâncias de brokers, armazenamento provisionado, transferência de dados e taxas adicionais por throughput (GB/s).

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o MSK como uma solução gerenciada para execução de clusters Apache Kafka.
- Reconhecer a integração com outros serviços AWS, como Lambda e S3, para criar pipelines de dados.
- Compreender como o MSK reduz o esforço operacional automatizando tarefas administrativas e aumentando a resiliência.