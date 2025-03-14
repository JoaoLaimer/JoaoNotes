[[Tecnologia e serviços da nuvem]]
Serviço de rede que melhora a disponibilidade, performance e resiliência de aplicativos globais ao direcionar tráfego de usuários para endpoints AWS mais próximos e disponíveis usando a rede global da AWS.
- **Pontos de Presença Globais**: Usa a infraestrutura da AWS para fornecer dois endereços IP estáticos que atuam como pontos de entrada para o tráfego, independentemente do endpoint em uso.
- **Roteamento Inteligente**: Direciona automaticamente os usuários para os endpoints mais próximos e disponíveis com base em latência, carga e saúde do endpoint.
- **Failover Automático**: Redireciona tráfego de forma automática e instantânea em caso de falha de um endpoint, garantindo alta disponibilidade.
- **Suporte Multi-Regional**: Facilita a implantação de aplicativos em várias Regiões AWS, mantendo alta performance para usuários em todo o mundo.
- **Integração com Outros Serviços AWS**: Funciona bem com Elastic Load Balancers (ELB), EC2, ECS e outros serviços que precisam de roteamento global eficiente.
- **Controle de Tráfego**: Permite definir pesos para balancear a distribuição de tráfego entre endpoints.
- **Suporte a Protocolos Diversos**: Trabalha com tráfego TCP e UDP, adequado para aplicativos de baixa latência, como jogos, VoIP e streaming.
- **Prove um IP estático** que serve como um ponte de entrada para a aplicação.
- **Melhor para casos não HTTP, como (UDP)**
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no tempo de uso do Global Accelerator (em horas).
    - Taxa adicional para transferência de dados por GB trafegado pela rede global da AWS.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Global Accelerator como uma solução para melhorar a performance e disponibilidade de aplicativos globais.
- Reconhecer a diferença entre Global Accelerator e Amazon CloudFront (CloudFront é focado em distribuição de conteúdo em cache, enquanto Global Accelerator é para roteamento global de tráfego).
- Compreender como o failover automático mantém a continuidade do serviço em caso de falhas regionais.