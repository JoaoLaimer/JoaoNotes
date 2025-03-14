[[Tecnologia e serviços da nuvem]]
AWS X-Ray é um serviço que permite a análise e o rastreamento de aplicativos distribuídos, ajudando a identificar gargalos, erros e o comportamento de serviços interdependentes em aplicações em nuvem.
- **Análise de Traços**: Captura e rastreia solicitações enquanto elas percorrem os serviços e recursos de uma aplicação, como Lambda, EC2, DynamoDB e outros.
- **Mapeamento de Dependências**: Gera mapas de serviços para visualizar como os componentes de um aplicativo se conectam e interagem.
- **Identificação de Problemas**: Ajuda a localizar gargalos de desempenho e pontos de falha ao mostrar latências, erros e exceções em diferentes partes do aplicativo.
- **Suporte a Aplicações Serverless**: Totalmente integrado com AWS Lambda, permitindo rastrear funções serverless e sua interação com outros serviços.
- **Integração com Outras Ferramentas AWS**: Funciona com CloudWatch para monitoramento e gerenciamento centralizado.
- **Configuração de Amostragem**: Permite controlar a quantidade de dados coletados para balancear custo e visibilidade.
- **Filtros Avançados**: Oferece filtros para segmentar e analisar dados específicos, como traços com erros ou solicitações lentas.
- **Personalização com SDKs**: Suporte a SDKs para várias linguagens, permitindo instrumentação personalizada de aplicações.
- **Relatórios Detalhados**: Apresenta latência, taxa de erro e outras métricas relevantes para otimização de aplicativos.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no número de traços processados e armazenados, com taxas adicionais para gravação de dados no S3 ou CloudWatch Logs.
    - Amostragem reduzida ajuda a controlar os custos em aplicações de alta carga.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS X-Ray como uma solução para rastreamento e análise de desempenho de aplicativos distribuídos.
- Reconhecer como ele auxilia na visualização de dependências entre componentes e serviços.
- Compreender como ele ajuda a identificar problemas como latências altas ou erros em aplicativos complexos.
