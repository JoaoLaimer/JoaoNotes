[[Segurança e conformidade]]
O **AWS CloudHSM** é um serviço que oferece **Hardware Security Modules (HSMs)** dedicados para gerenciar chaves criptográficas com alta segurança. Ele permite atender requisitos de conformidade rigorosos e operar chaves criptográficas em dispositivos físicos dentro da AWS.

---

### Características Técnicas

- **Hardware Dedicado**:
    
    - Cada HSM é uma instância dedicada executada em hardware validado pelo **FIPS 140-2 Level 3**.
    - Oferece isolamento completo entre seus HSMs e outros clientes AWS.
- **Controle Total de Chaves**:
    
    - Você controla e gerencia diretamente as chaves no HSM; a AWS não tem acesso a elas.
    - Suporte a APIs padrão de mercado, como **PKCS#11**, **Java JCE** e **Microsoft CNG**.
- **Alta Disponibilidade e Escalabilidade**:
    
    - Suporte para implantação de clusters de HSMs distribuídos em múltiplas zonas de disponibilidade (AZs) para alta disponibilidade.
    - Os clusters podem escalar horizontalmente para atender maiores demandas.
- **Integração com Serviços AWS**:
    
    - Pode ser usado com **Amazon RDS** para criptografia de dados no banco de dados.
    - Integração com o **Elastic Load Balancer (ELB)** para Terminação SSL/TLS.
    - Suporte ao uso em aplicações customizadas hospedadas no **EC2**.
- **Criptografia de Dados**:
    
    - Geração, armazenamento e uso de chaves para criptografia simétrica e assimétrica.
    - Pode ser usado para assinaturas digitais e geração de certificados.

---

### Informações Extras

- Oferece maior controle sobre criptografia do que o **AWS KMS**, já que o CloudHSM permite o gerenciamento direto das chaves no hardware dedicado.
- **Compatibilidade com padrões de segurança internacionais**, o que é essencial para atender regulamentações específicas como PCI DSS, GDPR e HIPAA.
- Não oferece integração direta com serviços AWS como KMS; é voltado para casos em que controle e conformidade são mais críticos.

---

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **CloudHSM** é usado em contextos altamente especializados, mas integra-se com:

- **RDS**: Para gerenciar criptografia em bancos de dados com maior controle de chave.
- **Elastic Load Balancer (ELB)**: Para Terminação SSL com chaves gerenciadas no HSM.
- **Amazon EC2**: Para uso em aplicativos que requerem acesso direto ao HSM.

---

### Custos

- **Modelo de Custos**:
    - Cobrança por hora para cada HSM provisionado.
    - Custos adicionais associados à transferência de dados entre regiões, se aplicável.
    - Não há custos baseados em transações ou chamadas de API.

---

### Casos de Uso Comuns no Exame

- Reconhecer a diferença entre **AWS CloudHSM** e **AWS KMS** em termos de controle e conformidade.
- Identificar cenários em que HSM dedicado é necessário para atender regulamentações específicas.
- Entender como o CloudHSM é usado para gerenciar criptografia em serviços como **RDS** e **ELB**.
- Selecionar casos de uso para geração de chaves assimétricas e assinaturas digitais em hardware dedicado.
- Saber que o CloudHSM oferece suporte para clusters em múltiplas AZs para alta disponibilidade.