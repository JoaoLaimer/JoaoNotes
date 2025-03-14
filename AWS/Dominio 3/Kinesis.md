[[Tecnologia e serviços da nuvem]]

Serviço que facilita a coleta, processamento e análise de grandes volumes de dados em tempo real, ideal para cenários como streaming de vídeo, monitoramento de logs e análise de eventos.
**Componentes do Kinesis**:

1. **Kinesis Data Streams**:
    
    - Permite ingerir e armazenar dados de streaming para processamento em tempo real.
    - Suporte para processamento distribuído com aplicativos personalizados ou integrados com serviços como AWS Lambda.
2. **Kinesis Data Firehose**:
    
    - Transfere dados de streaming diretamente para destinos como Amazon S3, Redshift, Elasticsearch ou Splunk.
    - Oferece transformações de dados leves durante a transferência.
3. **Kinesis Data Analytics**:
    
    - Analisa dados de streaming em tempo real usando SQL ou Apache Flink.
    - Ideal para detectar padrões, gerar métricas ou responder a eventos em tempo real.
4. **Kinesis Video Streams**:
    
    - Processa e armazena streams de vídeo em tempo real para análise, transmissão ou machine learning.
    - Suporte para aplicações como vigilância, IoT e análise de mídia.
- **Escalabilidade Automática**: Adapta-se dinamicamente ao volume de dados sem intervenção manual.
- **Baixa Latência**: Processamento em tempo real com latência de milissegundos, garantindo respostas rápidas a eventos.
- **Integração com Outros Serviços AWS**: Funciona perfeitamente com Lambda, S3, DynamoDB, e Redshift para pipelines de dados completos.
- **Alta Disponibilidade**: Projetado para ser resiliente e operar continuamente em grandes volumes de dados.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Kinesis Data Streams: Cobrança com base no número de shards e volume de dados ingeridos e lidos.
    - Kinesis Data Firehose: Baseado no volume de dados transferidos e processados.
    - Kinesis Data Analytics: Cobrança baseada nos recursos computacionais usados para processar os dados.
    - Kinesis Video Streams: Custos associados ao volume de vídeo ingerido, armazenado e transmitido.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar os componentes do Amazon Kinesis e suas funções (Streams, Firehose, Analytics e Video Streams).
- Reconhecer como o Kinesis facilita o processamento de dados em tempo real para big data e machine learning.
- Entender os benefícios de integração com outros serviços AWS para criar pipelines de dados completos.