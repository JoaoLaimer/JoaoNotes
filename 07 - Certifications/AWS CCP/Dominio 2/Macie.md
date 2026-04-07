[[Segurança e conformidade]]
Amazon Macie é um serviço gerenciado que usa machine learning e detecção de padrões para identificar, proteger e monitorar dados confidenciais armazenados no Amazon S3, ajudando a garantir conformidade e segurança.

- **Detecção de Dados Sensíveis**: Identifica automaticamente informações confidenciais, como números de cartão de crédito, CPF, endereços de e-mail e outras PII (informações pessoalmente identificáveis).
- **Classificação Automática**: Escaneia e classifica os dados armazenados no S3 com base em tipo e nível de sensibilidade.
- **Monitoramento Contínuo**: Avalia continuamente os buckets S3 em busca de permissões incorretas e exposição de dados.
- **Relatórios de Conformidade**: Gera relatórios detalhados que ajudam no cumprimento de regulamentações como GDPR, HIPAA e CCPA.
- **Alerta e Notificação**: Integra-se com Amazon EventBridge e AWS Security Hub para gerar alertas automatizados sobre vulnerabilidades.
- **Integração com IAM**: Gerencia e limita acessos para proteger dados confidenciais.
- **Análise Granular**: Suporte para análises detalhadas com logs sobre dados escaneados e configurados no S3.
- **Automação de Ações**: Permite usar AWS Lambda para responder automaticamente a problemas detectados, como revogar permissões incorretas.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no volume de dados escaneados e no número de buckets S3 monitorados.
    - Custos adicionais para alertas e integração com serviços como EventBridge e Security Hub.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon Macie como uma solução para detecção e proteção de dados sensíveis em S3.
- Reconhecer sua integração com regulamentos de conformidade e serviços de segurança AWS.
- Compreender como ele ajuda a monitorar permissões incorretas e prevenir exposição de dados.