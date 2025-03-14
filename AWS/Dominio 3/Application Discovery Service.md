[[Tecnologia e serviços da nuvem]]
O **AWS Application Discovery Service (ADS)** é uma ferramenta que auxilia na **descoberta e análise de inventário** em ambientes locais (on-premises) para facilitar **migrações para a AWS**. Ele coleta dados detalhados sobre os servidores, como **configuração de hardware**, **dependências de aplicativos** e **estatísticas de utilização**, ajudando no planejamento de migrações.

### Características Técnicas

- **Coleta de Dados**:
    
    - Usa agentes (Discovery Agents) instalados em servidores locais para coletar informações detalhadas, como:
        - **CPU, memória e disco**.
        - **Configurações de rede** e **interdependências** entre servidores.
    - Também suporta coleta de dados sem agentes (Agentless Discovery) ao se integrar com ferramentas de virtualização como VMware vCenter.
- **Armazenamento de Dados**:
    
    - As informações coletadas são armazenadas em um banco de dados **Application Discovery Service Repository**, acessível por meio da AWS Management Console ou APIs.
- **Exportação de Dados**:
    
    - Relatórios podem ser exportados em formatos como **CSV** para integração com ferramentas de planejamento de migração, como **AWS Migration Hub** e soluções de terceiros.
- **Mapeamento de Dependências**:
    
    - Identifica dependências entre servidores e aplicativos, fornecendo visualizações úteis para planejar migrações sem interrupções.
- **Integração com AWS Migration Hub**:
    
    - ADS pode enviar dados diretamente para o **AWS Migration Hub**, centralizando o gerenciamento do processo de migração.

---

### Informações Extras

- A coleta de dados pode levar várias semanas para criar uma imagem precisa do ambiente local.
- **Segurança dos Dados**: Os dados coletados são criptografados antes de serem enviados para a AWS.
- Apenas ambientes suportados (por exemplo, VMware, servidores físicos compatíveis) podem ser analisados com a descoberta sem agente.

---

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **Application Discovery Service** está diretamente integrado ao:

- **AWS Migration Hub**: Para centralizar os dados coletados e gerenciar o progresso da migração.
- **AWS Server Migration Service (SMS)**: Para simplificar a migração de servidores com base nas descobertas.

---

### Custos

- **Modelo de Custos**:
    - ADS **não possui custos adicionais** para descoberta com agentes ou sem agentes.
    - Custos associados podem incluir serviços auxiliares, como armazenamento ou ferramentas de terceiros para análise de relatórios exportados.

---

### Casos de Uso Comuns no Exame

- Reconhecer que o ADS é usado para **descobrir e mapear dependências** de servidores on-premises antes da migração.
- Identificar o papel do ADS na integração com o **AWS Migration Hub**.
- Diferenciar entre descobertas com agente e sem agente.
- Saber que ele coleta dados detalhados de hardware e software, incluindo métricas de utilização.
- Associar o ADS ao planejamento eficiente e sem interrupções em migrações complexas.