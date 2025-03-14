[[Tecnologia e serviços da nuvem]]
AWS DataSync é um serviço gerenciado que automatiza a movimentação de dados entre armazenamento local, NFS, SMB ou Hadoop (HDFS) e serviços de armazenamento na AWS, como S3, EFS e FSx. Ele é projetado para transferências rápidas, seguras e eficientes de grandes volumes de dados.
- **Transferência Rápida**: Otimizado para mover dados em alta velocidade, com até 10 vezes a performance de ferramentas tradicionais.
- **Automação de Tarefas**: Automatiza o agendamento, monitoramento e validação de transferências, reduzindo esforço manual.
- **Suporte a Diversos Protocolos**: Compatível com NFS, SMB e HDFS para conectar fontes de dados locais ou na nuvem.
- **Validação de Dados**: Garante a integridade dos dados durante e após a transferência com validação automática.
- **Bidirecionalidade**: Suporte a transferências de dados tanto para dentro quanto para fora da AWS.
- **Segurança Integrada**: Transfere dados criptografados em trânsito usando TLS, com controle de acesso gerenciado por AWS IAM.
- **Monitoramento Detalhado**: Integração com Amazon CloudWatch para rastrear métricas, logs e status de transferências.
- **Integração com Serviços AWS**: Movimenta dados diretamente para S3, EFS e FSx for Windows File Server.
- **Escalabilidade**: Permite transferir grandes volumes de dados, ajustando-se automaticamente à carga de trabalho.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no volume de dados transferidos por GB.
    - Custos adicionais podem surgir dependendo dos serviços de destino usados, como S3 ou EFS.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS DataSync como uma solução para mover dados entre ambientes locais e a nuvem AWS.
- Reconhecer sua eficiência em transferências rápidas e seguras de grandes volumes de dados.
- Compreender como ele reduz a complexidade e o esforço operacional em migrações de dados.