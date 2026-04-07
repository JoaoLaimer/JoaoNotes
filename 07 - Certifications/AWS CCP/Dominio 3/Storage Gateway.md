[[Tecnologia e serviços da nuvem]]
Serviço híbrido que conecta ambientes on-premises à nuvem AWS, permitindo que dados locais sejam armazenados, acessados e gerenciados na nuvem de forma segura e integrada.
- **Modos de Operação**:
    
    1. **File Gateway**: Permite armazenamento de arquivos no Amazon S3 usando protocolos NFS ou SMB, com acesso rápido e escalável.
    2. **Tape Gateway**: Substitui sistemas de fitas físicas por armazenamento em S3 Glacier ou S3 Glacier Deep Archive, ideal para backups e arquivamento.
    3. **Volume Gateway**: Armazena dados em volumes locais com snapshots no S3 e recuperação completa via Amazon EBS.
- **Integração com Serviços AWS**:
    
    - Snapshots de volumes são salvos no Amazon S3 e podem ser usados para criar volumes EBS.
    - Dados armazenados podem ser analisados com Amazon Athena ou transferidos para outros serviços AWS.
- **Cache Local**: Oferece cache local para acesso rápido aos dados mais frequentemente usados, reduzindo a latência.
    
- **Gerenciamento Simples**: Configuração e monitoramento centralizados no console AWS Storage Gateway.
    
- **Segurança Avançada**: Suporte para criptografia em trânsito e em repouso, com gerenciamento de permissões via AWS IAM.
    
- **Escalabilidade**: Os dados podem crescer dinamicamente no S3 sem limitações de capacidade.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no tipo de gateway utilizado (File, Tape, ou Volume Gateway).
    - Taxas para armazenamento em S3, recuperação de dados, transferências entre Regiões e snapshots de volumes.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Reconhecer o AWS Storage Gateway como uma solução para conectar ambientes locais à nuvem AWS.
- Identificar os diferentes modos de operação (File, Tape, Volume) e seus casos de uso.
- Compreender como o serviço facilita backup, arquivamento e recuperação de dados em ambientes híbridos.