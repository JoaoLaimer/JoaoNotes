[[Tecnologia e serviços da nuvem]]

Serviço de computação serverless que permite executar código em resposta a eventos sem gerenciar servidores, cobrando apenas pelo tempo de execução do código..
- **Modelo Serverless**: Não exige provisionamento, gerenciamento ou escalabilidade manual de servidores; tudo é gerenciado pela AWS.
- **Suporte a Múltiplas Linguagens**: Oferece compatibilidade com Python, Node.js, Java, Go, Ruby, e .NET, além de permitir a criação de runtimes personalizados.
- **Execução Baseada em Eventos**: Pode ser acionado por serviços AWS como S3, DynamoDB, SNS, API Gateway, CloudWatch, entre outros.
- **Integração com Outros Serviços AWS**: Funciona bem com serviços como Step Functions para orquestração de workflows e EventBridge para automação avançada.
- **Escalabilidade Automática**: Ajusta automaticamente a capacidade de acordo com o número de eventos recebidos, sem intervenção manual.
- **Camadas Lambda (Layers)**: Permite compartilhar bibliotecas e dependências entre funções, otimizando o desenvolvimento e o uso de recursos.
- **Tempo de Execução Flexível**: Suporte para execução de funções de até 15 minutos por invocação.
- **Segurança**: Gerenciamento de permissões detalhado com AWS IAM e suporte para criptografia de variáveis de ambiente.
**Modelo de Preços**:

- **Gratuito**:
    - 1 milhão de requisições gratuitas por mês.
    - 400.000 GB-segundos de execução gratuitos por mês.
- **Pague pelo uso**:
    - Cobrança baseada no número de invocações e na duração da execução (em milissegundos), além da memória alocada para a função.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Lambda como uma solução serverless para executar código em resposta a eventos.
- Reconhecer os casos de uso em automação, pipelines de dados e APIs.
- Compreender o modelo de preços baseado em tempo de execução e invocações.