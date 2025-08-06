[[Tecnologia e serviços da nuvem]]
O Elastic Load Balancer (ELB) distribui automaticamente o tráfego de entrada para várias instâncias, contêineres ou IPs em uma ou mais zonas de disponibilidade (AZs). Ele melhora a disponibilidade, escalabilidade e tolerância a falhas de aplicações, permitindo uma experiência de usuário consistente e confiável.

---

#### **Tipos de Elastic Load Balancer**

**1. Application Load Balancer (ALB)**

- **Descrição**: Otimizado para balancear tráfego HTTP/HTTPS em camadas de aplicação.
- **Características**:
    - Roteamento baseado em conteúdo (ex.: URL, cabeçalhos, métodos).
    - Integração com AWS Lambda para aplicativos serverless.
    - Suporte a WebSocket e HTTP/2.
    - Criação de listeners e regras detalhadas para fluxos específicos.

**2. Network Load Balancer (NLB)**

- **Descrição**: Projetado para balancear tráfego TCP/UDP em camadas de rede.
- **Características**:
    - Baixa latência para aplicativos que exigem alta performance.
    - Suporte para IPs estáticos e Elastic IPs.
    - Integração com AWS PrivateLink para conectar-se a serviços em VPCs privadas.

**3. Gateway Load Balancer (GWLB)**

- **Descrição**: Combina balanceamento de carga e roteamento de tráfego para appliances de rede como firewalls ou sistemas de detecção de intrusão (IDS).
- **Características**:
    - Transparente para o tráfego de rede.
    - Integração com appliances de terceiros.

**4. Classic Load Balancer (CLB)**

- **Descrição**: Balanceador de carga legado, compatível com tráfego em camadas de aplicação e rede.
- **Características**:
    - Suporte básico para HTTP/HTTPS e TCP.
    - Menos flexível em comparação com ALB e NLB.
- **Alta Disponibilidade**: Distribui tráfego entre várias AZs para garantir resiliência.
- **Auto Scaling**: Integra-se com **Auto Scaling Groups** para gerenciar automaticamente a capacidade de instâncias.
- **Health Checks**: Monitora continuamente a saúde das instâncias registradas para direcionar tráfego apenas para destinos funcionais.
- **TLS Offloading**: Gerencia criptografia TLS para reduzir a carga em instâncias backend.
- **Logging e Monitoramento**: Integra-se com **CloudWatch** e **Access Logs** para análise e auditoria do tráfego.
- **Roteamento Avançado**: Suporte a roteamento de tráfego com base em regras personalizadas (ALB).
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custo baseado no número de horas em que o load balancer está ativo.
    - Taxas adicionais por transferência de dados e número de regras ou listeners configurados.

---

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar os diferentes tipos de ELB e seus casos de uso: ALB para roteamento de conteúdo, NLB para baixa latência e GWLB para appliances de rede.
- Reconhecer o papel do ELB em melhorar a disponibilidade e escalabilidade de aplicações.
- Compreender a integração do ELB com Auto Scaling e Health Checks para gerenciamento eficiente de recursos.