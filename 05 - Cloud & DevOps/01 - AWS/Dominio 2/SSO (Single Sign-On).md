[[Segurança e conformidade]]
AWS Single Sign-On (SSO) é um serviço que permite gerenciar acesso centralizado a contas AWS e aplicativos baseados em nuvem, utilizando autenticação única para simplificar o gerenciamento de identidade e melhorar a experiência do usuário.
- **Autenticação Centralizada**: Gerencia o acesso a várias contas AWS e aplicativos SaaS em um único ponto de entrada.
- **Integração com Identity Providers (IdPs)**: Compatível com provedores de identidade como Microsoft Active Directory, Okta, Ping Identity e outros via SAML 2.0.
- **Gerenciamento de Contas AWS**: Permite atribuir permissões específicas por função ou conta para usuários e grupos, utilizando AWS Organizations.
- **SSO para Aplicativos SaaS**: Oferece integração com serviços como Salesforce, Slack e Office 365.
- **Console de Usuário Personalizado**: Usuários acessam diretamente todas as contas e aplicativos permitidos por meio de um portal unificado.
- **Permissões Baseadas em Funções**: Suporte a AWS IAM e políticas predefinidas para atribuir permissões personalizadas a diferentes usuários ou grupos.
- **Logs de Auditoria e Rastreamento**: Integração com AWS CloudTrail para registrar atividades de login e gerenciamento de acesso.
- **Multi-Fator Authentication (MFA)**: Reforça a segurança adicionando um segundo fator de autenticação.
- **Provisionamento Automático (SCIM)**: Automatiza o provisionamento e desprovisionamento de usuários em aplicativos compatíveis com o protocolo SCIM.
- **Alta Disponibilidade**: Serviço gerenciado que oferece redundância integrada para garantir acesso contínuo.
**Modelo de Preços**:

- **Gratuito**:
    - O uso do AWS SSO não gera custos adicionais.
    - Cobranças podem surgir para serviços associados, como AWS Organizations ou recursos provisionados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS SSO como uma solução para autenticação unificada e gerenciamento centralizado de acessos.
- Reconhecer sua integração com provedores de identidade externos e AWS Organizations para controle de contas.
- Compreender o papel do AWS SSO em melhorar a segurança e simplificar operações de acesso.