[[Tecnologia e serviços da nuvem]]
Amazon EMR é um serviço gerenciado que facilita o processamento, análise e transformação de grandes volumes de dados usando frameworks de big data, como Apache Hadoop, Spark, Hive, Presto, e outros.
- **Frameworks de Big Data**: Suporte a ferramentas populares como Hadoop, Spark, HBase, Hive, Presto e Flink, além de bibliotecas de machine learning como MLlib.
- **Escalabilidade Automática**: Ajusta automaticamente a capacidade dos clusters com base na carga de trabalho, economizando custos.
- **Integração com Armazenamento**: Trabalha diretamente com Amazon S3, permitindo usar o S3 como armazenamento principal de dados e logs.
- **Segurança e Controle de Acesso**: Suporte a criptografia de dados em trânsito e repouso, além de controle de permissões detalhado com AWS IAM.
- **Flexibilidade de Instâncias**: Suporte para instâncias Spot (custo reduzido), sob demanda e reservadas para otimizar custos.
- **Processamento Rápido**: Utiliza o Elastic Fabric Adapter (EFA) para acelerar cargas de trabalho distribuídas, como machine learning e análise de dados.
- **Cluster Permanente ou Transitório**: Oferece opções para executar clusters transitórios para tarefas específicas ou manter clusters de longa duração para análises contínuas.
- **Monitoramento e Diagnóstico**: Integração com Amazon CloudWatch e outras ferramentas para rastreamento de desempenho e identificação de gargalos.
- **Notebooks Integrados**: Suporte a Jupyter Notebooks para desenvolvimento interativo e análise exploratória.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no número e tipo de instâncias EC2 usadas no cluster.
    - Taxas adicionais para armazenamento no S3, transferência de dados e serviços associados (como Spark e Hadoop).
    - Uso de instâncias Spot pode reduzir significativamente os custos.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon EMR como uma solução para processamento e análise de grandes volumes de dados.
- Reconhecer a integração com frameworks de big data, como Hadoop e Spark.
- Compreender como ele ajuda a reduzir custos com instâncias Spot e armazenamento no S3.