[[Tecnologia e serviços da nuvem]]
AWS Cloud Development Kit (CDK) é uma framework de código aberto que permite aos desenvolvedores definir e provisionar infraestrutura da AWS usando linguagens de programação como TypeScript, Python, Java, C# e Go. Ele abstrai a complexidade da configuração de recursos AWS e facilita o uso de boas práticas no gerenciamento de infraestrutura como código (IaC).
- **Definição de Infraestrutura em Código**: Permite a definição de recursos da AWS como instâncias EC2, VPCs, RDS, Lambda, etc., diretamente em código utilizando linguagens de alto nível.
- **Abstração de Recursos**: Fornece abstrações de nível mais alto (chamadas _constructs_) que encapsulam melhores práticas para configurar e provisionar recursos.
- **Integração com AWS CloudFormation**: O CDK gera automaticamente templates do AWS CloudFormation a partir do código, facilitando o provisionamento de recursos na AWS.
- **Suporte a Múltiplas Linguagens**: Oferece suporte para várias linguagens populares, como TypeScript, Python, Java, C# e Go, para permitir que os desenvolvedores usem as linguagens com as quais estão mais familiarizados.
- **Bibliotecas de Construção Reutilizáveis**: Inclui construções reutilizáveis que podem ser compartilhadas entre equipes, ajudando a padronizar e simplificar o desenvolvimento de infraestruturas na AWS.
- **Deploy de Infraestrutura com Facilidades**: Suporta o comando de _deploy_ direto de uma CLI para provisionar e gerenciar recursos sem a necessidade de escrever templates complexos em YAML ou JSON.
- **Facilidade de Testes**: O CDK facilita a criação de testes automatizados para infraestrutura, permitindo que os desenvolvedores testem se os recursos estão sendo configurados corretamente.
- **Infraestrutura como Código (IaC)**: Integra práticas de IaC que facilitam a replicação e versionamento de ambientes em diferentes estágios de desenvolvimento.
- **Compatibilidade com CI/CD**: Funciona bem com AWS CodePipeline, CodeBuild e outras ferramentas de integração contínua para automação de deploys e updates de infraestrutura.
**Modelo de Preços**:

- **Gratuito**:
    - O AWS CDK em si é gratuito, mas os recursos provisionados através dele são cobrados conforme o uso de serviços AWS (EC2, S3, Lambda, etc.).

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS CDK como uma solução para definir e provisionar infraestrutura usando código.
- Reconhecer como o CDK automatiza e simplifica o gerenciamento de recursos AWS com a abstração de melhores práticas.
- Compreender como o CDK facilita a integração com ferramentas de CI/CD para automação de infraestrutura.