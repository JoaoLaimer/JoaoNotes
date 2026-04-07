[[Segurança e conformidade]]
AWS Shield é um serviço gerenciado de proteção contra ataques **Distributed Denial of Service (DDoS)**. Ele protege aplicativos e recursos hospedados na AWS, garantindo disponibilidade e resiliência contra ataques maliciosos.

**1. Duas Camadas de Proteção**

- **Shield Standard** (Gratuito):
    
    - Proteção automática contra ataques DDoS comuns, como volumétricos e de reflexão, para todos os serviços AWS.
    - Integração com serviços como **Elastic Load Balancing (ELB)**, **CloudFront** e **Route 53**.
    - É automaticamente ativado para todos os clientes AWS sem opções de customização, assim **gerenciado pelo AWS**.
- **Shield Advanced** (Pago):
    
    - Proteção mais robusta contra ataques sofisticados e direcionados.
    - Mitigação personalizada com monitoramento em tempo real.
    - Acesso 24/7 à **AWS DDoS Response Team (DRT)** para suporte especializado durante ataques.
    - **Cobertura Financeira**: Reembolso de custos adicionais causados por ataques, como transferência de dados.
    - Detecção aprimorada e mitigação automática para aplicativos personalizados.
    - Abrange, **Amazon Elastic Compute Cloud, Elastic Load Balancing (ELB), Amazon CloudFront, Amazon Route 53, AWS Global Accelerator, EC2.** 

**2. Mitigação Automática**

- Detecta e mitiga ataques automaticamente, sem necessidade de intervenção manual.
- Funciona em conjunto com **AWS WAF** para aplicar regras personalizadas de proteção.

**3. Monitoramento e Análise**

- **Real-Time Metrics**: Métricas detalhadas de tráfego e eventos de segurança no **Amazon CloudWatch**.
- **Threat Environment Dashboard**: Insights sobre tendências de ataques em escala global.

**4. Suporte Multi-Região e Multi-Conta**

- Protege recursos em todas as regiões da AWS com políticas centralizadas, especialmente para ambientes multi-conta.

**5. Integração com Outros Serviços AWS**

- Trabalha com **CloudFront**, **Route 53**, e **Global Accelerator** para reduzir latência e proteger aplicativos distribuídos.
- Integração com **VPC Traffic Mirroring** para analisar tráfego suspeito.
**Modelo de Preços**:

- **Shield Standard**: Gratuito para todos os clientes AWS.
- **Shield Advanced**:
    - Taxa fixa mensal por conta (atualmente $3.000 por mês).
    - Custos adicionais com base na largura de banda protegida.
**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Shield como a solução para proteger contra ataques DDoS.
- Diferenciar entre Shield Standard (proteção básica gratuita) e Shield Advanced (proteção paga com suporte e recursos avançados).
- Reconhecer sua integração com AWS WAF, CloudFront e Route 53 para proteção de ponta a ponta.