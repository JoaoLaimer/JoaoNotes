[[Tecnologia e serviços da nuvem]]
Serviço que permite criar e gerenciar recursos da AWS como infraestrutura como código (IaC), facilitando o provisionamento, atualização e gerenciamento de ambientes de forma automatizada e consistente.

- **Infraestrutura como Código (IaC)**: Define toda a infraestrutura em arquivos de texto (templates) no formato JSON ou YAML.
- **Automação Completa**: Gerencia o ciclo de vida dos recursos, incluindo provisionamento, atualização e exclusão.
- **Controle de Dependências**: Analisa automaticamente as dependências entre recursos e executa as ações na ordem correta.
- **Recursos Personalizados**: Suporte para criar extensões que permitem gerenciar recursos fora da AWS ou serviços personalizados.
- **Suporte Multi-Conta e Multi-Região**: Permite gerenciar recursos em várias contas e Regiões, simplificando arquiteturas distribuídas.
- **Monitoramento e Logs**: Integração com Amazon CloudWatch para acompanhar o status e os eventos das implantações.
- **Rollback Automático**: Reverte automaticamente para o estado anterior em caso de falha no provisionamento ou atualização.
- **StackSets**: Permite gerenciar várias pilhas (stacks) de recursos em contas e Regiões diferentes, facilitando a padronização em larga escala.

**Modelo de Preços**:

- **Gratuito**: Não há custo adicional para usar o CloudFormation.
    - O custo está relacionado aos serviços subjacentes que são criados, como instâncias [[EC2 (Elastic Compute Cloud)]], buckets [[S3 (Simple Storage Service)]], etc.
- **Custos Adicionais para Recursos Avançados**:
    - StackSets que usam recursos em várias contas podem gerar custos adicionais relacionados à configuração de permissões (ex.: AWS Organizations).

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Reconhecer o AWS CloudFormation como uma solução para automatizar o provisionamento de infraestrutura com infraestrutura como código.
- Identificar o uso de templates para criar ambientes consistentes e replicáveis.
- Compreender como o CloudFormation ajuda a gerenciar arquiteturas complexas e reduz o risco de erros manuais.