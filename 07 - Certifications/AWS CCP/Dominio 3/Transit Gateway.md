[[Tecnologia e serviços da nuvem]]
AWS Transit Gateway é um serviço que simplifica o gerenciamento de redes ao conectar múltiplas VPCs, data centers on-premises e redes locais. Ele age como um hub central para o roteamento de tráfego, eliminando a necessidade de criar conexões individuais ponto a ponto entre redes.
**1. Arquitetura de Hub e Spoke**

- Conecta várias VPCs, redes on-premises e contas AWS por meio de um único ponto centralizado.
- Suporte para milhares de conexões simultâneas sem a complexidade de gerenciar múltiplos túneis.

**2. Suporte a Multi-Conta**

- Integra-se com **AWS Organizations**, permitindo que contas dentro da mesma organização compartilhem e acessem o Transit Gateway.

**3. Roteamento Centralizado**

- Usa tabelas de roteamento associadas a cada VPC ou conexão on-premises para gerenciar o tráfego de maneira granular.
- Suporte para roteamento dinâmico com **Border Gateway Protocol (BGP)** para redes locais.

**4. Conectividade Global**

- Permite conectar Transit Gateways em diferentes regiões usando **Transit Gateway Peering**, possibilitando redes globais interligadas.

**5. Suporte a VPN e Direct Connect**

- Integra-se com **AWS Direct Connect** e VPNs para conexões de alta largura de banda e baixa latência com redes on-premises.

**6. Escalabilidade e Desempenho**

- Gerencia automaticamente a escalabilidade conforme o número de conexões e o tráfego aumentam.
- Projetado para oferecer baixa latência e alta disponibilidade.

**7. Segurança e Controle**

- Integra-se com **AWS Resource Access Manager (RAM)** para compartilhar o Transit Gateway entre contas com políticas de acesso específicas.
- Suporte para políticas de roteamento personalizadas e segmentação de tráfego.

**8. Monitoramento e Logs**

- Integração com **Amazon CloudWatch** para monitorar métricas de uso e desempenho.
- Suporte para logs detalhados de tráfego usando **Transit Gateway Flow Logs**.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança por hora para conexões ativas no Transit Gateway.
    - Taxas adicionais para transferência de dados entre VPCs ou com redes on-premises.
**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Transit Gateway como uma solução para conectar várias VPCs e redes on-premises de forma centralizada.
- Reconhecer sua capacidade de integrar-se com Direct Connect e VPNs para conectividade híbrida.
- Compreender o uso de roteamento centralizado e tabelas de roteamento personalizadas para simplificar a gestão de redes.