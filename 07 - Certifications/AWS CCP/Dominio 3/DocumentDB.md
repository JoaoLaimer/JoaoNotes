[[Tecnologia e serviços da nuvem]]
Amazon DocumentDB é um serviço gerenciado de banco de dados de documentos baseados em formato JSON que oferece alta performance, escalabilidade e compatibilidade com MongoDB. Ele é projetado para lidar com workloads de dados semi-estruturados ou não estruturados em larga escala.

- **Compatibilidade com MongoDB**: Oferece suporte para drivers e ferramentas do MongoDB, permitindo que aplicativos existentes sejam migrados com alterações mínimas.
- **Escalabilidade Automática**: Ajusta automaticamente a capacidade de armazenamento em incrementos de 10 GB, até 64 TB.
- **Replicação Automática**: Replicação em três zonas de disponibilidade (AZs) para alta disponibilidade e durabilidade dos dados.
- **Consultas em Tempo Real**: Processa consultas rapidamente usando índices otimizados para dados semi-estruturados.
- **Backup Contínuo e Recuperação Point-in-Time**: Permite restaurar dados em qualquer ponto dos últimos 35 dias.
- **Gerenciamento Simplificado**: Automatiza tarefas como backups, atualizações de software e failovers.
- **Segurança Avançada**: Suporte para criptografia de dados em repouso com AWS KMS, criptografia em trânsito com TLS e controle de acesso com AWS IAM.
- **Monitoramento e Diagnóstico**: Integração com Amazon CloudWatch para rastrear métricas de desempenho, uso de recursos e integridade do cluster.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no tipo e tamanho das instâncias, volume de armazenamento provisionado, IOPS e transferências de dados.
    - Os backups contínuos e a recuperação point-in-time geram custos adicionais.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon DocumentDB como uma solução gerenciada para bancos de dados compatíveis com MongoDB.
- Reconhecer seus benefícios em escalabilidade automática, alta disponibilidade e recuperação de dados.
- Compreender como ele reduz o esforço operacional ao automatizar tarefas de manutenção e gerenciamento.