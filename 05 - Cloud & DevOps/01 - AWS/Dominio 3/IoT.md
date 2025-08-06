[[Tecnologia e serviços da nuvem]]
O **AWS IoT** é um conjunto de serviços projetados para conectar, gerenciar e operar dispositivos de **Internet das Coisas (IoT)** de forma segura. Ele fornece a infraestrutura para coletar, processar e analisar dados de dispositivos, bem como integrar esses dispositivos a outros serviços AWS.

---

### Características Técnicas

- **Conectividade e Gerenciamento de Dispositivos**:
    
    - **AWS IoT Core**: Conecta dispositivos ao AWS Cloud usando protocolos como MQTT, HTTP e WebSockets.
    - **Device Shadow**: Permite estados persistentes para dispositivos, mesmo quando offline.
    - **Registry**: Registro de dispositivos que armazena informações como IDs e atributos.
- **Segurança**:
    
    - **Autenticação e Autorização**: Uso de certificados X.509, chaves públicas/privadas e **IAM** para controle de acesso.
    - **Criptografia**: Comunicação entre dispositivos e AWS é criptografada.
    - **AWS IoT Device Defender**: Identifica e remedia vulnerabilidades de segurança.
- **Processamento de Dados**:
    
    - **IoT Analytics**: Permite análise de dados coletados de dispositivos.
    - **IoT Greengrass**: Extende serviços AWS para dispositivos locais, suportando execução de funções **Lambda** no edge.
- **Machine Learning**:
    
    - Integração com **Amazon SageMaker** para criar e implantar modelos de aprendizado de máquina com base nos dados dos dispositivos.
    - **IoT Events**: Detecta padrões e aciona ações com base em eventos definidos.
- **Integração com Outros Serviços**:
    
    - Suporte nativo para **AWS Lambda**, **Amazon Kinesis**, **Amazon S3**, **DynamoDB** e **CloudWatch** para armazenamento, processamento e monitoramento de dados.
    - Permite integração com **Amazon SNS** e **SQS** para notificações e filas.

---

### Informações Extras

- O **AWS IoT Core** permite conectar **milhões de dispositivos** de maneira simultânea.
- Suporta execução de regras personalizadas através de **AWS IoT Rules Engine**, permitindo direcionar mensagens para serviços AWS.
- O uso de **Device Shadow** é importante para sincronizar estados de dispositivos em tempo real e offline.
- **AWS IoT SiteWise** facilita a coleta e análise de dados de dispositivos industriais.
- Suporta **detecção de anomalias** com **IoT Device Advisor**.

---

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **AWS IoT** abrange vários subserviços:

- **IoT Core**: Conexão e gerenciamento de dispositivos.
- **IoT Greengrass**: Processamento local de dados e execução de funções Lambda no edge.
- **IoT Analytics**: Análise avançada de dados coletados.
- **IoT Events**: Automação baseada em eventos.
- **IoT Device Defender**: Segurança para dispositivos IoT.
- **IoT SiteWise**: Coleta e organização de dados industriais.

---

### Custos

- **Modelo de Custos**:
    - Cobrança baseada no número de mensagens enviadas ou recebidas no **IoT Core**.
    - **IoT Analytics** cobra pelo processamento e armazenamento de dados.
    - **IoT Greengrass** pode ter custos adicionais para execução de funções locais.
    - Custo para uso de **certificados de dispositivos** e uso de recursos do **Rules Engine**.

---

### Casos de Uso Comuns no Exame

- Identificar como conectar dispositivos IoT ao AWS Cloud usando o **IoT Core**.
- Reconhecer o papel do **Device Shadow** para manter o estado persistente de dispositivos offline.
- Diferenciar entre serviços como **IoT Greengrass** (processamento local) e **IoT Analytics** (análise na nuvem).
- Analisar como o **IoT Events** pode ser usado para automatizar ações baseadas em condições específicas.
- Configurar permissões de segurança e criptografia com **IoT Device Defender**.