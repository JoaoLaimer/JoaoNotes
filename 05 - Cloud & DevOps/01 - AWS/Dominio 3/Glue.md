[[Tecnologia e serviços da nuvem]]
Serviço gerenciado de ETL (Extração, Transformação e Carga) que facilita a preparação e integração de dados para análises, machine learning e aplicações.
- **ETL Automatizado**: Cria e executa pipelines ETL para transformar e mover dados de diferentes fontes para um destino, como Amazon Redshift, S3 ou RDS.
- **Catálogo de Dados**: Mantém um catálogo centralizado com metadados sobre os dados disponíveis, tornando-os facilmente pesquisáveis e acessíveis.
- **Suporte a Dados Semi-estruturados**: Processa dados em formatos como JSON, Parquet, Avro, ORC e CSV.
- **Compatibilidade com SQL e Python**: Permite criar scripts ETL em Python (PySpark) ou usar consultas SQL para transformar dados.
- **Glue Studio**: Interface gráfica que simplifica o design de pipelines ETL, reduzindo a necessidade de codificação manual.
- **Suporte a Workflows**: Orquestra pipelines complexos com dependências e passos definidos, facilitando automação e monitoramento.
- **Integração com Serviços AWS**: Funciona perfeitamente com S3, Redshift, Athena, DynamoDB e EMR para cenários de big data e analytics.
- **Crawlers Automatizados**: Descobrem automaticamente esquemas de dados e atualizam o catálogo sem intervenção manual.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no tempo de execução dos trabalhos ETL (em minutos), no uso do Glue Data Catalog e crawlers.
    - Glue Studio e Glue DataBrew também têm custos específicos para processamento de dados e recursos consumidos.
    - Camada gratuita disponível para o Glue Data Catalog (1 milhão de objetos e 1 milhão de solicitações por mês durante 1 ano).

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Glue como uma solução para ETL automatizado e centralização de metadados.
- Reconhecer o Glue Data Catalog como um recurso para armazenar metadados de forma pesquisável.
- Compreender como o Glue simplifica a integração de dados em pipelines para analytics e machine learning.