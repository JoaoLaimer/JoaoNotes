[[Cobrança, Preços e Suporte]] 
Serviço que utiliza machine learning para analisar o uso de recursos computacionais na AWS e fornecer recomendações personalizadas para melhorar desempenho, reduzir custos e aumentar eficiência.

- **Recomendações de Instâncias**: Analisa instâncias do Amazon EC2, volumes do Amazon EBS, grupos de Auto Scaling e instâncias do AWS Lambda para sugerir ajustes.
- **Redução de Custos**: Identifica instâncias subutilizadas ou superdimensionadas e recomenda tamanhos ou tipos de instâncias mais adequados.
- **Melhoria de Desempenho**: Sugere alterações que podem melhorar o desempenho das aplicações sem custos adicionais.
- **Modelos de ML**: Utiliza machine learning para identificar padrões de uso e prever necessidades futuras de recursos.
- **Relatórios Detalhados**: Fornece métricas e insights para ajudar a justificar decisões de otimização.
- **Suporte a EC2 Spot e Savings Plans**: Inclui recomendações para otimizar custos com instâncias reservadas e planos de economia.
- **Compatibilidade com CloudWatch**: Integra-se ao Amazon CloudWatch para coletar métricas de desempenho e uso de recursos.
**Modelo de Preços**:

- **Gratuito**:
    - O AWS Compute Optimizer não possui custos adicionais.
    - As recomendações são baseadas em métricas coletadas por serviços como CloudWatch, que podem gerar custos conforme o volume de dados monitorados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Reconhecer o AWS Compute Optimizer como uma solução para ajustar recursos computacionais, reduzindo custos e melhorando desempenho.
- Identificar a relação entre métricas de uso (via CloudWatch) e as recomendações geradas.
- Entender como o serviço ajuda na escolha de instâncias EC2, grupos de Auto Scaling e configurações de Lambda para maximizar eficiência.