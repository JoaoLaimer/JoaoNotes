[[Segurança e conformidade]]
Serviço que registra atividades de API e ações realizadas em **sua conta** AWS, fornecendo auditoria, monitoramento e rastreamento de eventos para garantir conformidade e segurança.
- **Seus logs salvos possuem encriptação ativada por padrão**
- **Registro de Atividades**: Captura chamadas de API feitas por usuários, serviços ou aplicativos, incluindo ações realizadas no console da AWS, CLI ou SDKs.
- **Eventos de Gerenciamento**: Registra ações administrativas, como criação, exclusão ou alteração de recursos.
- **Eventos de Dados**: Monitora acessos específicos a dados, como leituras e gravações em buckets do S3 ou consultas ao DynamoDB.
- **Armazenamento de Logs**: Salva automaticamente os logs em um bucket do Amazon S3 para auditoria e análise futura.
- **Insights**: Detecta padrões incomuns de atividade na conta AWS, ajudando a identificar possíveis incidentes de segurança.
- **Integração com Outros Serviços AWS**: Funciona bem com Amazon [[CloudWatch]] para configurar alarmes e Amazon Athena para análise avançada de logs.
- **Multi-Conta e Multi-Região**: Oferece uma visão consolidada das atividades em várias contas AWS dentro de uma organização.
- **Retenção Personalizada**: Permite configurar políticas de retenção para armazenar logs conforme requisitos de conformidade.
**Modelo de Preços**:

- **Gratuito**:
    - Os primeiros 90 dias de eventos de gerenciamento são gratuitos para cada trilha (trail).
    - A criação de trilhas (trails) para registrar eventos de gerenciamento básicos não tem custo.
- **Pague pelo uso**:
    - Cobrança adicional para eventos de dados e logs armazenados no S3.
    - Custos podem surgir ao integrar com serviços como Athena ou CloudWatch.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS CloudTrail como uma solução para auditoria e rastreamento de atividades na conta AWS.
- Reconhecer a diferença entre eventos de gerenciamento (ações administrativas) e eventos de dados (acessos a dados).
- Compreender como o CloudTrail ajuda a cumprir requisitos de conformidade e investigar incidentes de segurança.