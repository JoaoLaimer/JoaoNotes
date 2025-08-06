[[Segurança e conformidade]] e [[Tecnologia e serviços da nuvem]]
Serviço que unifica e automatiza o gerenciamento de recursos AWS e ambientes híbridos (AWS e on-premises), ajudando na operação, manutenção e governança de infraestrutura.

- **Session Manager**: Acesso seguro e sem necessidade de SSH ou RDP a instâncias EC2 ou servidores on-premises.
- **Parameter Store**: Armazena e gerencia dados de configuração, como chaves de API, parâmetros e segredos.
- **Run Command**: Executa comandos remotos em instâncias EC2 ou servidores on-premises sem necessidade de login direto.
- **Automation**: Automatiza tarefas operacionais, como criação de snapshots ou aplicação de patches.
- **Patch Manager**: Gerencia patches de sistemas operacionais, garantindo conformidade e segurança.
- **OpsCenter**: Consolida e rastreia problemas operacionais detectados em ambientes gerenciados.
- **Inventory**: Coleta dados de configuração de instâncias EC2 e servidores on-premises para auditorias e relatórios.
- **State Manager**: Garante que os estados desejados (como configurações ou patches) sejam aplicados automaticamente às instâncias.
- **Application Manager**: Monitora a integridade de aplicativos e fornece insights em um painel centralizado.
**Modelo de Preços**:

- **Gratuito para Algumas Funcionalidades**:
    - Inventário, Parameter Store (parâmetros padrão) e execução básica de comandos.
- **Pague pelo uso**:
    - Custos adicionais para execução avançada de automações, armazenamento de parâmetros avançados e uso de OpsCenter e Application Manager.
    - Algumas funcionalidades, como Patch Manager e Run Command, são cobradas conforme o número de instâncias gerenciadas.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Systems Manager como uma solução para gerenciar e automatizar recursos em ambientes híbridos.
- Reconhecer funcionalidades como Session Manager (acesso seguro a servidores) e Patch Manager (aplicação de patches).
- Compreender como o Systems Manager centraliza o gerenciamento de infraestrutura para reduzir esforços operacionais.