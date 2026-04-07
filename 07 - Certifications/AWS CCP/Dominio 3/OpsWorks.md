[[Tecnologia e serviços da nuvem]]
AWS OpsWorks é um serviço de gerenciamento de configuração e automação que usa **Chef** e **Puppet** para gerenciar servidores em instâncias EC2, data centers locais ou outras plataformas de nuvem. Ele é projetado para configurar, operar e automatizar tarefas de infraestrutura de forma consistente e repetível.
**1. Modelos de Implantação**

- **OpsWorks Stacks**: Permite gerenciar arquiteturas de aplicativos de pilha completa, incluindo a configuração de servidores, bancos de dados e balanceadores de carga.
- **OpsWorks for Chef Automate**: Proporciona um servidor gerenciado do Chef para automação de configurações, gerenciamento de nós e conformidade.
- **OpsWorks for Puppet Enterprise**: Oferece um servidor Puppet gerenciado para orquestração de infraestrutura com controle detalhado.

**2. Automação de Configuração**

- Usa **receitas Chef** ou **manifests Puppet** para instalar e configurar software automaticamente.
- Permite configuração automática de instâncias ao serem inicializadas ou modificadas.

**3. Gerenciamento de Estados**

- Garante que a infraestrutura esteja em conformidade com a configuração desejada, aplicando alterações automaticamente quando necessário.

**4. Suporte Multi-Plataforma**

- Gerencia servidores em AWS, data centers on-premises ou outras plataformas de nuvem como Microsoft Azure e Google Cloud.

**5. Controle de Versões**

- Integração com repositórios de código como Git para gerenciar versões de configurações e receitas.

**6. Escalabilidade**

- Configura automaticamente servidores adicionais para lidar com cargas de trabalho aumentadas.
- Automatiza a desativação de servidores quando a demanda diminui.

**7. Monitoramento e Logs**

- Integração com CloudWatch Logs para rastrear desempenho e solucionar problemas em tempo real.
- Coleta métricas de uso e eventos de configuração para análise posterior.

**8. Segurança**

- Controle de acesso granular via IAM para gerenciar quem pode implantar, configurar ou operar instâncias.
- Suporte para criptografia de dados sensíveis em trânsito e repouso.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos com base no número de nós gerenciados por Chef Automate ou Puppet Enterprise.
    - Cobrança adicional para instâncias EC2, armazenamento e outros recursos subjacentes usados no OpsWorks.
**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS OpsWorks como uma solução para automação de configuração com Chef ou Puppet.
- Reconhecer os diferentes modelos de implantação, como **OpsWorks Stacks** e **OpsWorks for Puppet Enterprise**.
- Compreender sua aplicação em ambientes híbridos para gerenciar configurações em várias plataformas.