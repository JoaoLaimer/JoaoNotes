[[Segurança e conformidade]]
AWS WAF é um firewall para aplicativos web que protege contra vulnerabilidades comuns, como injeções de SQL, ataques de script entre sites (XSS) e tentativas de exploração de APIs. Ele permite criar regras personalizadas para filtrar tráfego malicioso antes que atinja seus aplicativos.
- **Regras Personalizáveis**: Permite criar regras específicas para bloquear, permitir ou monitorar tráfego baseado em padrões de IP, cabeçalhos HTTP, URI, entre outros.
- **Managed Rules**: Oferece conjuntos de regras gerenciadas pela AWS ou por parceiros, otimizadas para proteção contra ameaças comuns.
- **Proteção DDoS (com Shield)**: Integração com AWS Shield para mitigar ataques DDoS em conjunto com WAF.
- **Escalabilidade Automática**: Adapta-se automaticamente ao volume de tráfego, suportando ambientes de alta demanda.
- **Suporte Multi-Serviço**: Funciona com Amazon CloudFront, Application Load Balancer (ALB), e API Gateway para proteger diferentes tipos de aplicativos e APIs (AppSync).
- **Análise de Logs**: Integração com Amazon Kinesis Data Firehose para exportar logs detalhados de tráfego para análise.
- **Bot Control**: Detecta e gerencia bots automatizados com políticas específicas para bloquear ou permitir suas interações.
- **Fácil Gerenciamento**: Interface intuitiva no console da AWS e suporte para APIs para automação de regras.
- O WAF não pode ser instanciado em um **EC2**. 
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no número de regras criadas e no volume de solicitações processadas.
    - Managed Rules e Bot Control têm custos adicionais, dependendo das políticas aplicadas.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS WAF como uma solução para proteger aplicativos web contra ameaças e vulnerabilidades comuns.
- Reconhecer sua integração com CloudFront, ALB e API Gateway para proteção de ponta a ponta.
- Compreender o uso de Managed Rules e como elas facilitam a implementação de segurança rapidamente.