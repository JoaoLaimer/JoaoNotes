[[Tecnologia e serviços da nuvem]]
Serviço que ajusta automaticamente a capacidade de recursos computacionais, como instâncias **EC2**, de acordo com as demandas da aplicação, garantindo desempenho ideal com controle de custos.
- **Ajuste Automático**: Escala automaticamente os recursos para cima ou para baixo com base em políticas definidas, como uso de CPU, tráfego ou horários programados.
- **Compatibilidade com Múltiplos Recursos**: Funciona com Amazon [[EC2 (Elastic Compute Cloud)]], grupos de Auto Scaling, Amazon [[ECS (Elastic Container Service)]], DynamoDB, Aurora e Spot Fleets.
- **Alta Disponibilidade**: Garante redundância ao **adicionar ou remover** ou seja, ele escala **HORIZONTALMENTE**  recursos conforme necessário, minimizando falhas de serviço.
- **Políticas de Escalabilidade**:
    - **Baseada em Métricas**: Aumenta ou reduz a capacidade com base em métricas específicas (ex.: CPU > 70%).
    - **Programada**: Escala recursos em horários ou datas específicas (ex.: aumentar servidores durante horários de pico).
    - **Baseada em Previsão**: Utiliza machine learning para prever picos de tráfego e ajustar a capacidade antecipadamente (Predictive Scaling).
    - **Saude da instancia** 
- **Fácil Integração**: Configura e gerencia escalabilidade através do console da AWS, CLI ou API.
- **Monitoramento Contínuo**: Integra-se ao Amazon CloudWatch para monitorar métricas e gerar alarmes que acionam escalabilidade.
- **Remove instancias com saude baixa.**
**Modelo de Preços**:

- **Gratuito para Configuração**: Não há custo adicional para usar o AWS Auto Scaling.
- **Custos Relacionados aos Recursos**: A cobrança é baseada nos recursos subjacentes utilizados, como instâncias EC2, DynamoDB ou Aurora, conforme o dimensionamento automático.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Reconhecer o AWS Auto Scaling como uma solução para ajustar recursos dinamicamente com base na demanda.
- Identificar como o serviço contribui para redução de custos e melhoria do desempenho.
- Compreender as diferentes políticas de escalabilidade disponíveis (baseada em métricas, programada e preditiva).