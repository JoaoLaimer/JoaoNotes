[[Cobrança, Preços e Suporte]]
**Cost Allocation Tags** são **marcadores** aplicados aos recursos AWS para identificar, rastrear e alocar custos. Eles ajudam a organizar faturas e análises de uso, permitindo segmentar custos por **projeto**, **departamento**, **ambiente** ou qualquer outra categoria.

### Características Técnicas

- **Tipos de Tags**:
    
    - **AWS-generated Tags**: Criadas automaticamente pela AWS, geralmente prefixadas com `aws:`.
    - **User-defined Tags**: Criadas pelo usuário para personalização e rastreamento específico.
- **Ativação no Billing and Cost Management**:
    
    - Tags precisam ser ativadas no **console de Cost Allocation Tags** para serem utilizadas nos relatórios de custos.
    - Uma vez ativadas, as tags aparecem no **AWS Cost Explorer**, **AWS Budgets** e relatórios detalhados de utilização.
- **Integração com Outros Serviços**:
    
    - **AWS Cost Explorer**: Visualiza custos por tags específicas.
    - **AWS Budgets**: Define orçamentos baseados em tags para monitorar e controlar gastos.
    - **AWS Organizations**: Tags podem ser usadas em contas vinculadas para análises centralizadas.

### Informações Extras

- **Tags não são retroativas**: Só influenciam dados de custos a partir do momento em que são ativadas.
- Máximo de **50 tags** definidas por recurso.
- As tags do tipo `aws:` são somente leitura, mas muito úteis para automação e análises padrão.
- Tags são case-sensitive.
- Utilizadas com **Resource Groups** para gerenciar recursos agrupados por tags específicas.

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

Cost Allocation Tags estão dentro de **Billing and Cost Management** e abrangem:

- **AWS Cost Explorer**: Para visualizar dados por tag.
- **AWS Budgets**: Permite definir orçamentos específicos para tags, como departamentos ou projetos.
- **AWS Organizations**: Consolida análises de tags em contas vinculadas.
- **AWS Resource Groups**: Gerenciamento eficiente de recursos baseados em tags.

### Custos

- **Modelo de Custos**:
    - Não há custos adicionais para criar ou ativar tags.
    - Custos podem ser gerados ao utilizar serviços que processam dados com tags (e.g., análises no Cost Explorer).

### Casos de Uso Comuns no Exame

- Identificar a funcionalidade das **AWS-generated Tags** e **User-defined Tags**.
- Analisar um cenário onde custos precisam ser atribuídos a projetos específicos.
- Configurar um **budget** utilizando tags para alertas personalizados.
- Reconhecer que as tags devem ser **ativadas** para refletir nos relatórios de custo.
- Gerenciar custos em contas de **AWS Organizations** usando tags compartilhadas.