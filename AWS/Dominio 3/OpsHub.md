[[Tecnologia e serviços da nuvem]]
O **AWS OpsHub** é a ferramenta gráfica oficial para gerenciar dispositivos da **AWS Snow Family**, permitindo configuração, monitoramento e operação de dispositivos como **AWS Snowcone**, **AWS Snowball Edge**, e **AWS Snowmobile**. Ele oferece uma interface simples e intuitiva, eliminando a necessidade de usar a CLI ou APIs para tarefas comuns.

---

### Características Técnicas

- **Interface Visual Intuitiva**:
    
    - Configuração rápida de dispositivos Snow Family, incluindo inicialização, configuração de rede e habilitação de recursos edge.
    - Monitoramento em tempo real do status dos dispositivos e transferências de dados.
- **Transferência de Dados Segura**:
    
    - Suporte para configurar tarefas de transferência de dados entre o dispositivo e o **Amazon S3**.
    - **Criptografia habilitada por padrão**: Todos os dados armazenados no dispositivo são criptografados usando chaves gerenciadas pelo cliente no AWS Key Management Service (KMS).
- **Gerenciamento Offline**:
    
    - Permite que dispositivos sejam configurados e operados em ambientes sem conectividade direta com a AWS.
    - Configuração inicial e monitoramento local do dispositivo sem necessidade de acesso à internet.
- **Exclusividade para Snow Family**:
    
    - Suporte dedicado apenas para dispositivos Snowcone, Snowball Edge e Snowmobile.
    - Facilita o uso de dispositivos em implantações edge e ambientes remotos.
- **Volume Configuration**:
    
    - Configuração de volumes de armazenamento, incluindo modos de operação específicos como armazenamento bloqueado ou objetos S3.

---

### Informações Extras

- O OpsHub **não gera custos adicionais**, sendo gratuito para uso, mas é necessário ter dispositivos Snow Family.
- Ele suporta **aplicativos edge**, permitindo que dispositivos executem funções **AWS Lambda**, serviços de contêiner ou aplicativos customizados localmente.
- OpsHub não substitui o AWS Management Console ou a CLI para gerenciar outros serviços AWS, sendo exclusivo para dispositivos Snow Family.

---

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **OpsHub** abrange o gerenciamento de:

- **AWS Snowcone**: Para transferências de dados pequenas ou uso edge portátil.
- **AWS Snowball Edge**: Para transferências de médio a grande porte e computação edge.
- **AWS Snowmobile**: Para transferências em escala de exabytes.

---

### Custos

- **Modelo de Custos**:
    - OpsHub é gratuito.
    - Custos são aplicáveis apenas ao uso de dispositivos Snow Family e às transferências de dados associadas.

---

### Casos de Uso Comuns no Exame

- Identificar que o OpsHub é **exclusivo para gerenciar dispositivos Snow Family**.
- Saber que ele **habilita criptografia por padrão** usando AWS KMS e suporta transferência de dados para o Amazon S3.
- Reconhecer que o OpsHub permite **operação offline**, sendo essencial para ambientes sem conectividade com a AWS.
- Entender que ele é usado para configuração de volumes e inicialização de dispositivos Snow Family de forma gráfica.