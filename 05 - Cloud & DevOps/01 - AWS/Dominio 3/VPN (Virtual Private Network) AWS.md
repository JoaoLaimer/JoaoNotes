[[Tecnologia e serviços da nuvem]]
AWS VPN é uma solução que permite conexões seguras entre redes locais ou dispositivos remotos e a infraestrutura AWS. Ele inclui duas opções principais: **AWS Site-to-Site VPN** para conectar redes locais a VPCs e **AWS Client VPN** para acesso remoto seguro.
**1. AWS Site-to-Site VPN**

- **Conexão Criptografada**: Estabelece túneis IPsec entre redes locais ou on-premises e VPCs da AWS.
- **Suporte Multi-Região e Multi-VPC**: Funciona com **AWS Transit Gateway** para conectar múltiplas VPCs ou Regiões.
- **Tolerância a Falhas**: Cada conexão inclui dois túneis redundantes para maior disponibilidade e failover automático.
- **Gerenciamento Simples**: Fácil configuração por meio do console AWS, CLI ou APIs.
- **Compatibilidade com Dispositivos**: Suporte a roteadores de terceiros e appliances de rede compatíveis com IPsec.

**2. AWS Client VPN**

- **Acesso Remoto Seguro**: Permite que usuários se conectem a redes AWS ou locais de qualquer lugar por meio de VPNs baseadas em SSL.
- **Autenticação Personalizável**: Integração com AWS IAM, Active Directory e provedores de identidade SAML para autenticação segura.
- **Escalabilidade Automática**: Capacidade de atender um grande número de conexões simultâneas.
- **Gerenciamento Multi-Conta**: Compatível com AWS Organizations para gerenciamento centralizado de usuários.

**3. Segurança e Criptografia**

- Usa padrões avançados de criptografia, como AES-256, para proteger o tráfego em trânsito.
- Integração com **AWS KMS** para gerenciamento de chaves de criptografia.

**4. Monitoramento e Logs**

- Integração com **Amazon CloudWatch** e **AWS CloudTrail** para rastrear conexões, logs de atividade e métricas de desempenho.
- Suporte para monitoramento de latência, pacotes descartados e falhas de conexão.

**5. Configuração Flexível**

- Compatível com roteamento estático e dinâmico via **Border Gateway Protocol (BGP)**.
- Possibilidade de configurar diferentes sub-redes para separar tráfego interno e externo.
**Modelo de Preços**:

- **Site-to-Site VPN**:
    - Custos baseados por hora por conexão de VPN ativa.
    - Taxas adicionais para transferência de dados.
- **Client VPN**:
    - Cobrança baseada no número de horas de associação ao ponto de extremidade e no número de conexões simultâneas.
**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS VPN como uma solução para conexões seguras entre redes locais e AWS (Site-to-Site VPN).
- Reconhecer o AWS Client VPN como uma opção para acesso remoto seguro a recursos AWS e on-premises.
- Compreender como ele fornece alta segurança com criptografia avançada e redundância para conexões críticas.