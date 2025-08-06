[[Segurança e conformidade]]
O **AWS Secrets Manager** é um serviço para **gerenciamento de segredos**, como credenciais de banco de dados, chaves de API e outros dados confidenciais. Ele facilita o **armazenamento seguro**, **gerenciamento automático de rotação** e **acesso controlado** a segredos.
### Características Técnicas

- **Armazenamento Seguro**:
    
    - Segredos são criptografados usando **AWS Key Management Service (KMS)**.
    - Suporte a texto simples ou pares chave-valor, para armazenar configurações complexas.
- **Rotação Automática**:
    
    - Integração com **Amazon RDS**, **Redshift**, **DocumentDB**, entre outros, para rotação automática de credenciais de banco de dados.
    - Suporte a rotinas personalizadas para segredos externos, utilizando **AWS Lambda**.
- **Gerenciamento de Acesso**:
    
    - Integração com **AWS Identity and Access Management (IAM)** para controle detalhado de acesso.
    - Permissões podem ser configuradas por usuário, função ou serviço AWS.
- **Integração com Serviços AWS**:
    
    - Integra-se diretamente com **AWS SDK** para recuperar segredos em tempo de execução.
    - Suporte ao uso com **CloudFormation** para provisionamento automatizado.
- **Monitoramento e Auditoria**:
    
    - Logs de acesso e alterações disponíveis no **AWS CloudTrail**.
    - Alertas configuráveis usando **CloudWatch** para acessos ou eventos específicos.

---

### Informações Extras

- **Segredos não expiram automaticamente**: a rotação deve ser configurada pelo administrador.
- Suporte para **filtros de pesquisa** baseados em tags para gerenciamento de segredos em larga escala.
- **Alternativa ao Parameter Store** (AWS Systems Manager):
    - Secrets Manager é mais adequado para segredos sensíveis devido à rotação automática.
    - Parameter Store é recomendado para configurações menos críticas, sem rotação.

---

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **Secrets Manager** é um serviço independente, mas integra-se com:

- **AWS KMS**: Criptografia de segredos.
- **AWS Lambda**: Para criar rotinas de rotação personalizadas.
- **Amazon RDS** e **Redshift**: Suporte nativo à rotação de credenciais.
- **IAM**: Controle granular de acesso a segredos.
- **CloudTrail e CloudWatch**: Monitoramento de acessos e auditoria.

---

### Custos

- **Modelo de Custos**:
    - **Armazenamento**: Cobrança por segredo armazenado por mês (atualmente cerca de **$0.40 por segredo**).
    - **Rotação**: Custo adicional para chamadas de API realizadas durante a rotação.
    - Integração com Lambda para rotação personalizada pode incorrer em custos de execução.

---

### Casos de Uso Comuns no Exame

- Identificar quando usar **Secrets Manager** em vez do **Parameter Store** para gerenciamento de credenciais.
- Entender como configurar a **rotação automática de segredos** para serviços como Amazon RDS.
- Reconhecer o papel do **IAM** e do **KMS** no gerenciamento e na segurança de segredos.
- Saber como auditar acessos a segredos usando o **CloudTrail**.
- Analisar cenários de integração com aplicativos para acessar segredos em tempo de execução via **AWS SDK**.