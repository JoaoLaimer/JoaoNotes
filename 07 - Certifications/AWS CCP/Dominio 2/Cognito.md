[[Segurança e conformidade]]
Serviço que permite adicionar autenticação, autorização e gerenciamento de usuários a aplicativos da web e móveis, com suporte para login social e autenticação corporativa.
- **Pools de Usuários (User Pools)**:
    
    - Permite criar e gerenciar diretórios de usuários com funcionalidades como registro, login, recuperação de senha e autenticação multifator (MFA).
    - Suporte a autenticação via email, número de telefone e login social (ex.: Google, Facebook e Amazon).
- **Pools de Identidade (Identity Pools)**:
    
    - Oferece autenticação baseada em credenciais temporárias para acessar serviços AWS, como S3 e DynamoDB.
    - Integra login de usuários autenticados (ex.: via User Pools ou login social) e usuários anônimos.
- **Autenticação Federada**:
    
    - Suporte para integração com provedores de identidade corporativos que utilizam SAML 2.0, OpenID Connect ou diretórios Microsoft Active Directory.
- **Customização e Branding**:
    
    - Permite personalizar telas de login e fluxos de autenticação para atender à identidade visual do aplicativo.
- **Escalabilidade**:
    
    - Gerencia milhões de usuários sem a necessidade de provisionar ou manter servidores.
- **Segurança Avançada**:
    
    - Suporte para MFA, controle granular de permissões e criptografia de dados.
    - Integração com AWS WAF e Amazon CloudWatch para monitoramento e segurança adicionais.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança com base no número de usuários ativos mensais (MAUs).
    - Recursos adicionais, como autenticação MFA ou login social, podem gerar custos extras.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon Cognito como uma solução para adicionar login social ou autenticação multifator a aplicativos.
- Compreender como o Cognito facilita o gerenciamento de usuários em ambientes de alta escala.
- Reconhecer a função de pools de identidade para autenticar usuários e gerenciar permissões em serviços AWS.