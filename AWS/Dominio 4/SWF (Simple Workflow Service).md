[[Tecnologia e serviços da nuvem]]
AWS Simple Workflow Service (SWF) é um serviço que ajuda a coordenar tarefas em aplicativos distribuídos. Ele gerencia o fluxo de trabalho de tarefas, garantindo que sejam executadas na ordem correta, com rastreamento detalhado e possibilidade de intervenções humanas.
#### **Características Técnicas**

**1. Coordenação de Fluxos de Trabalho**
- Gerencia a execução de tarefas sequenciais, paralelas ou dependentes.
- Suporte a workflows complexos com controle detalhado sobre o estado de cada etapa.
**2. Atividades e Decisões**
- **Atividades**: Representam tarefas individuais executadas por workers (pessoas ou sistemas).
- **Decisões**: Determinam os próximos passos no fluxo de trabalho, com base no resultado das atividades anteriores.
**3. Suporte a Longa Duração** 
- Permite executar workflows com duração de minutos a meses, rastreando o progresso e estados.
**4. Intervenção Humana**
- Suporte a etapas que requerem aprovação ou entrada manual antes de continuar o fluxo.
**5. Controle Total**
- Permite lógica personalizada para lidar com falhas, tentativas de reprocessamento e tempo limite de tarefas.
**6. Integração com Outros Serviços AWS**
- Trabalha com EC2, Lambda, e S3 para processamento e armazenamento de dados.
- Registra eventos em **CloudWatch** para monitoramento e alertas.
**7. Rastreamento e Logs**
- Mantém um histórico detalhado de eventos para auditoria e depuração.
**8. API Flexível**
- Oferece APIs para configurar, iniciar e monitorar workflows programaticamente.
**Modelo de Preços**:
- **Pague pelo uso**:
    - Cobrança baseada no número de workflows iniciados, decisões realizadas e eventos registrados.
**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:
- Identificar o AWS SWF como uma solução para coordenação de tarefas e workflows complexos.
- Reconhecer sua capacidade de gerenciar fluxos de trabalho de longa duração e integração com tarefas humanas.
- Compreender como ele oferece controle detalhado sobre lógica de workflows, tentativas e falhas.