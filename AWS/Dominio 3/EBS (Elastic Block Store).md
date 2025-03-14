[[Tecnologia e serviços da nuvem]]
Serviço de armazenamento em bloco de alta performance, projetado para ser usado com instâncias EC2 para cargas de trabalho que exigem acesso rápido e consistente a dados.
- **Tipos de Volumes**:
    - **General Purpose SSD (gp3, gp2)**: Balanceia preço e performance, ideal para aplicações gerais.
    - **Provisioned IOPS SSD (io2, io1)**: Alta performance para aplicações críticas, como bancos de dados.
    - **Throughput Optimized HDD (st1)**: Armazenamento otimizado para grandes volumes de dados sequenciais, como logs e big data.
    - **Cold HDD (sc1)**: Alternativa econômica para dados acessados raramente.
- **Snapshot de Dados**: Permite criar backups incrementais armazenados no Amazon S3 para recuperação ou replicação.
- **Redimensionamento Flexível**: Volumes podem ser redimensionados dinamicamente sem tempo de inatividade, ajustando capacidade e performance.
- **Criptografia Integrada**: Oferece criptografia de dados em repouso e em trânsito com AWS Key Management Service (KMS).
- **Alta Disponibilidade e Durabilidade**: Projetado para replicação em múltiplos servidores na mesma Zona de Disponibilidade.
- **Multi-Attach**: Permite que volumes io2 sejam anexados a várias instâncias EC2 simultaneamente (para workloads específicos).
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no tamanho do volume alocado (em GB por mês).
    - Custos adicionais para IOPS provisionados em tipos como io1 e io2.
    - Snapshots são cobrados pelo armazenamento no S3.
    - Transferências entre zonas ou Regiões podem gerar custos adicionais.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon EBS como uma solução de armazenamento persistente para instâncias EC2.
- Reconhecer os diferentes tipos de volumes (gp3, io2, st1, sc1) e seus casos de uso.
- Compreender o benefício de snapshots para backup e recuperação de volumes EBS.