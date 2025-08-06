[[Tecnologia e serviços da nuvem]]
AWS Elastic Disaster Recovery (DRS) é um serviço gerenciado que simplifica e automatiza o processo de recuperação de desastres, permitindo restaurar rapidamente aplicativos e sistemas para a AWS em caso de falhas. Ele replica dados e configurações de servidores físicos, virtuais ou em nuvem para a infraestrutura da AWS, garantindo continuidade operacional.

**1. Recuperação Automática**

- Automatiza a restauração de sistemas com tempos de recuperação (RTO) rápidos, geralmente de minutos.
- Suporte para ambientes físicos, VMware, Hyper-V, Microsoft Azure e Google Cloud.

**2. Replicação Contínua de Dados**

- Sincroniza dados em tempo real para evitar perda significativa em caso de falha (RPO baixo).
- Transferência de dados criptografados para instâncias EC2 no formato nativo AWS.

**3. Recuperação Point-in-Time**

- Suporte para múltiplos pontos de recuperação, permitindo restaurar dados em momentos específicos no tempo.

**4. Escalabilidade Automática**

- Adapta-se automaticamente às necessidades de recuperação, garantindo que recursos AWS sejam alocados conforme necessário.

**5. Suporte a Aplicações Críticas**

- Permite a recuperação de sistemas operacionais, bancos de dados e aplicativos corporativos como SAP, Oracle e Microsoft SQL Server.

**6. Testes de Recuperação Sem Interrupções**

- Executa testes regulares de recuperação para validar a preparação para desastres sem impactar sistemas de produção.

**7. Integração com Outros Serviços AWS**

- Funciona com Amazon CloudWatch para monitoramento e alertas.
- Suporte a VPCs, Load Balancers e Auto Scaling para restaurar arquiteturas completas.

**8. Criptografia e Conformidade**

- Transferência e armazenamento de dados criptografados com chaves gerenciadas pelo cliente ou AWS KMS.
- Compatível com regulamentações como GDPR, HIPAA e PCI DSS.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança por servidores protegidos.
    - Custos adicionais por armazenamento de dados e recursos provisionados durante o evento de recuperação.

---

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Elastic Disaster Recovery como uma solução para recuperação de desastres gerenciada e rápida.
- Reconhecer sua capacidade de replicar dados em tempo real e oferecer recuperação point-in-time.
- Compreender como ele reduz o custo e a complexidade em comparação com soluções tradicionais de DR.