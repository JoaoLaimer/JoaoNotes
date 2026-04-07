[[Tecnologia e serviços da nuvem]]
Amazon S3 é um serviço de armazenamento de objetos altamente escalável, durável (**11 9s**) e seguro, projetado para armazenar e recuperar qualquer quantidade de dados a qualquer momento, de qualquer lugar.
- **Armazenamento Baseado em Objetos**: Ideal para dados não estruturados como arquivos, imagens, backups e logs.
- **Classes de Armazenamento**:
    - **S3 Standard**: Para dados acessados com frequência, **não possui cobrança por retrieval, capacidade minima e duração.** 
    - **S3 Intelligent-Tiering**: Alterna automaticamente entre camadas de custo com base no padrão de acesso, **não possui cobrança por retrieval, capacidade minima e duração.** 
    - **S3 Standard-IA (Infrequent Access)**: Para dados acessados esporadicamente, mas que precisam de baixa latência,  **possui cobrança por retrieval por GB, duração minima de 30 dias e minima capacidade de 128kb.**
    - **S3 One Zone-IA**: Menor custo para dados acessados raramente e armazenados em uma única AZ, **possui cobrança por retrieval por GB, duração minima de 30 dias e minima capacidade de 128kb.**
    - **S3 Glacier e Glacier Deep Archive**: Para arquivamento de dados com recuperação lenta e custo reduzido.
    - Dados são encriptados automaticamente. 
	    - Glacier Instant Retrieval: acesse em milisegundos. **possui cobrança por retrieval por GB, duração minima de 90 dias e minima capacidade de 128kb.**
	    - Glacier Flexible Retrieval:
		    - **possui cobrança por retrieval por GB, duração minima de 90 dias e minima capacidade de 40kb.**
		    - Expedited: acesse arquivos em 1-5 minutos
		    - Standard: 3-5 horas
		    - Bulk: 5-12
		-  Glacier Deep Archive:
			- **possui cobrança por retrieval por GB, duração minima de 180 dias e minima capacidade de 40kb.**
			- Standard: 12 horas
			- Bulk: 45 horas
- **Versionamento**: Mantém várias versões de objetos para recuperação de dados excluídos ou alterados acidentalmente.
- **Controle de Acesso**: Gerencie permissões com AWS IAM, políticas de bucket e listas de controle de acesso (ACLs).
- **Replication**: Suporte a replicação de objetos entre Regiões (CRR) e dentro de uma mesma região (SRR).
- **Criptografia**:
	- O usuario deve ativar
    - Criptografia de dados em repouso com SSE (Server-Side Encryption) usando AWS KMS, SSE-C ou SSE-S3.
    - Criptografia de dados em trânsito com HTTPS.
- **Integração com Outros Serviços AWS**: Trabalha com serviços como Lambda, Athena, Glue e Snowball para análises, processamento e transferência de dados.
- **Eventos S3**: Gatilhos automáticos para ações em tempo real usando Lambda ou SQS.
- **Monitoramento e Logs**: Integração com AWS CloudTrail e CloudWatch para auditoria e monitoramento de atividades.
- **Estrutura flat non-hierarchical.**
- **Storage Lens**: Ferramenta de análise que fornece insights detalhados sobre o uso de armazenamento S3.
- **Tamanho**: Virtualmente Infinito.
- **S3 Lifecycle**: Transiciona objetos por Storage Classes.
- **S3 Object Lock**: Previne que objetos sejam deletados ou sobrescritos por um tempo ou indefinitivamente, ajuda a manter regulamentos, WORM (write-once-read-many).
- **S3 Replication**: Replica objetos e seus meta dados e tags, para um ou mais buckets.
- **S3 Batch Operations**: Gerencia bilhões de objetos com uma unica request API S3.


**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança por GB armazenado, solicitações (PUT, GET) e transferência de dados.
    - Classes de armazenamento e replicação podem gerar custos adicionais.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon S3 como uma solução de armazenamento de objetos escalável e seguro.
- Reconhecer as classes de armazenamento e quando utilizá-las para otimizar custos.
- Compreender a integração com outros serviços AWS para automação e processamento de dados.