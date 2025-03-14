[[Segurança e conformidade]]
Serviço gerenciado que ajuda a configurar e gerenciar um ambiente multi-conta seguro e escalável na AWS, com base nas melhores práticas recomendadas.

- **Landing Zone Automatizada**: Configura automaticamente uma estrutura inicial para múltiplas contas AWS, incluindo governança, políticas de segurança e conformidade utilizando [[CloudFormation]].
- **Guardrails (Trilhos de Proteção)**:
    - Oferece controles predefinidos para impor políticas e boas práticas de segurança.
    - Inclui **guardrails preventivos** (bloqueiam ações não conformes) e **detectivos** (notificam sobre desvios).
- **Integração com AWS Organizations**: Utiliza AWS Organizations para criar e gerenciar contas dentro de uma estrutura hierárquica.
- **Conformidade Contínua**: Monitora automaticamente o ambiente e gera relatórios para verificar se as contas estão em conformidade com os guardrails configurados.
- **Painel Centralizado**: Fornece uma visão unificada para gerenciar contas, conformidade e status de políticas.
- **Suporte a Workloads Diversos**: Permite adaptar o ambiente para workloads regulados (ex.: GDPR, SOC, HIPAA) ou com requisitos corporativos específicos.

**Modelo de Preços**:

- **Gratuito**: O AWS Control Tower não tem custo adicional.
    - Os custos associados são gerados pelos serviços subjacentes usados, como AWS [[Organizations]], [[CloudTrail]], Config e S3.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Control Tower como uma solução para configurar e gerenciar ambientes multi-conta com governança centralizada.
- Reconhecer a importância dos **guardrails** para impor políticas e manter conformidade em todas as contas.
- Compreender como o Control Tower automatiza a configuração de um ambiente seguro e escalável para novas contas.

Consegue gerenciar multiplas contas, orquestra as capacidades de varios servicos da AWS, incluindo AWS [[Organizations]], [[Service Catalog]], [[IAM Identity Center]]
**CRIA MUITAS CONTAS COM CONFIGURACOES DEFINIDAS SIMULTANEAMENTE**
