[[Tecnologia e serviços da nuvem]]
AWS Snow Family é um conjunto de dispositivos físicos projetados para transferir grandes volumes de dados para a AWS, implantar computação na borda e operar em ambientes desconectados. Ele inclui **Snowcone**, **Snowball** e **Snowmobile**, cada um com capacidades específicas para diferentes cenários.
#### **Membros da Snow Family**

**1. AWS Snowcone**

- **Descrição**: Dispositivo portátil e compacto para transferências menores de dados e computação de borda.
- **Capacidade**: Até 8 TB de armazenamento.
- **Características**:
    - Resistente a condições adversas.
    - Executa cargas de trabalho locais com A**WS IoT Greengrass e Amazon EC2**.
    - Alimentado via tomada ou bateria.
    - Suporte para criptografia de dados e transferências offline ou online.
    - Ideal para coleta de dados no campo ou ambientes remotos.

**2. AWS Snowball**

- **Descrição**: Dispositivo para transferência de dados em escala média e computação na borda.
- **Tipos**:
    - **Snowball Edge Storage Optimized**: Até 80 TB de capacidade de armazenamento.
    - **Snowball Edge Compute Optimized**: Até 52 vCPUs, suporte para GPU e 42 TB de capacidade para cargas de trabalho de IA/ML.
- **Características**:
    - Transferência segura de grandes volumes de dados para a AWS.
    - Suporte para ambientes desconectados ou com conectividade limitada.
    - Integração com serviços de borda, como AWS IoT Greengrass e Lambda.

**3. AWS Snowmobile**

- **Descrição**: Caminhão customizado para transferir **exabytes de dados**.
- **Capacidade**: Até 100 PB por unidade.
- **Características**:
    - Projetado para migrações massivas de data centers.
    - Alta segurança com criptografia de ponta a ponta e vigilância física.
    - Operado por engenheiros AWS para transporte seguro de dados.
#### **Características Técnicas Gerais**:

- **Criptografia de Dados**: Todos os dispositivos usam criptografia AES-256 com gerenciamento de chaves via AWS KMS.
- **Transferência Offline e Online**: Dados podem ser transferidos fisicamente para a AWS ou sincronizados com o S3 via conexão de rede.
- **Computação Local**: Suporte para execução de cargas de trabalho na borda com EC2 e Lambda.
- **Resistência Física**: Dispositivos projetados para operar em condições adversas e locais remotos.
- **Rastreamento e Monitoramento**: Integração com AWS OpsHub para gerenciar e monitorar dispositivos Snow Family.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobranças baseadas no número de dispositivos usados, duração do aluguel e serviços adicionais, como suporte técnico.
    - Snowmobile tem custos personalizados para projetos de grande escala.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar membros da Snow Family e seus propósitos, como Snowcone para cargas menores, Snowball para transferência em escala média e Snowmobile para migrações massivas.
- Reconhecer o uso de criptografia e segurança física como diferenciais para transferência de dados.
- Compreender como a Snow Family facilita migrações e soluções de borda em ambientes desconectados.