[[Segurança e conformidade]]
Estratégia e conjunto de práticas para restaurar sistemas críticos e minimizar interrupções em caso de falhas ou desastres, utilizando os serviços e infraestrutura da AWS.

**Estratégias Comuns de Recuperação de Desastres**:

- **Backup and Restore**:
    
    - Os dados são regularmente salvos (backups) e restaurados em caso de necessidade.
    - **Ideal para**: Sistemas onde o tempo de recuperação (RTO - Recovery Time Objective) não é crítico.
    - **Serviços Relacionados**: AWS Backup, Amazon S3, S3 Glacier, e AWS Storage Gateway.
- **Pilot Light**:
    
    - Uma versão mínima do ambiente está sempre em execução, pronta para ser escalada rapidamente em caso de falha.
    - **Ideal para**: Ambientes que requerem uma recuperação mais rápida, mas com custos reduzidos.
    - **Serviços Relacionados**: Amazon EC2, Auto Scaling, Amazon RDS.
- **Warm Standby**:
    
    - Um ambiente reduzido está ativo e pode ser rapidamente escalado para produção.
    - **Ideal para**: Sistemas que precisam de menor tempo de recuperação com algum custo adicional.
    - **Serviços Relacionados**: Elastic Load Balancing (ELB), Route 53, RDS Multi-AZ.
- **Multi-Site Active-Active**:
    
    - Múltiplas instâncias do sistema estão ativas em Regiões diferentes, oferecendo disponibilidade contínua.
    - **Ideal para**: Ambientes críticos onde o tempo de inatividade é inaceitável.
    - **Serviços Relacionados**: Amazon Route 53 (failover), AWS Global Accelerator, S3 Cross-Region Replication.

**Serviços Importantes para Recuperação de Desastres**:

- **Amazon S3**: Armazenamento seguro e escalável para backups e replicações de dados.
- **AWS Backup**: Centraliza e automatiza backups com políticas de retenção e replicação entre Regiões.
- **AWS Elastic Disaster Recovery (AWS DRS)**: Automatiza a recuperação de sistemas on-premises ou na nuvem com failover rápido.
- **Amazon RDS Multi-AZ**: Oferece failover automático para cópias secundárias em caso de falhas no banco de dados primário.
- **Amazon Route 53**: Gerencia failover DNS para redirecionar tráfego automaticamente durante interrupções.
- **AWS Snow Family**: Para transferência de grandes volumes de dados em ambientes desconectados ou de conectividade limitada.

**Modelo de Preços**:

- **Baseado no uso**:
    - Custos relacionados ao armazenamento (ex.: S3, S3 Glacier).
    - Recursos computacionais ativos (ex.: EC2, RDS).
    - Replicação entre Regiões e tráfego de rede em caso de failover.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar diferentes estratégias de recuperação de desastres (Backup and Restore, Pilot Light, Warm Standby, Multi-Site).
- Reconhecer como serviços como AWS Backup, Route 53 e Elastic Disaster Recovery ajudam na continuidade dos negócios.
- Compreender os benefícios de replicação entre Regiões para mitigar desastres localizados.