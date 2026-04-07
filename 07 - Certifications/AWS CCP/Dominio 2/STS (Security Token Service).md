[[Segurança e conformidade]]
Serviço que emite credenciais temporárias para acessar recursos da AWS, permitindo autenticação segura e controlada para usuários, aplicativos ou serviços.
- **Credenciais Temporárias**:
    
    - Oferece chaves de acesso temporárias que expiram automaticamente após um período definido, reduzindo riscos de segurança.
    - Inclui um ID de acesso, uma chave secreta e um token de sessão.
- **AssumeRole**:
    
    - Permite que um usuário ou serviço assuma uma função (IAM Role) com permissões específicas, ideal para acessar recursos em outras contas ou realizar tarefas com permissões restritas.
- **Federated Users**:
    
    - Facilita a integração com provedores de identidade externos, como Microsoft Active Directory, SAML 2.0, ou OpenID Connect, permitindo autenticação federada.
- **GetSessionToken**:
    
    - Gera credenciais temporárias para usuários IAM autenticados, útil em casos de MFA (autenticação multifator).
- **AssumeRoleWithWebIdentity**:
    
    - Permite autenticação de usuários através de provedores de identidade de aplicativos móveis ou da web, como Amazon Cognito, Google, ou Facebook.
- **Region-Specific Endpoints**:
    
    - STS pode emitir credenciais específicas de uma região para garantir conformidade com requisitos locais ou melhorar a latência.
**Modelo de Preços**:

- **Gratuito**: Não há custos diretos para usar o STS; no entanto, os custos associados ao uso de outros serviços AWS, como Amazon S3 ou DynamoDB, aplicam-se às operações realizadas com as credenciais temporárias.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Reconhecer o AWS STS como uma solução para gerar credenciais temporárias e reduzir riscos de segurança.
- Compreender como assumir uma função (IAM Role) ajuda no gerenciamento de permissões entre contas.
- Identificar o STS como um facilitador de integração com autenticação federada ou provedores de identidade externos.