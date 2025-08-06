[[Segurança e conformidade]]
O root user é a conta principal criada ao configurar uma conta AWS. Ele tem permissões administrativas totais e irrestritas para acessar e gerenciar todos os recursos da AWS, incluindo funções críticas como exclusão de contas, alteração de informações de pagamento e configuração de segurança global.

- **Permissões Totais**: O root user tem acesso irrestrito a todos os serviços e configurações da conta AWS.
	- Exemplos: Alterar informações de contas, Fechar contas, Alterar planos no AWS Support, Ativar MFA para um bucket S3, Registrar-se como vendedor de instancias Reservadas no Markeplace, etc.
- **Funções Críticas**: Necessário para tarefas como:
    - Configurar o faturamento da conta.
    - Cancelar a conta AWS.
    - Gerenciar métodos de pagamento.
    - Restaurar credenciais IAM bloqueadas.
- **Segurança Reforçada**:
    - **Autenticação Multifator (MFA)**: Recomendado para proteger o root user contra acessos não autorizados.
    - **Uso Limitado**: Boas práticas sugerem que o root user seja usado apenas em tarefas indispensáveis e raramente.
- **Gerenciamento Delegado**: Capacidade de criar usuários IAM com permissões específicas para realizar operações administrativas, reduzindo a dependência do root user.
**Melhores Práticas de Segurança**:

1. Ativar MFA para o root user.
2. Criar usuários IAM com permissões administrativas e desativar o uso diário do root user.
3. Monitorar o acesso e uso do root user com AWS CloudTrail.
4. Nunca compartilhar as credenciais do root user.
**Modelo de Preços**:

- Não há custos associados diretamente ao uso do root user, mas ações realizadas podem gerar cobranças com base nos recursos consumidos.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Reconhecer o root user como uma identidade com acesso total e irrestrito à conta AWS.
- Identificar boas práticas para proteger e limitar o uso do root user.
- Compreender que a delegação de tarefas para usuários IAM melhora a segurança e a governança da conta.