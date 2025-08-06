
[[Segurança e conformidade]] e [[Cobrança, Preços e Suporte]]
Serviço que permite gerenciar múltiplas contas AWS em uma estrutura centralizada, facilitando o controle de políticas, orçamentos e segurança em um ambiente multi-conta.
- **Gerenciamento Centralizado**: Oferece uma visão centralizada para gerenciar contas vinculadas e aplicar políticas organizacionais (SCPs).
- **Organizational Units (OUs)**: Agrupa contas em unidades organizacionais para aplicar políticas específicas a conjuntos de contas.
- **Service Control Policies (SCPs)**: Permite impor permissões específicas em contas ou OUs, restringindo ou permitindo ações em serviços da AWS.
- **Compartilhamento de Recursos**: Facilita o compartilhamento de recursos entre contas usando serviços como AWS Resource Access Manager (RAM).
- **Integração com AWS Cost Management**: Monitora custos consolidados para todas as contas vinculadas, simplificando o controle financeiro.
- **Suporte Multi-Conta**: Permite criar e gerenciar novas contas AWS diretamente pela interface do Organizations.
- **Conformidade e Segurança**: Oferece controle detalhado para garantir que todas as contas estejam em conformidade com políticas e padrões corporativos.
- **Uma conta so pode ser removida de uma organização se ela conseguir operar como uma conta standalone.**
**Modelo de Preços**:

- **Gratuito**:
    - Não há custo adicional para usar o AWS Organizations.
    - Custos são associados aos serviços consumidos pelas contas vinculadas.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Organizations como uma ferramenta para gerenciar várias contas AWS com controle centralizado.
- Reconhecer a importância das Service Control Policies (SCPs) para impor limites de uso em contas vinculadas.
- Entender como o Organizations ajuda a simplificar o monitoramento de custos e a otimização financeira em um ambiente multi-conta.