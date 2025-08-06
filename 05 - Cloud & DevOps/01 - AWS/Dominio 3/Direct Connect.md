[[Tecnologia e serviços da nuvem]]
AWS Direct Connect é um serviço que estabelece uma conexão de rede dedicada entre as instalações locais do cliente e a infraestrutura da AWS. Ele permite transferências de dados consistentes, seguras e de alta largura de banda, reduzindo custos e aumentando a eficiência para aplicações que exigem conectividade híbrida.
**1. Conexão de Rede Dedicada**

- Oferece conexões privadas e diretas com velocidades que variam de **50 Mbps** a **100 Gbps**.
- Reduz a dependência de conexões de internet pública para acessar recursos AWS.

**2. Compatibilidade com VPCs**

- Integra-se diretamente com **Amazon VPC**, permitindo que recursos locais acessem instâncias EC2, bancos de dados e outros serviços.
- Suporte a várias VPCs usando **Direct Connect Gateway** para maior escalabilidade.

**3. Redução de Latência e Consistência**

- Conexões mais consistentes e com menor latência em comparação com redes baseadas na internet.
- Ideal para workloads críticos e aplicações em tempo real.

**4. Segurança Avançada**

- Criptografia opcional com integração a VPNs para tráfego altamente sensível.
- Conexões privadas garantem maior segurança contra ameaças da internet pública.

**5. Modelos de Implementação**

- **Dedicated Connection**: Conexões físicas exclusivas fornecidas por provedores parceiros da AWS.
- **Hosted Connection**: Conexões compartilhadas por um provedor de serviços, com capacidade escalável.

**6. Conectividade Global**

- Permite acesso a qualquer Região AWS por meio de um único ponto de conexão usando o **Direct Connect Gateway**.
- Suporte para **Resilient Connectivity** com failover automático entre links redundantes.

**7. Transferência de Dados Eficiente**

- Reduz os custos de transferência de dados para fora da AWS em comparação com transferências realizadas pela internet.

**8. Monitoramento e Logs**

- Integração com **Amazon CloudWatch** para monitoramento de tráfego e desempenho da conexão.
- Logs detalhados para análise e otimização de conectividade.
**Modelo de Preços**:

- **Custo Fixo por Porta**:
    - Cobranças baseadas na velocidade da conexão escolhida (ex.: 1 Gbps ou 10 Gbps).
- **Transferência de Dados**:
    - Taxas reduzidas para transferências de dados entre a AWS e as instalações do cliente.
**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Direct Connect como uma solução para conectividade dedicada e segura com a AWS.
- Reconhecer sua integração com Amazon VPC e Direct Connect Gateway para redes híbridas.
- Compreender como ele reduz custos de transferência de dados e melhora a consistência de redes críticas.