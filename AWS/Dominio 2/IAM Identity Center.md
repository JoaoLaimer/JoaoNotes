[[Segurança e conformidade]]
AWS IAM Identity Center é uma solução que centraliza o gerenciamento de acesso e autenticação a contas AWS e aplicativos baseados na nuvem, permitindo logins únicos (SSO) para usuários em toda a organização. Ele é integrado com AWS Organizations e suporta provedores de identidade externos.
- **Autenticação Centralizada**: Oferece um portal único para acessar várias contas AWS e aplicativos SaaS suportados.
- **Integração com AWS Organizations**: Gerencia permissões de acesso para várias contas de forma centralizada e consistente.
- **SSO para Aplicativos SaaS**: Suporte para aplicativos como Salesforce, Slack e Microsoft 365 usando autenticação SAML 2.0.
- **Suporte a Identity Providers (IdPs)**: Integração com IdPs como Okta, Azure AD, Ping Identity e outros, permitindo que organizações usem diretórios corporativos existentes.
- **Permissões Baseadas em Funções**: Criação e atribuição de permissões com base em funções IAM, permitindo acesso granular a recursos específicos.
- **Multi-Fator Authentication (MFA)**: Suporte para reforçar a segurança com autenticação multifatorial.
- **Provisionamento SCIM**: Automatiza a criação, atualização e remoção de usuários e grupos em aplicativos que suportam o protocolo SCIM.
- **Logs e Auditoria**: Integração com AWS CloudTrail para rastrear atividades de login e alterações em permissões.
- **Console Unificado**: Usuários acessam contas e aplicativos permitidos diretamente de um portal centralizado.
**Modelo de Preços**:

- **Gratuito**:
    - Não há custos adicionais para o uso do IAM Identity Center.
    - Cobranças aplicam-se a serviços subjacentes, como AWS Organizations ou recursos provisionados nas contas AWS.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o IAM Identity Center como uma solução para gerenciamento centralizado de identidade e autenticação única (SSO).
- Reconhecer sua integração com AWS Organizations e provedores de identidade externos.
- Compreender como ele melhora a segurança e simplifica operações em ambientes multi-conta.