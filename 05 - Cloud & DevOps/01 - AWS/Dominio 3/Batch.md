[[Tecnologia e serviços da nuvem]]

Serviço gerenciado para executar grandes volumes de tarefas em lote, como processamento de dados, simulações ou processamento de arquivos, de forma escalável e eficiente.

- **Escalabilidade Automática**: Ajusta automaticamente os recursos (instâncias EC2) conforme a carga de trabalho, garantindo eficiência e economia de custos.
- **Suporte a Diversos Tipos de Trabalho**: Permite executar jobs de diferentes tipos, como contêineres Docker, jobs com dependências, e tarefas de longa duração ou tarefas paralelizadas.
- **Integração com Outras Ferramentas AWS**: Fácil integração com serviços como Amazon S3 (para armazenamento de dados), Amazon CloudWatch (para monitoramento) e AWS IAM (para controle de acesso).
- **Gerenciamento de Dependências**: Permite definir e gerenciar dependências entre jobs, facilitando a execução de workflows complexos.
- **Agendamento de Jobs**: Jobs podem ser agendados para execução em horários específicos, garantindo que tarefas sejam executadas quando recursos estiverem disponíveis.
- **Facilidade de Uso**: AWS Batch cuida da infraestrutura necessária para execução de jobs, permitindo que os desenvolvedores se concentrem nas tarefas de processamento de dados.
- **Customização de Ambientes de Execução**: Possibilidade de configurar e personalizar o ambiente de execução dos jobs, como escolher o tipo de instância EC2 ou usar clusters do Amazon ECS para gerenciar contêineres.
**Ideal para**:

- Processamento de grandes volumes de dados, como análise de big data, geração de relatórios ou execução de simulações científicas.
- Empresas que precisam de processamento em lote para trabalhos que não exigem interação em tempo real.
- Execução de tarefas paralelizadas, como renderização de vídeos, processamento de imagens ou treinamento de modelos de machine learning em grandes volumes de dados.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança com base na quantidade de recursos computacionais utilizados durante a execução dos jobs.
    - Preço depende do tipo de instância EC2 ou recursos de contêiner usados para a execução do trabalho.
    - O armazenamento de dados (ex.: no S3) e o uso de outros serviços AWS também podem ser cobrados conforme o uso.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Processamento de grandes conjuntos de dados para análises financeiras ou científicas.
- Execução de tarefas de big data que precisam ser distribuídas em múltiplas instâncias de computação.
- Automatização de tarefas em larga escala, como o processamento de imagens ou vídeos em produção de mídia.