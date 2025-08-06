[[Tecnologia e serviços da nuvem]]
O **AWS Outposts** é uma solução de infraestrutura híbrida que leva os serviços da **AWS para data centers locais** ou locais de cliente. Ele é projetado para cenários em que baixa latência, conformidade regulatória ou requisitos de soberania de dados exigem a execução de cargas de trabalho fora das regiões da AWS, mas com a mesma experiência de nuvem.
### Características Técnicas

- **Infraestrutura Gerenciada**:
    
    - Oferece racks totalmente gerenciados pela AWS, com hardware e software configurados para rodar serviços AWS localmente.
    - Permite executar serviços como **Amazon EC2**, **EBS**, **RDS**, **EKS**, e **S3**.
- **Baixa Latência Local**:
    
    - Projetado para aplicações que exigem processamento local e comunicação em tempo real, como sistemas industriais ou aplicações médicas.
- **Gerenciamento Unificado**:
    
    - Recursos do Outposts são gerenciados no **AWS Management Console** da mesma forma que outros serviços em regiões da AWS.
    - Integração nativa com **IAM**, **CloudFormation** e **CloudWatch**.
- **Conectividade com a Nuvem**:
    
    - Conexão direta com a região da AWS mais próxima para sincronizar dados e gerenciar cargas de trabalho híbridas.
    - Requer um link confiável para operação contínua em modos híbridos.
- **Serviços Compatíveis**:
    
    - **Compute**: Instâncias EC2, ECS, EKS.
    - **Storage**: EBS e Amazon S3 em Outposts (limitado a certas versões do hardware).
    - **Banco de Dados**: Suporte para **Amazon RDS** e **Amazon ElastiCache**.

---

### Informações Extras

- **Personalização**: Disponível em configurações padrão ou personalizadas para se adaptar às necessidades do cliente.
- **Regiões Limitadas**: Outposts está disponível para compra e entrega em regiões específicas da AWS.
- **Responsabilidade Compartilhada**: O cliente é responsável por fornecer energia, conectividade de rede e acesso físico seguro ao local do rack.
- **Ativo Físico**: Ao contrário de serviços puramente virtuais, o Outposts é entregue como um rack físico no local.

---

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **AWS Outposts** suporta e se conecta a diversos serviços AWS:

- **EC2 e EBS**: Para computação e armazenamento.
- **EKS e ECS**: Para execução de contêineres.
- **Amazon S3 em Outposts**: Armazenamento local com APIs S3.
- **RDS**: Para bancos de dados gerenciados localmente.

---

### Custos

- **Modelo de Custos**:
    - Baseado em **instâncias reservadas** para serviços como EC2 e armazenamento EBS.
    - Inclui custos de hardware (compra ou aluguel) e suporte gerenciado.
    - Custos adicionais podem se aplicar ao uso de conectividade com regiões AWS.

---

### Casos de Uso Comuns no Exame

- Reconhecer o **AWS Outposts** como uma solução híbrida para cargas de trabalho locais.
- Entender que ele permite executar **serviços AWS no local** com gerenciamento centralizado na nuvem.
- Identificar que o Outposts é útil para conformidade regulatória, baixa latência ou soberania de dados.
- Saber que ele suporta **EBS, S3, EC2, RDS, ECS, EKS**, mas requer conectividade confiável com uma região AWS para muitas operações.