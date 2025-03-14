[[Tecnologia e serviços da nuvem]]
Amazon MQ é um serviço gerenciado de mensagens que facilita a migração e o gerenciamento de brokers de mensagens baseados em padrões, como **ActiveMQ** e **RabbitMQ**. Ele permite comunicação assíncrona entre aplicativos e sistemas distribuídos.
- **Suporte a Protocolos Padrão**: Compatível com protocolos populares como AMQP, MQTT, STOMP e JMS, eliminando a necessidade de reescrever aplicativos ao migrar para a nuvem.
- **Gerenciamento Simplificado**: Automatiza tarefas operacionais, como provisionamento, atualizações e failover, reduzindo o esforço administrativo.
- **Alta Disponibilidade**: Configuração Multi-AZ com failover automático para maior resiliência.
- **Segurança Integrada**: Suporte a criptografia de dados em trânsito e em repouso, controle de acesso com AWS IAM e conectividade com Amazon VPC.
- **Monitoramento e Logs**: Integração com Amazon CloudWatch para monitorar métricas como conexões, filas e mensagens.
- **Escalabilidade Horizontal**: Suporte para adicionar mais brokers para lidar com cargas de trabalho crescentes.
- **Suporte a Brokers Personalizados**: Possibilidade de ajustar configurações específicas do broker para atender requisitos de desempenho e segurança.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos com base no tempo de execução dos brokers (por hora), armazenamento de mensagens e transferência de dados.
    - Diferentes tipos de brokers (ActiveMQ ou RabbitMQ) podem influenciar os custos.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon MQ como uma solução para gerenciar serviços de mensagens baseados em ActiveMQ e RabbitMQ.
- Reconhecer sua compatibilidade com protocolos padrão como um facilitador para migrações.
- Compreender como ele automatiza tarefas operacionais e garante alta disponibilidade.