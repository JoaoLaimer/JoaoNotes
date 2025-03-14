[[Tecnologia e serviços da nuvem]]
Amazon CloudFront é uma rede de entrega de conteúdo (CDN) gerenciada que distribui dados, vídeos, aplicativos e APIs com baixa latência e alta velocidade, usando uma rede global de pontos de presença (Edge Locations).
- **Entrega Global**: Distribui conteúdo usando uma rede de pontos de presença em todo o mundo, garantindo baixa latência e alta disponibilidade.
- **Suporte a Vários Tipos de Conteúdo**: Compatível com entrega de sites estáticos, vídeos em streaming, aplicativos dinâmicos e APIs.
- **Integração com S3 e EC2**: Funciona perfeitamente com armazenamento no S3 ou servidores EC2 como origem para distribuição de conteúdo.
- **Segurança Avançada**: Suporte para AWS Shield e AWS WAF para proteção contra ataques DDoS e vulnerabilidades web.
- **Cache Personalizável**: Configuração granular para TTL (time-to-live) de conteúdo e suporte a cache dinâmico com base em cookies, cabeçalhos HTTP e strings de consulta.
- **Entrega Segura**: Suporte para HTTPS, TLS e integração com AWS Certificate Manager (ACM) para certificados SSL/TLS gratuitos.
- **Monitoramento Detalhado**: Integração com Amazon CloudWatch para métricas e logs, como taxa de transferência e número de solicitações.
- **Streaming de Vídeo**: Suporte nativo para RTMP e HLS, permitindo entrega eficiente de vídeos sob demanda ou em tempo real.
- **Invalidation de Cache**: Permite atualizar ou invalidar conteúdo no cache a qualquer momento para garantir que os usuários recebam as versões mais recentes.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobranças baseadas no volume de dados transferidos para os pontos de presença e número de solicitações processadas.
    - Preços variam por região e tipo de conteúdo (estático ou dinâmico).
    - Recursos adicionais, como invalidation de cache, têm custo proporcional ao número de invalidações solicitadas.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon CloudFront como uma solução para distribuição de conteúdo global com baixa latência.
- Reconhecer sua integração com S3, EC2 e serviços de segurança como WAF e Shield.
- Compreender o benefício de entrega segura e cache personalizável para melhorar a performance e reduzir custos.