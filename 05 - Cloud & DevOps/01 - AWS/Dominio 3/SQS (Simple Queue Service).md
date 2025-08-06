[[Tecnologia e serviços da nuvem]]
Serviço de fila gerenciado que facilita a comunicação entre sistemas e componentes de aplicativos distribuídos, desacoplando-os para maior escalabilidade e resiliência.
- **Modelo de Fila**:
    - **Standard Queue**: Oferece alta taxa de transferência e entrega eventual, em que uma mensagem pode ser entregue mais de uma vez (não FIFO).
    - **FIFO Queue (First-In-First-Out)**: Garante a ordem de entrega e entrega única por mensagem, ideal para aplicativos onde a sequência é essencial.
- **Durabilidade de Mensagens**: Mensagens podem ser armazenadas por até 14 dias se não forem processadas.
- **Integração com Outros Serviços AWS**: Funciona bem com Lambda, SNS, ECS e outros serviços para criar fluxos de trabalho assíncronos.
- **Visibilidade de Mensagens**: Suporta configuração de intervalos para impedir que mensagens sejam processadas simultaneamente por vários consumidores.
- **Escalabilidade Automática**: Capaz de lidar com um número ilimitado de mensagens, ajustando-se automaticamente à demanda.
- **Dead-Letter Queues (DLQs)**: Captura mensagens que não podem ser processadas para depuração e análise de falhas.
- **Criptografia**: Suporte para criptografia de mensagens em repouso usando AWS Key Management Service (KMS).
**Duração default**: 4 dias.
Max: 14 dias.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrados com base no número de solicitações de API (envio e recebimento de mensagens).
    - FIFO Queues têm preços diferenciados devido às garantias adicionais.
    - Custos extras para armazenamento prolongado ou uso de DLQs.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon SQS como uma solução para comunicação assíncrona entre sistemas distribuídos.
- Reconhecer a diferença entre Standard Queue e FIFO Queue em termos de entrega e ordem de mensagens.
- Compreender os benefícios de Dead-Letter Queues (DLQs) para depuração de mensagens não processadas.