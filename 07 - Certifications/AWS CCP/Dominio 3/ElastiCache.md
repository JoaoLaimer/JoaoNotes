[[Tecnologia e serviços da nuvem]]
Amazon ElastiCache é um serviço gerenciado de armazenamento em cache na memória que melhora o desempenho de aplicativos, oferecendo tempos de resposta ultrarrápidos ao armazenar dados frequentemente acessados em memória. Ele suporta **Redis** e **Memcached**, dois mecanismos populares de caching.
- **Suporte a Redis e Memcached**: Redis para casos de uso mais avançados (persistência, replicação) e Memcached para caching simples e distribuído.
- **Baixa Latência**: Fornece tempos de resposta em microssegundos, ideal para aplicativos que exigem alta performance.
- **Escalabilidade**: Suporte a escalabilidade horizontal (sharding) e vertical (aumento de nós) para lidar com cargas de trabalho maiores.
- **Replicação e Failover Automático**: Redis suporta réplicas para alta disponibilidade e failover automático em caso de falha do nó primário.
- **Monitoramento**: Integração com Amazon CloudWatch para rastrear métricas como uso de memória, hits no cache e taxa de evicção.
- **Persistência de Dados**: Redis oferece persistência opcional para salvar dados em disco, garantindo recuperação em caso de falhas.
- **Segurança**: Suporte para criptografia de dados em trânsito e em repouso, isolamento com Amazon VPC e controle de acesso detalhado com IAM.
- **Gerenciamento Simplificado**: Automatiza tarefas como atualizações de software, recuperação de nós e backups.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no tipo e número de nós, armazenamento usado e transferência de dados.
    - Nós maiores ou clusters com mais réplicas têm custos proporcionais.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon ElastiCache como uma solução para melhorar a performance de aplicativos com caching na memória.
- Reconhecer as diferenças entre Redis (alta disponibilidade e persistência) e Memcached (simplicidade e caching distribuído).
- Compreender como o ElastiCache reduz a carga em bancos de dados subjacentes e melhora o desempenho geral.