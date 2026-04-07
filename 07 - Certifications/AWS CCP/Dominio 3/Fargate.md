[[Tecnologia e serviços da nuvem]]
E um serviço de computação sem servidor para contêineres que permite executar aplicações sem ter que gerenciar a infraestrutura. Funciona com [[ECS (Elastic Container Service)]] e com [[EKS (Elastic Kubernetes Service)]]
- **Gerenciamento Automático de Infraestrutura**: Fargate provisiona e escala automaticamente os recursos necessários para executar contêineres.
- **Modelo Serverless**: Não exige a configuração de instâncias EC2 ou clusters subjacentes; o foco está apenas na execução dos contêineres.
- **Escalabilidade Automática**: Ajusta automaticamente os recursos com base nas necessidades de carga de trabalho, sem intervenção manual.
- **Compatibilidade com ECS e EKS**: Oferece suporte para tarefas orquestradas com Amazon ECS ou pods gerenciados em clusters Kubernetes via EKS.
- **Isolamento de Contêineres**: Cada tarefa ou pod tem seus próprios recursos isolados, garantindo segurança e desempenho previsíveis.
- **Custo Baseado em Uso**: Paga apenas pelos recursos consumidos durante a execução, como CPU e memória.

**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada nos recursos consumidos (CPU e memória) pelas tarefas ou pods enquanto estão em execução.
    - Custo adicional para armazenamento e transferência de dados, dependendo dos serviços AWS integrados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Fargate como uma solução serverless para executar contêineres sem gerenciar servidores.
- Reconhecer como o Fargate se integra ao ECS e EKS para orquestração de contêineres.
- Compreender os benefícios de escalabilidade e otimização de custos em aplicações baseadas em contêineres.