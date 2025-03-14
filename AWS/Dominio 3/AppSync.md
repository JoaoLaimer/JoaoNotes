[[Tecnologia e serviços da nuvem]]
Serviço gerenciado que facilita a criação de APIs GraphQL para aplicativos móveis, da web e corporativos, permitindo acesso em tempo real a dados de diversas fontes com sincronização automática entre dispositivos e a nuvem.

- **APIs GraphQL Gerenciadas**: Permite consultar, modificar e sincronizar dados de forma eficiente usando GraphQL.
- **Dados em Tempo Real**: Suporta assinaturas GraphQL para transmitir atualizações em tempo real aos clientes conectados.
- **Integração com Serviços AWS**: Funciona perfeitamente com Amazon DynamoDB, AWS Lambda, Amazon RDS, Elasticsearch e outros para acessar dados em diferentes fontes.
- **Sincronização Offline**: Aplicativos continuam funcionando offline e sincronizam automaticamente as alterações quando reconectados à internet.
- **Controle de Acesso**: Integra-se com AWS IAM, Amazon Cognito e chaves API para gerenciar autenticação e autorização com segurança.
- **Escalabilidade Automática**: Suporta o crescimento dinâmico de usuários e consultas sem necessidade de gerenciar infraestrutura.
**Ideal para**:

- Desenvolvedores que precisam criar APIs rápidas e escaláveis para aplicativos móveis ou da web.
- Aplicativos que necessitam de dados em tempo real, como notificações, chats ou dashboards ao vivo.
- Cenários onde a sincronização offline é essencial, como aplicativos móveis que operam em áreas com conectividade limitada.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no número de solicitações (queries, mutations e subscriptions).
    - Adicional por operações em tempo real e transferência de dados.
    - O custo também pode incluir o uso de serviços subjacentes, como DynamoDB e Lambda, para armazenar e processar os dados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS AppSync como uma solução para criar APIs escaláveis com GraphQL.
- Reconhecer a vantagem de sincronização offline para aplicativos móveis.
- Entender como integrar dados em tempo real melhora a experiência do usuário em aplicativos modernos.