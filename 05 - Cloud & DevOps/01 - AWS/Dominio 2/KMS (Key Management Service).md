[[Segurança e conformidade]]
AWS Key Management Service (KMS) é um serviço gerenciado que facilita a criação, o gerenciamento e o uso de chaves criptográficas para proteger dados em aplicativos e serviços AWS. Ele permite gerenciar o ciclo de vida de chaves com segurança e conformidade.
- **Gerenciamento de Chaves**: Criação, rotação e exclusão de chaves gerenciadas pela AWS (AWS-managed keys) ou pelo cliente (Customer-managed keys).
- **Integração com Serviços AWS**: Funciona com mais de 100 serviços, como S3, EBS, RDS, DynamoDB e Lambda, para criptografia automática de dados em repouso e em trânsito.
- **Suporte a CMKs (Customer Master Keys)**:
    - **AWS-managed CMKs**: Criadas e gerenciadas pela AWS para uso simplificado.
    - **Customer-managed CMKs**: Oferecem controle total sobre permissões, rotação automática e política de chaves.
    - **CloudHSM-backed CMKs**: Integração com AWS CloudHSM para chaves armazenadas em hardware dedicado.
- **Envelope Encryption**: Usa chaves do KMS para proteger chaves de dados menores, aumentando a eficiência e a segurança.
- **Controle de Acesso Detalhado**: Gerenciamento granular com políticas IAM e políticas de chaves específicas para definir quem pode usar ou gerenciar chaves.
- **Auditoria e Monitoramento**: Integração com AWS CloudTrail para registrar todas as ações realizadas com chaves, garantindo rastreabilidade.
- **FIPS 140-2 Compliance**: Atende aos padrões de segurança FIPS 140-2 para criptografia, garantindo conformidade com normas rigorosas.
- **Rotação de Chaves**: Rotação automática de chaves gerenciadas pelo cliente em intervalos regulares para reforçar a segurança.
- **Assinatura Digital e Criptografia Assimétrica**: Suporte para criptografia e assinatura digital com chaves assimétricas.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no número de solicitações de API (ex.: criptografia, descriptografia, geração de chaves).
    - Taxas adicionais para chaves gerenciadas pelo cliente e chaves assinadas pelo CloudHSM.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS KMS como a solução para gerenciar e proteger chaves criptográficas usadas por serviços AWS.
- Reconhecer o suporte para rotação automática e gerenciamento granular de chaves.
- Compreender a integração com CloudTrail para auditoria e rastreamento de ações de chaves.