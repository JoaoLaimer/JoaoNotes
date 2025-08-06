[[Segurança e conformidade]]
Serviço de detecção de ameaças que monitora continuamente atividades maliciosas ou comportamentos suspeitos em sua conta AWS, ajudando a proteger aplicativos e dados.
- **Análise Inteligente de Dados**: Usa machine learning, análise comportamental e inteligência de ameaças de terceiros para identificar possíveis ataques ou vulnerabilidades.
- **Fontes de Dados Integradas**: Analisa logs de [[VPC Flow]], [[CloudTrail]] e DNS para detectar atividades incomuns, como tentativas de exfiltração de dados ou acesso não autorizado.
- **Detecção de Ameaças Específicas**: Identifica atividades como mineração de criptomoedas, tráfego vindo de locais suspeitos e alterações em permissões de recursos.
- **Monitoramento Contínuo**: Operação sempre ativa, sem a necessidade de configurar ou gerenciar infraestrutura adicional.
- **Alertas e Insights**: Gera achados (findings) detalhados que podem ser visualizados no console, integrados ao [[CloudWatch]] ou encaminhados para sistemas de resposta automatizada.
- **Escalabilidade Automática**: Funciona com todas as contas e Regiões dentro de uma organização AWS.
- **Integração com Outros Serviços AWS**: Funciona bem com AWS Security Hub, AWS Lambda e Amazon SNS para automação de respostas e notificações.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança com base no volume de dados analisados (logs de VPC Flow, CloudTrail e DNS).
    - Custos adicionais podem surgir ao integrar com outros serviços AWS, como SNS ou Lambda.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon GuardDuty como uma ferramenta para detecção automática de ameaças em contas AWS.
- Reconhecer como o GuardDuty usa fontes de dados e inteligência de ameaças para detectar comportamentos suspeitos.
- Compreender como o GuardDuty se integra ao Security Hub e outros serviços para resposta a incidentes.