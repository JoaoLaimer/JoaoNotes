[[Tecnologia e serviços da nuvem]]
Amazon EventBridge é um serviço de barramento de eventos que facilita a integração de aplicativos usando eventos de várias fontes, como serviços AWS, aplicações SaaS e sistemas personalizados. Ele permite criar arquiteturas orientadas a eventos sem a necessidade de gerenciar infraestrutura de mensagens.

**Características Técnicas**:

- **Eventos de Múltiplas Fontes**: Suporte para eventos de mais de 200 serviços AWS, aplicativos SaaS (como Zendesk, Shopify) e eventos personalizados.
- **Regras Baseadas em Padrões**: Filtragem e roteamento de eventos com base em padrões definidos, permitindo envio seletivo para destinos específicos.
- **Transformação de Eventos**: Permite modificar eventos antes de encaminhá-los para os destinos, adaptando o formato ou o conteúdo às necessidades do consumidor.
- **Alta Disponibilidade**: Totalmente gerenciado com redundância integrada em várias zonas de disponibilidade.
- **Destinos Compatíveis**: Suporte para enviar eventos para AWS Lambda, SQS, SNS, Step Functions, Kinesis Data Streams, APIs HTTP, entre outros.
- **Event Replay**: Permite reexecutar eventos arquivados para depuração, testes ou análise.
- **Arquivamento e Retenção**: Armazena eventos para recuperação e reprodução futura, com configurações personalizáveis de retenção.
- **Schemas Registry**: Detecta automaticamente esquemas de eventos, permitindo integração com ferramentas de desenvolvimento e SDKs gerados automaticamente.
- **APIs Avançadas**: Suporte para integração com serviços externos e aplicações personalizadas via APIs de eventos.

**Ideal para**:

- Arquiteturas orientadas a eventos que precisam de comunicação em tempo real entre serviços ou aplicativos.
- Empresas que buscam eliminar acoplamento rígido entre componentes de sistemas distribuídos.
- Workloads que requerem escalabilidade automática e alta disponibilidade sem gerenciamento manual de mensagens.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no número de eventos publicados, roteados e arquivados.
    - Taxas adicionais para eventos replay e retenção de eventos arquivados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon EventBridge como uma solução para roteamento de eventos em arquiteturas distribuídas.
- Reconhecer recursos como **Transformação de Eventos** e **Schemas Registry** para integração e automação avançadas.
- Compreender como ele facilita a comunicação em tempo real e reduz a complexidade de sistemas orientados a eventos.