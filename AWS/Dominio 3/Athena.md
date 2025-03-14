[[Tecnologia e serviços da nuvem]]
Amazon Athena é um serviço interativo de consulta que facilita a análise de dados no Amazon [[S3 (Simple Storage Service)]] usando SQL. Athena é completamente gerenciado, sem necessidade de infraestrutura, e permite consultar dados em formatos como CSV, JSON, Parquet, ORC e Avro, entre outros.
- **Consulta SQL**: Athena usa SQL padrão para consultas, tornando-o acessível a qualquer pessoa familiarizada com SQL.
- **Análise de Dados no S3**: Não é necessário mover ou carregar dados para outros serviços; você pode executar consultas diretamente nos dados armazenados no Amazon S3.
- **Escalabilidade**: O serviço se adapta automaticamente ao volume de dados, escalando conforme necessário, sem necessidade de gerenciamento de infraestrutura.
- **Formato de Dados Otimizado**: Funciona bem com dados em formatos como Parquet e ORC, que são colunarmente otimizados, melhorando a performance de consulta e reduzindo custos.
- **Integração com Glue Data Catalog**: Athena pode usar o AWS Glue Data Catalog para gerenciar metadados e facilitar a descoberta de dados no S3.
- **Armazenamento Econômico**: Não há custo fixo de armazenamento em Athena; você paga apenas pelas consultas realizadas, com base no volume de dados escaneado.
- **Segurança**: Suporta controle de acesso via AWS IAM, criptografia de dados em trânsito e em repouso, além de integração com AWS CloudTrail para auditoria de consultas.
- **Consultas Ad-Hoc**: Ideal para análise ad-hoc de grandes volumes de dados sem a necessidade de provisionamento de servidores ou clusters.
- **Conectividade com BI**: Pode ser integrado com ferramentas de BI como Amazon QuickSight ou ferramentas de terceiros para visualização de dados.
**Modelo de Preços**:

- **Pague pelo uso**:
    - O preço é baseado no volume de dados escaneados por consulta.
    - Redução de custos ao usar formatos de dados otimizados como Parquet e ORC, pois são colunarmente comprimidos, diminuindo o volume de dados escaneados.
    - Não há custo fixo ou cobrança por armazenamento; os dados armazenados no S3 são cobrados conforme as tarifas padrão do S3.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- **Identificar o Amazon Athena** como uma solução para consultas SQL rápidas e econômicas diretamente em dados armazenados no S3.
- **Compreender o modelo de preços**, que se baseia na quantidade de dados escaneados, e como otimizar consultas com formatos de dados comprimidos.
- **Reconhecer o papel do Athena em Data Lakes**, permitindo análise de dados sem a necessidade de mover ou transformar dados antes de consultá-los.