[[Tecnologia e serviços da nuvem]]
Amazon Elastic Container Registry (ECR) é um serviço gerenciado para armazenar, gerenciar e implantar imagens de contêineres. Ele é altamente integrado com serviços da AWS, como [[ECS (Elastic Container Service)]], [[EKS (Elastic Kubernetes Service)]] e AWS Lambda, permitindo fluxos de trabalho contínuos para aplicações baseadas em contêineres.
- **Repositórios Privados e Públicos**: Suporte para armazenar imagens em repositórios privados e compartilhar imagens publicamente.
- **Integração com CI/CD**: Facilita fluxos de trabalho automatizados em pipelines de CI/CD usando AWS CodePipeline, CodeBuild e Jenkins.
- **Gerenciamento de Permissões**: Controle de acesso detalhado por AWS IAM para restringir quem pode acessar e modificar imagens.
- **Segurança Avançada**: Suporte para criptografia de imagens em repouso e integração com AWS KMS para maior controle.
- **Scanning de Vulnerabilidades**: Detecção de vulnerabilidades em imagens com base em bancos de dados de CVEs (Common Vulnerabilities and Exposures).
- **Performance Otimizada**: Downloads rápidos de imagens por meio de integração com Amazon Elastic Network Interface (ENI).
- **Suporte Multi-Região**: Facilita o armazenamento e acesso a imagens em diferentes regiões para otimizar a disponibilidade e performance.
- **Compatibilidade com Docker**: Totalmente integrado ao Docker CLI, permitindo que desenvolvedores empurrem e puxem imagens com comandos familiares.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no armazenamento de imagens e na transferência de dados entre Regiões ou fora da AWS.
    - Os primeiros 500 MB por mês de armazenamento em repositórios privados são gratuitos.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon ECR como uma solução para armazenar e gerenciar imagens de contêineres.
- Reconhecer sua integração com ECS, EKS e Lambda para implantação direta de contêineres.
- Compreender como ele suporta fluxos de trabalho seguros com scanning de vulnerabilidades e permissões IAM.