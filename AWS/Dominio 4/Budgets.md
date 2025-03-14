[[Cobrança, Preços e Suporte]]

Ferramenta de gerenciamento de custos que permite configurar e monitorar orçamentos personalizados para uso da AWS, ajudando a controlar gastos e a prever custos futuros.

- **Definição de Orçamentos**: Permite configurar limites para custos, uso ou cobertura de Savings Plans e Reserved Instances (RIs).
- **Alertas Personalizados**: Envia notificações via email ou Amazon SNS quando os custos ou uso excedem os limites configurados ou atingem determinados percentuais.
- **Monitoramento em Tempo Real**: Atualizações frequentes fornecem uma visão detalhada dos custos e uso em comparação com o orçamento.
- **Previsão Baseada em Dados**: Gera previsões de gastos futuros com base no uso e nos custos históricos.
- **Integração com AWS Cost Explorer**: Fornece insights detalhados para ajudar a entender e otimizar os gastos.
- **Suporte Multi-Conta**: Pode ser usado em conjunto com o AWS Organizations para monitorar orçamentos de contas vinculadas.
- **Diferentes Tipos de Orçamento**:

- **Custo**: Limite máximo de gastos com base no consumo.
- **Uso**: Limite máximo de utilização de serviços ou recursos.
- **Cobertura**: Verifica a cobertura de Savings Plans e RIs.
- **Budget Actions**: Permite definir ações automáticas (como restringir permissões ou encerrar recursos) com base no status do orçamento.
- **Cost Anomaly Detection**: Identifica padrões anômalos de gastos e envia alertas para ajudar a evitar surpresas.
- **Notificações Configuráveis**: Até 20 notificações por orçamento via e-mail ou SNS, com base em limites de custo, uso ou Savings Plans.
- **Integração com Cost Explorer**: Visualiza relatórios detalhados diretamente do orçamento para entender os fatores de custo.
-  **Orçamentos Multi-Cenário**:
    - **Cost Budgets**: Monitoram gastos totais ou específicos por serviço, região ou etiqueta (tag).
    - **Usage Budgets**: Controlam a utilização de recursos como instâncias EC2 ou armazenamento S3.
    - **RI and Savings Plans Budgets**: Acompanham cobertura e uso de instâncias reservadas e Savings Plans.
- **Automação com APIs**: Suporte para APIs que permitem criar, atualizar e monitorar orçamentos programaticamente.
- **Relatórios de Orçamento Consolidado**: Integra-se com AWS Organizations para monitorar e consolidar orçamentos em várias contas.

**Modelo de Preços**:

- **Gratuito para Orçamentos Simples**:
    - Até 62 alertas de orçamento mensais sem custo adicional.
    - Custos adicionais podem ser aplicados para notificações ou integrações personalizadas (ex.: via SNS).

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Budgets como uma ferramenta para controlar e prever gastos.
- Reconhecer a importância dos alertas de custo para evitar excedentes inesperados.
- Compreender como os orçamentos de cobertura ajudam a monitorar o uso de Savings Plans e RIs.