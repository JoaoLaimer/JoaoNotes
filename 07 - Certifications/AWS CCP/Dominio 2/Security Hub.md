[[Segurança e conformidade]]
Serviço centralizado que agrega, organiza e prioriza dados de segurança de várias contas e serviços AWS, oferecendo uma visão abrangente da postura de segurança da organização.
- **Centralização de Dados de Segurança**: Consolida alertas e achados de serviços AWS como [[GuardDuty]], [[Macie]], [[Inspector]] e de parceiros externos.
- **Padrões de Conformidade**: Monitora automaticamente recursos em busca de conformidade com frameworks como AWS Foundational Security Best Practices, CIS AWS Foundations Benchmark e PCI DSS.
- **Painéis Personalizáveis**: Fornece uma visão geral dos achados de segurança com gráficos, tabelas e insights acionáveis.
- **Classificação de Prioridades**: Organiza achados com base na gravidade, facilitando a priorização de ações.
- **Automação de Respostas**: Integração com AWS Lambda e Amazon EventBridge para automatizar respostas a eventos de segurança.
- **Integração Multi-Conta**: Suporte a organizações AWS para consolidar dados de segurança de várias contas em um único local.
- **APIs Abertas**: Permite integração com ferramentas de segurança de terceiros e sistemas de gerenciamento de eventos e informações de segurança (SIEM).
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no número de achados processados e recursos avaliados em conformidade com frameworks de segurança.
    - O uso de serviços subjacentes (como GuardDuty, Macie, Inspector) tem custos adicionais.
- **Camada Gratuita**:
    - 30 dias gratuitos para novos usuários do Security Hub.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Security Hub como uma solução centralizada para monitoramento e gerenciamento de segurança.
- Reconhecer os frameworks de conformidade suportados, como PCI DSS e CIS Benchmarks.
- Compreender como o Security Hub se integra com outros serviços AWS e ferramentas de terceiros para automatizar respostas e gerar insights acionáveis.