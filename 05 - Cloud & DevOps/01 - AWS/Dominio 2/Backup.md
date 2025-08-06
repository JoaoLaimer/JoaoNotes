[[Segurança e conformidade]]
Serviço gerenciado que centraliza e automatiza o backup de dados em serviços AWS, garantindo proteção, restauração e conformidade com políticas de retenção.
- **Backup Centralizado**: Permite gerenciar backups de diferentes serviços AWS a partir de um único console, incluindo Amazon [[EBS (Elastic Block Store)]], [[RDS (Relational Database Service)]], [[DynamoDB]], [[S3 (Simple Storage Service)]], [[EFS (Elastic File System)]], [[FSx]], e mais.
- **Automação**: Oferece agendamento automatizado para backups recorrentes, eliminando a necessidade de tarefas manuais.
- **Retenção e Políticas Personalizadas**: Suporte para políticas de retenção personalizáveis para atender a requisitos organizacionais e regulatórios.
- **Restauração Simples**: Facilita a restauração de backups em minutos, reduzindo o impacto de falhas ou exclusões acidentais.
- **Conformidade e Relatórios**: Monitora atividades de backup e gera relatórios detalhados para auditorias e conformidade com padrões como GDPR, SOC e HIPAA.
- **Cópias Entre Regiões e Contas**: Garante proteção adicional ao permitir cópias de backups em diferentes Regiões ou contas AWS, melhorando a recuperação de desastres.
- **Criptografia e Segurança**: Todos os backups são criptografados, e as permissões são gerenciadas via AWS IAM.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança com base na quantidade de dados armazenados nos backups (em GB por mês).
    - Custo adicional para transferências de backups entre Regiões ou contas AWS.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Backup como uma solução para gerenciar backups automatizados e centralizados.
- Compreender a importância de backups entre Regiões para recuperação de desastres.
- Reconhecer como o AWS Backup ajuda a manter conformidade regulatória com retenção de dados e auditorias.