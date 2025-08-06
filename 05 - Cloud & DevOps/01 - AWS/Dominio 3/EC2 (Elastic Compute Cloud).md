[[Tecnologia e serviços da nuvem]]
Serviço de computação escalável que permite criar e gerenciar instâncias de servidores virtuais na nuvem para hospedar aplicativos e executar cargas de trabalho diversas.

- **Tipos de Instância**:
    
    - **General Purpose**: Para cargas de trabalho balanceadas (ex.: t4g, m6i).
    - **Compute Optimized**: Para processamento intensivo (ex.: c7g, c6i).
    - **Memory Optimized**: Para aplicativos com alta demanda de memória (ex.: r6g, x2idn).
    - **Storage Optimized**: Para aplicativos que exigem acesso rápido a grandes volumes de dados (ex.: i4i, d2).
    - **Accelerated Computing**: Para workloads que usam GPUs ou FPGAs, como machine learning e gráficos (ex.: p4d, g5).
- **Elasticidade e Escalabilidade**:
    
    - Auto Scaling para ajustar automaticamente os recursos de acordo com a demanda.
    - Elastic Load Balancing (ELB) para distribuir tráfego entre várias instâncias.
- **Segurança**:
    
    - Controle de acesso via AWS IAM.
    - Redes Virtuais Seguras (VPC) para isolar instâncias.
    - Suporte para chaves SSH e firewalls configuráveis via Security Groups.
- **Opções de Armazenamento**:
    
    - Amazon EBS (Elastic Block Store) para armazenamento persistente.
    - Armazenamento em instâncias (Instance Store) para dados temporários.
- **Lançamento de scripts durante inicialização**: User Data, shell scripts ou cloud-init directives.
- **EC2 Image Builder**: Simplifica o processo de testar, construir e implementação de uma VM e imagens de containers para uso na AWS ou On-Premises.                       
**Modelos de Preços**:  
- **Pague por segundo tem um custo minimo de 1 minuto para instancias Linux e Windows.**
- **Para outras instancias sera cobrado por hora.**
Amazon EC2 oferece flexibilidade de custos com diferentes opções de cobrança para atender a workloads variados:

1. **On-Demand (Sob Demanda)**
    
    - **Descrição**: Pague por hora ou segundo de uso, sem necessidade de compromisso a longo prazo.
    - **Ideal para**: Workloads imprevisíveis ou testes e desenvolvimento.
    - **Custo**: Mais alto comparado a outras opções.
2. **Reserved Instances (Instâncias Reservadas)**
    
    - **Descrição**: Compromisso de 1 ou 3 anos para obter descontos significativos (até 75%) comparado a On-Demand.
    - **Tipos**:
        - **Standard Reserved Instances**: Maior desconto, mas sem flexibilidade de trocar tipo ou família de instância.
        - **Convertible Reserved Instances**: Permitem trocar o tipo ou a família de instância durante o período do compromisso, com desconto menor que as Standard.
    - **Ideal para**: Workloads estáveis e previsíveis, como servidores de banco de dados ou aplicativos de produção.
3. **Savings Plans**
    
    - **Descrição**: Compromisso de uso (em horas ou dólares) por 1 ou 3 anos com flexibilidade de usar qualquer tipo de instância EC2 ou até outros serviços, como AWS Fargate.
    - **Ideal para**: Workloads variados, onde a flexibilidade entre serviços é importante.
    - **Comparação**: Mais flexível que Reserved Instances, mas com desconto menor.
    - **Compute Savings Plans**: Mais flexibilidade, reduz custos 66%, se aplicam para EC2s **não importante a família da instancia, tamanho, AZ, Region, OS, também se aplica a Fargate e Lambda.**
    - **EC2 Instance Saving Plans**: Prove o menor dos preços 72%, em **troca de um commitment para o uso de famílias de instancias individuais numa região.**
1. **Spot Instances**
    
    - **Descrição**: Permite usar capacidade ociosa da AWS com descontos de até 90%, mas as instâncias podem ser encerradas a qualquer momento se a capacidade for necessária para outros clientes.
    - **Ideal para**: Processamento de big data, simulações, renderização e cargas tolerantes a interrupções.
5. **Dedicated Hosts**
    
    - **Descrição**: Servidores físicos dedicados, oferecendo controle total sobre a alocação de instâncias para atender requisitos de licenciamento ou conformidade.
    - **Ideal para**: Workloads com requisitos rigorosos de licenciamento, como SQL Server, ou ambientes altamente regulamentados.
6. **Dedicated Instances**
    
    - **Descrição**: Instâncias dedicadas a um único cliente, sem compartilhar hardware com outras contas.
    - **Ideal para**: Ambientes que requerem isolamento físico por razões de segurança ou conformidade.
7. **Spot Fleet**
    
    - **Descrição**: Gerencia um conjunto de Spot Instances e, opcionalmente, instâncias On-Demand para atender a uma capacidade-alvo.
    - **Ideal para**: Escalabilidade com controle de custos em cargas de trabalho elásticas e tolerantes a falhas.
**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon EC2 como uma solução para computação escalável e personalizável.
- Reconhecer os diferentes tipos de instância e opções de compra para otimizar custos.
- Compreender a importância de recursos como Auto Scaling e Elastic Load Balancing na gestão eficiente de cargas de trabalho.