[[Tecnologia e serviços da nuvem]]
Serviço gerenciado de data warehouse em nuvem, projetado para armazenar e analisar grandes volumes de dados estruturados e semi-estruturados de forma rápida e escalável.
- **Alta Performance**: Utiliza técnicas como armazenamento em colunas, compressão de dados e paralelismo massivo (MPP) para consultas rápidas em grandes conjuntos de dados.
- **Compatibilidade com SQL**: Suporte completo para SQL, facilitando o uso por analistas e engenheiros de dados.
- **Escalabilidade Flexível**: Permite ajustar a capacidade automaticamente com o **Redshift Spectrum** para consultas em dados armazenados no Amazon S3 sem a necessidade de carregar os dados no data warehouse.
- **Clusters Gerenciados**: Facilita o gerenciamento de clusters, incluindo backups automáticos, atualizações e criptografia.
- **Suporte a Dados Semi-estruturados**: Capacidade de processar JSON, Avro, ORC e Parquet diretamente no Redshift Spectrum.
- **Integração com Outros Serviços AWS**: Funciona bem com S3, Glue, Athena, Kinesis, e QuickSight para fluxos de trabalho de ETL, consultas e visualização de dados.
- **Carga Automática de Dados**: Integração nativa com AWS Data Pipeline e ferramentas de ETL como Glue para carregar e transformar dados.
- **Redshift Serverless**: Permite executar cargas de trabalho analíticas sem a necessidade de gerenciar clusters.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos variam com base no tamanho e tipo de nó do cluster, armazenamento e transferência de dados.
    - **Reserved Instances**: Descontos para compromissos de 1 ou 3 anos, ideais para workloads previsíveis.
    - **Redshift Serverless**: Cobrança baseada no uso por segundo de computação e armazenamento.
- **Camada Gratuita**:
    - 2 meses gratuitos para novos usuários, com 750 horas por mês em um nó DC2.Large e 160 GB de armazenamento no S3.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon Redshift como uma solução para data warehousing e análise de grandes volumes de dados.
- Reconhecer o Redshift Spectrum como um recurso para consultar dados diretamente no S3.
- Compreender os benefícios do modelo Serverless para reduzir complexidade operacional.