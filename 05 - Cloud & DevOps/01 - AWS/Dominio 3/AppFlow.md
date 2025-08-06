[[Tecnologia e serviços da nuvem]]
Serviço de integração que permite transferir dados de forma segura entre aplicativos SaaS (Software as a Service) e serviços AWS, sem a necessidade de escrever código.
- **Integrações Nativas**: Conecta facilmente aplicativos SaaS populares, como Salesforce, Google Analytics, Slack, Zendesk, ServiceNow, e Workday, com serviços AWS como S3, Redshift e DynamoDB.
- **Transferência Bidirecional**: Suporte para fluxo de dados em ambas as direções, entre aplicativos SaaS e a AWS.
- **Filtros e Transformações**: Permite transformar dados (ex.: limpeza, concatenação, mapeamento de campos) durante a transferência, sem precisar de scripts adicionais.
- **Execução Automatizada ou Sob Demanda**: Os fluxos de dados podem ser agendados, acionados por eventos ou executados manualmente.
- **Conformidade e Segurança**: Oferece criptografia de dados em trânsito e em repouso, além de estar em conformidade com padrões como GDPR, SOC e HIPAA.
- **Visualização de Dados**: Integração com Amazon QuickSight para análise e visualização de dados transferidos.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no número de fluxos executados e na quantidade de dados transferidos (medida em GB).
    - Custos adicionais podem surgir dependendo dos serviços AWS utilizados, como S3 ou Redshift.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS AppFlow como uma solução para sincronizar dados entre SaaS e serviços AWS.
- Compreender como o AppFlow elimina a necessidade de soluções de integração customizadas e complexas.
- Reconhecer a segurança e conformidade oferecidas pelo AppFlow em fluxos de dados sensíveis.