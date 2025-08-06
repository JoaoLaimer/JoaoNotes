[[Tecnologia e serviços da nuvem]]
AWS CodePipeline é um serviço de entrega contínua que automatiza os fluxos de trabalho de lançamento de software. Ele integra várias etapas, como compilação, teste e implantação, em pipelines configuráveis, permitindo entregas rápidas e confiáveis.
- **Automação de Pipeline**: Define pipelines para automação de todas as etapas do ciclo de vida do software, desde o commit até a produção.
- **Integração com Serviços AWS**: Suporte nativo para CodeCommit, CodeBuild, CodeDeploy, Lambda, Elastic Beanstalk, ECS e S3.
- **Suporte a Ferramentas Externas**: Compatibilidade com GitHub, Bitbucket, Jenkins e outras ferramentas de CI/CD populares.
- **Gatilhos Automáticos**: Inicia pipelines automaticamente com base em alterações no repositório de código ou eventos configurados.
- **Aprovações Manuais**: Adiciona pontos de aprovação em pipelines para garantir controle antes de prosseguir para etapas críticas.
- **Execução Paralela e Serial**: Configuração flexível para etapas que podem ser executadas em sequência ou simultaneamente.
- **Integração com Notificações**: Trabalha com Amazon SNS para enviar notificações sobre o status do pipeline.
- **Segurança**: Controle de acesso granular com AWS IAM, garantindo permissões específicas para cada etapa e recurso do pipeline.
- **Monitoramento e Logs**: Integração com CloudWatch para rastrear métricas e gerar logs detalhados de execução como mudanças no CodeCommit.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no número de pipelines ativos por mês.
    - As etapas de pipeline que utilizam outros serviços, como CodeBuild ou CodeDeploy, geram cobranças adicionais.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS CodePipeline como uma solução para automação de entrega contínua.
- Reconhecer sua integração com serviços AWS e ferramentas externas para pipelines de CI/CD.
- Compreender como ele melhora a eficiência do ciclo de vida de desenvolvimento de software.