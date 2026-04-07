[[Tecnologia e serviços da nuvem]]
Serviço de orquestração que facilita a criação de workflows serverless para coordenar serviços da AWS e aplicativos personalizados, permitindo automação de processos com lógica complexa.

- **Orquestração de Tarefas**: Permite coordenar múltiplos serviços, como AWS Lambda, DynamoDB, S3 e ECS, em um fluxo de trabalho único e visual.
- **Definição Simples**: Usa a linguagem Amazon States Language (JSON) para definir estados, transições e lógica do workflow.
- **Fluxos de Trabalho Visual**: Oferece uma interface gráfica para criar, visualizar e monitorar workflows, facilitando o entendimento e a manutenção.
- **Reprocessamento e Retentativa Automática**: Detecta falhas em tarefas e executa retentativas automáticas com base em políticas configuráveis, reduzindo erros manuais.
- **Escalabilidade Automática**: Ajusta dinamicamente os recursos para suportar workflows de alta carga.
- **Workflows Longos**: Suporte a workflows que duram minutos, horas ou até meses, úteis em processos como aprovação de documentos ou execução de tarefas assíncronas.
- **Integração com Serviços AWS**: Conecta facilmente com mais de 200 serviços da AWS, incluindo Lambda, SQS, SNS, ECS, Glue e mais.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança baseada no número de transições de estado realizadas no workflow.
    - Preços diferenciados para dois tipos de workflows:
        - **Standard Workflows**: Ideal para processos de longa duração e alta flexibilidade.
        - **Express Workflows**: Otimizado para execuções rápidas e de alta taxa de eventos.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Step Functions como uma ferramenta para orquestrar serviços AWS e automatizar processos complexos.
- Reconhecer a diferença entre Standard e Express Workflows em termos de custo e aplicação.
- Compreender como o Step Functions facilita a integração e coordenação de tarefas assíncronas em ambientes distribuídos.