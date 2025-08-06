[[Segurança e conformidade]]
Serviço da AWS que permite gerenciar de forma segura o acesso a recursos da AWS, permitindo a criação e gerenciamento de usuários, grupos, permissões e políticas de acesso.

- **Controle de Acesso Granular**: Define políticas que determinam quais ações os usuários podem realizar em recursos específicos da AWS, com base em roles (funções), usuários e grupos.
- **Gerenciamento de Identidade**: Criação de usuários, grupos e atribuição de permissões para gerenciar o acesso aos serviços e recursos da AWS.
- **Políticas Baseadas em JSON**: Políticas definidas em JSON que podem ser aplicadas a usuários ou grupos para conceder ou restringir acessos a serviços e recursos da AWS.
- **Autenticação Multifator (MFA)**: Reforça a segurança com autenticação multifatorial, exigindo uma segunda forma de verificação além da senha.
- **Controle de Acesso a Nível de Recurso**: Atribuição de permissões específicas para acessar recursos de forma detalhada (ex.: instâncias EC2, buckets S3, tópicos SNS).
- **Temporary Security Credentials**: Uso de credenciais temporárias para usuários e serviços com AWS STS (Security Token Service), permitindo acesso limitado e de curta duração.
- **Integração com Serviços Externos**: Suporte para autenticação de usuários com provedores de identidade externos via SAML 2.0, Active Directory ou outros serviços de federação.
- **Políticas de Senha e Segurança**: Define requisitos de senha, expiração e bloqueio para melhorar a segurança de contas de usuários.
- **Auditabilidade e Monitoramento (Access Advisor)**: Integrado com AWS CloudTrail para rastrear ações e eventos de IAM, permitindo auditoria de acessos e alterações de permissões.
- **Users**: Identidades para acesso individual a recursos.
- **Groups**: Coleções de usuários com permissões comuns.
- **Roles**: Permissões assumidas por usuários ou serviços para acessar recursos temporariamente.
- **Policies**: Definem permissões (gerenciadas ou inline).
- **Permissions Boundary**: Limita as permissões de um usuário ou função.
- **Identity Providers**: Integrações para autenticar usuários externos.
- **Access Analyzer**: Ajuda a identificar recursos na sua organização ou contas, como Buckets S3 ou Roles IAM, compartilhados com entidades externas.

**Modelo de Preços**:
- **Gratuito**:
    - Não há custo para usar o IAM.
    - As cobranças só ocorrem com o uso de recursos que são acessados ou gerenciados pelo IAM (ex.: serviços como EC2 ou S3).
    - O uso de MFA (Autenticação Multifatorial) também não gera custos adicionais.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS IAM como uma solução centralizada para gerenciar segurança e permissões na AWS.
- Compreender a diferença entre usuários, grupos, roles e políticas de segurança.
- Reconhecer a importância do IAM na governança e na conformidade de segurança em organizações.