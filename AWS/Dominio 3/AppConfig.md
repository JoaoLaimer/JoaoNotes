[[Tecnologia e serviços da nuvem]]
AWS AppConfig é um serviço da AWS que facilita o gerenciamento e a implementação de configurações em aplicativos. Ele permite que você altere configurações de maneira controlada e sem necessidade de reiniciar ou reimplantar aplicativos, reduzindo riscos e melhorando a agilidade operacional.
**1. Gerenciamento Centralizado de Configurações**

- Armazena configurações separadas do código-fonte, permitindo atualizações independentes e mais rápidas.
- Suporte para diferentes tipos de configurações, como arquivos JSON, YAML ou parâmetros simples.

**2. Implementações Controladas**

- **Releases Gradativas**: Permite lançar alterações de configuração progressivamente para reduzir riscos.
- **Monitoramento de Impacto**: Integração com Amazon CloudWatch para rastrear métricas e interromper implementações problemáticas automaticamente.

**3. Suporte Multi-Ambiente**

- Criação de configurações específicas para diferentes ambientes, como desenvolvimento, teste e produção.
- Gerenciamento centralizado para implementar configurações de forma consistente em vários serviços ou aplicações.

**4. Integração com AWS Systems Manager**

- Armazena configurações no AWS Systems Manager Parameter Store ou Secrets Manager para maior segurança e flexibilidade.

**5. Validação de Configurações**

- Verifica automaticamente a sintaxe e a validade dos arquivos de configuração antes da implementação.

**6. Segurança e Controle de Acesso**

- Gerenciamento granular de permissões com AWS IAM para garantir que apenas usuários autorizados possam modificar configurações.

**7. Integração com Arquiteturas Modernas**

- Compatível com aplicações baseadas em contêineres (ECS, EKS) e serverless (AWS Lambda).
- Suporte para aplicativos rodando on-premises ou em outras nuvens.

**8. Automação com APIs**

- APIs para gerenciar configurações, ambientes e implementações programaticamente.'
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobranças baseadas no número de configurações armazenadas e no volume de implementações realizadas.
**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS AppConfig como uma solução para gerenciamento de configurações de aplicativos.
- Reconhecer sua capacidade de realizar releases controlados e monitorar o impacto de alterações.
- Compreender como ele se integra com AWS Systems Manager e outros serviços para segurança e eficiência.