[[Tecnologia e serviços da nuvem]]
Amazon VPC permite criar uma rede virtual isolada logicamente na AWS, onde você pode executar recursos, como instâncias EC2, com controle total sobre as configurações de rede, incluindo sub-redes, roteamento e segurança.
- **Sub-redes**: Divida a VPC em sub-redes públicas e privadas para segmentação de recursos com base na acessibilidade.
- **Controle de Roteamento**: Personalize tabelas de roteamento para direcionar o tráfego entre sub-redes, gateways e dispositivos on-premises.
- **Gateways de Internet e NAT**: Permitem que sub-redes públicas acessem a Internet e sub-redes privadas façam conexões de saída.
- **Peering de VPCs**: Conecta VPCs diferentes, mesmo em Regiões distintas, para compartilhar recursos.
- **VPN e Direct Connect**: Estabeleça conexões seguras entre sua VPC e redes on-premises.
- **Segurança Avançada**: Use grupos de segurança (Security Groups) para controlar o tráfego de entrada e saída em instâncias e listas de controle de acesso à rede (ACLs) para configurar regras adicionais em sub-redes.
- **Endereçamento IP**: Defina ranges de IPs (CIDR blocks) e integre-se com o Amazon Route 53 para gerenciamento DNS.
- **Endereços IP Elásticos**: Reserve e associe IPs públicos a instâncias para conexões estáveis e persistentes.
- **VPC Flow Logs**: Capture informações sobre o tráfego de entrada e saída na VPC para auditoria e monitoramento.
- **Integração com Outros Serviços AWS**: Conecta-se a serviços como Lambda, RDS, e ALB para isolar e proteger aplicativos.
- **Uma SUBNET VPC não pode estar admitida em mais de uma AZ** 
- **VPC Endpoint Gateway: Os endpoints da VPC de gateway fornecem conectividade confiável para o Amazon S3 e o DynamoDB sem a necessidade de um gateway da Internet ou um dispositivo NAT para sua VPC. Os endpoints de gateway não usam o AWS PrivateLink, ao contrário de outros tipos de endpoints da VPC.**
- **Security Groups so podem ter allow rule.**
- **NAT gateway e gerenciado pelo AWS.**
- **NAT instance e uma instancia que e usada como gateway para acesso a internet e sua performance depende do tipo de instancia, e gerenciado pelo cliente.**
**Modelo de Preços**:

- **Gratuito para Configuração da VPC**: Não há custo para criar VPCs ou sub-redes.
- **Pague pelo uso de recursos associados**:
    - Gateways NAT e IPs Elásticos têm custos.
    - Transferências de dados entre zonas de disponibilidade ou para fora da AWS geram cobranças adicionais.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon VPC como a base para criar redes isoladas na AWS.
- Reconhecer recursos como sub-redes, grupos de segurança e VPC Flow Logs como parte da configuração de redes seguras.
- Compreender como gateways de Internet e NAT conectam recursos a redes externas de forma controlada.