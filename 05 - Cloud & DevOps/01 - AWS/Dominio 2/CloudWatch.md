[[Segurança e conformidade]] e [[Tecnologia e serviços da nuvem]]
Serviço de monitoramento e observabilidade que coleta, visualiza e analisa métricas, logs e eventos de recursos AWS e aplicações em execução na nuvem ou on-premises.
- **Coleta de Métricas**: Monitora métricas padrão de serviços AWS, como uso de CPU, memória e tráfego de rede, e permite a criação de métricas personalizadas.
- **Logs Centralizados**: Armazena e analisa logs de aplicativos e sistemas em tempo real para identificar problemas ou otimizar o desempenho.
- **Alarmes Personalizados**: Configura alarmes para notificar ou acionar ações automáticas (ex.: escalonamento) com base em limites definidos.
- **Painéis de Controle (Dashboards)**: Oferece uma visão unificada de métricas e logs, com gráficos personalizáveis para visualização de dados.
- **Eventos e Ações Automatizadas**: Integra-se com Amazon SNS, Lambda e Step Functions para responder automaticamente a eventos, como falhas ou alterações em recursos.
- **Monitoramento de Aplicativos**: Com Amazon CloudWatch Application Insights, identifica problemas em aplicativos com base em logs, métricas e eventos.
- **Insights Avançados**: Serviços como CloudWatch Logs Insights permitem consultas e análises avançadas de grandes volumes de dados de logs.
- **Suporte Multi-Conta e Multi-Região**: Consolida métricas e logs de várias contas e Regiões AWS para facilitar o gerenciamento.
**Modelo de Preços**:

- **Gratuito**:
    - Métricas padrão para muitos serviços AWS estão inclusas.
    - Alarme gratuito para métricas padrão.
- **Pague pelo uso**:
    - Custos adicionais para logs armazenados, consultas de logs e métricas personalizadas.
    - Cobrança baseada no número de alarmes criados e volume de eventos processados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon CloudWatch como uma solução para monitorar métricas e logs de serviços AWS.
- Reconhecer a importância de alarmes e dashboards para garantir a alta disponibilidade de sistemas.
- Compreender como o CloudWatch pode acionar ações automáticas com outros serviços, como Lambda ou SNS.