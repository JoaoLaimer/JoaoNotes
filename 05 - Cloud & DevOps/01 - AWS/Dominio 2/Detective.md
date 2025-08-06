[[Segurança e conformidade]]
Amazon Detective é um serviço gerenciado de análise e visualização de segurança que ajuda a investigar e identificar a causa raiz de atividades suspeitas ou potenciais ameaças em sua infraestrutura AWS. Ele analisa automaticamente logs e eventos de segurança para fornecer insights detalhados e conexões relevantes.
- **Análise Automática**: Processa dados de segurança, como logs do **AWS CloudTrail, Amazon VPC Flow Logs e Amazon GuardDuty,** para identificar padrões de comportamento.
- **Criação de Gráficos de Segurança**: Gera visualizações dinâmicas de atividades e conexões entre recursos para facilitar a investigação.
- **Correlação de Eventos**: Liga atividades suspeitas a eventos relacionados, permitindo uma análise mais contextualizada.
- **Integração com GuardDuty e Security Hub**: Trabalha em conjunto com outros serviços AWS para complementar a detecção de ameaças e centralizar a resposta.
- **Suporte a Dados Históricos**: Analisa logs e eventos armazenados para fornecer contexto histórico durante investigações.
- **Gerenciamento Simples**: Sem necessidade de configuração ou manutenção de infraestrutura; o serviço opera automaticamente com base nos dados habilitados.
- **Escalabilidade**: Lida com grandes volumes de dados e atividades complexas em infraestruturas AWS em escala.
- **Segurança e Conformidade**: Os dados processados permanecem protegidos por criptografia e seguem as políticas de acesso definidas por IAM.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no volume de dados processados e analisados (geralmente originados de GuardDuty, CloudTrail e VPC Flow Logs).
    - Preços variam com base na quantidade de eventos e na duração do armazenamento de dados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon Detective como uma solução para investigação de atividades suspeitas e ameaças de segurança.
- Reconhecer sua integração com GuardDuty e Security Hub como parte de um ecossistema de segurança AWS.
- Compreender como ele automatiza a análise de logs e facilita a identificação de causa raiz.