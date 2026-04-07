[[Tecnologia e serviços da nuvem]]
O **AWS PrivateLink** é um serviço que permite acessar serviços da AWS e aplicativos hospedados de forma **privada** dentro de uma **VPC**. Ele utiliza interfaces **Elastic Network Interfaces (ENIs)** com endereços IP privados para estabelecer conexões seguras, eliminando a necessidade de expor os serviços à internet pública.
### Características Técnicas

- **Conexões Privadas**:
    
    - Estabelece acesso privado a serviços da AWS, como **S3**, **Kinesis**, **EC2**, entre outros, diretamente de uma **VPC**.
    - Usa **Endpoints de Interface (Interface Endpoints)** para conectar serviços ao **AWS PrivateLink**.
- **Serviços Suportados**:
    
    - Compatível com diversos serviços da AWS (ex.: S3, Kinesis, Secrets Manager).
    - Suporte para aplicativos personalizados hospedados em **Elastic Load Balancer (NLB)**.
- **Segurança Avançada**:
    
    - **Tráfego não sai da rede AWS** e permanece dentro do backbone seguro da AWS.
    - Integração com **IAM Policies** para controlar o acesso a endpoints privados.
- **Multi-Account e Multi-Region**:
    
    - Permite que consumidores em contas ou regiões diferentes acessem serviços por meio de **Interface Endpoints** compartilhados.
    - Ideal para arquiteturas SaaS, conectando clientes de forma privada.
- **Elastic Network Interfaces (ENIs)**:
    
    - Cada endpoint privado é representado por uma ENI na VPC, configurada automaticamente com endereços IP privados.

---

### Informações Extras

- PrivateLink é projetado para funcionar exclusivamente dentro da rede da AWS. Não permite conexões privadas para serviços fora da AWS.
- **Interface Endpoints** são cobrados com base na quantidade de dados transferidos e no tempo ativo.
- PrivateLink pode ser combinado com outras soluções como **VPC Peering** ou **Transit Gateway**, mas com objetivos distintos.

---

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **AWS PrivateLink** conecta serviços e recursos por meio de **Interface Endpoints**:

- **Interface Endpoints**: Conecta serviços da AWS e SaaS a VPCs.
- **NLB**: Publicação de aplicativos privados hospedados em Network Load Balancers para consumo via PrivateLink.
- **CloudWatch Logs**: Transmissão privada de logs para o CloudWatch via PrivateLink.

---

### Custos

- **Modelo de Custos**:
    - Cobrança baseada no número de endpoints criados (preço por hora).
    - Custos adicionais pela quantidade de dados transferidos por meio do endpoint.
    - Exemplo de uso econômico: Evitar custos de tráfego de internet pública usando endpoints privados.

---

### Casos de Uso Comuns no Exame

- Identificar o **AWS PrivateLink** como a solução para conectar serviços AWS e aplicativos sem expor tráfego à internet.
- Saber que ele é usado para **Interface Endpoints** para serviços como **S3** ou aplicativos hospedados em **NLBs**.
- Diferenciar PrivateLink de outras soluções como **VPC Peering** (que conecta redes inteiras) ou **Transit Gateway**.
- Reconhecer seu papel em arquiteturas SaaS para oferecer conectividade privada entre provedores e consumidores.