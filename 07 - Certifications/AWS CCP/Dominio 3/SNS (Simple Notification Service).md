[[Tecnologia e serviços da nuvem]]

Serviço de mensagens gerenciado que permite enviar notificações entre aplicativos, serviços ou diretamente para usuários por meio de email, SMS ou outras integrações.
- **Pub/Sub (Publicação/Assinatura)**: Suporta modelo em que editores (publishers) enviam mensagens para tópicos e assinantes (subscribers) recebem essas mensagens por canais configurados.
- **Entrega Multicanal**: Permite enviar notificações por SMS, email, push notifications e integração com outros serviços AWS, como Lambda, SQS ou HTTP/S.
- **Alta Disponibilidade**: Projetado para entregar mensagens de forma confiável, com baixa latência e escalabilidade automática.
- **Filtros de Assinatura**: Permite que assinantes de um tópico recebam apenas mensagens de interesse, filtrando por atributos específicos.
- **Segurança Avançada**: Suporte para criptografia de mensagens em trânsito e repouso, além de gerenciamento de permissões com AWS IAM.
- **Integração Simples com Outros Serviços AWS**: Funciona bem com Lambda (para acionar funções), [[SQS (Simple Queue Service)]] (para filas) e CloudWatch (para monitoramento).
- **Fan-out**: Permite enviar uma mensagem para vários assinantes simultaneamente.
- **Delivery Status**: Relatórios sobre o status de entrega de mensagens para rastrear envios e identificar falhas.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Mensagens publicadas em tópicos são cobradas por número de publicações.
    - Entregas são cobradas com base no tipo de canal (ex.: mensagens SMS têm custo adicional).
    - Notificações push para dispositivos móveis podem incluir cobranças do provedor de push.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon SNS como uma solução para enviar notificações em tempo real entre serviços ou para usuários.
- Reconhecer a integração com serviços como Lambda e SQS para criar sistemas distribuídos.
- Compreender os benefícios de notificações multicanal e do modelo pub/sub para comunicação assíncrona.