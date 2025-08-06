[[Segurança e conformidade]]
AWS Network Firewall é um serviço gerenciado que oferece proteção contra ameaças de rede em VPCs. Ele permite inspecionar, filtrar e monitorar tráfego de rede para proteger aplicativos e dados, utilizando regras de firewall configuráveis e padrões conhecidos de segurança.
**1. Regras de Firewall Personalizáveis**

- **Regras de Controle de Tráfego**: Definição de regras para permitir, bloquear ou inspecionar tráfego com base em endereços IP, portas e protocolos.
- **Inspeção de Stateful e Stateless**:
    - **Stateful**: Mantém o contexto da conexão para decisões mais precisas.
    - **Stateless**: Avaliação independente de cada pacote.
- **Regras Baseadas em Domínios**: Inspeciona tráfego com base em nomes de domínio, permitindo ou bloqueando o acesso a URLs específicas.

**2. Integração com AWS Managed Rules**

- Conjuntos de regras gerenciadas pela AWS ou fornecedores terceiros para proteção contra ameaças comuns.

**3. Proteção Avançada Contra Ameaças**

- Suporte para detecção e prevenção de intrusões (IDS/IPS) baseado em padrões conhecidos de ataques.
- Integração com logs de fluxo e análise para identificar comportamentos suspeitos.

**4. Integração com VPCs**

- Funciona com **VPC Traffic Mirroring** e **AWS Transit Gateway** para monitorar e filtrar tráfego de rede.
- Configuração simplificada por meio de políticas associadas a sub-redes específicas em uma VPC.

**5. Segurança e Conformidade**

- Criptografia de tráfego e suporte para auditoria com **AWS CloudTrail** e **CloudWatch Logs**.
- Alinhamento com requisitos de conformidade, como PCI DSS e HIPAA.

**6. Escalabilidade e Alta Disponibilidade**

- Escala automaticamente para lidar com grandes volumes de tráfego sem interrupção do serviço.
- Alta disponibilidade com redundância em várias zonas de disponibilidade (AZs).

**7. Monitoramento e Log de Atividades**

- Integração com **Amazon CloudWatch** para métricas em tempo real.
- **Flow Logs** detalhados para análise e geração de relatórios.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no número de firewalls ativos, gigabytes processados e regras configuradas.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Network Firewall como uma solução para proteger redes em VPCs contra tráfego malicioso.
- Reconhecer suas capacidades de inspeção de estado (stateful) e prevenção de intrusões (IDS/IPS).
- Compreender como ele se integra com outros serviços AWS, como CloudWatch, para monitoramento e segurança.