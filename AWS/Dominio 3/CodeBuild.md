[[Tecnologia e serviços da nuvem]]
Serviço totalmente gerenciado de integração contínua (CI) que compila o código-fonte, executa testes e gera pacotes prontos para implantação de forma automática e escalável.
- **Compilação Automática**: CodeBuild pode compilar o código de qualquer repositório, como GitHub, AWS CodeCommit ou Bitbucket, sem a necessidade de provisionar servidores ou gerenciar infraestrutura.
- **Execução de Testes**: Suporta execução de testes unitários e de integração durante o processo de compilação para garantir a qualidade do código antes da implantação.
- **Escalabilidade**: Escala automaticamente para suportar múltiplas compilações simultâneas, com a possibilidade de configurar instâncias de compilação de acordo com as necessidades do projeto.
- **Ambientes de Build Personalizados**: Suporta ambientes personalizados e pré-configurados com suporte a várias linguagens de programação, como Java, Python, Node.js, Ruby, Go, entre outros.
- **Integração com Outros Serviços AWS**: Integra-se perfeitamente com serviços como AWS CodePipeline para criar pipelines de CI/CD, AWS Lambda para automação, Amazon S3 para armazenamento de artefatos e Amazon CloudWatch para monitoramento de builds.
- **Armazenamento de Artefatos**: Armazena pacotes de saída (artefatos) diretamente no Amazon S3, permitindo acesso fácil para a próxima etapa do pipeline ou implantação.
- **Suporte a Docker**: Suporte nativo para Docker, permitindo que você crie containers personalizados como ambientes de build.
- **Segurança**: Garante a segurança dos builds com controle de acesso por AWS IAM e a capacidade de criptografar dados em trânsito e em repouso.
- **Preços Baseados no Uso**: O custo é baseado no tempo de execução dos builds, com cobrança por minuto para o uso de instâncias de build.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no tempo de execução das compilações (por minuto).
    - Custo adicional para armazenar artefatos no S3 e para o uso de instâncias de compilação personalizadas ou específicas.
    - Não há custo para as compilações em instâncias de build padrão, mas o uso de instâncias maiores ou com maior desempenho pode gerar custos adicionais.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- **Identificar o AWS CodeBuild** como parte da estratégia de CI/CD, automatizando a compilação e os testes do código.
- **Entender a integração do CodeBuild com outros serviços AWS**, como CodePipeline, S3 e Lambda, para criar um fluxo de trabalho de automação completo.
- **Compreender o modelo de preços**, que cobra pelo tempo de execução de cada build, permitindo uma escalabilidade automática e otimização de custos.