[[Tecnologia e serviços da nuvem]]
Serviço de implantação totalmente gerenciado que automatiza a distribuição de código para instâncias EC2, servidores on-premises, contêineres e serviços como AWS Lambda.
- **Suporte a Diferentes Plataformas**: Funciona com instâncias EC2, servidores físicos ou virtuais on-premises, ECS e funções Lambda.
- **Modelos de Implantação**:
    - **All-at-Once**: Atualiza todas as instâncias de uma só vez.
    - **Rolling**: Atualiza as instâncias em lotes.
    - **Canary**: Atualiza uma pequena parte para teste antes da implantação total.
    - **Blue/Green**: Direciona o tráfego para uma nova versão enquanto mantém a versão anterior disponível como backup.
- **Automação**: Automatiza todo o processo de implantação, reduzindo erros manuais e tempo de inatividade.
- **Integração com Outras Ferramentas AWS**: Funciona bem com AWS [[CodePipeline]] para pipelines de CI/CD e [[CloudWatch]] para monitoramento de implantações.
- **Rollbacks Automáticos**: Permite reverter automaticamente para a versão anterior em caso de falhas.
- **Monitoramento e Notificações**: Suporte para Amazon CloudWatch, SNS e logs para rastrear o progresso e identificar problemas.
- **Gerenciamento de Configuração**: Oferece controle detalhado sobre como o software é implantado e atualizado.
**Modelo de Preços**:

- **Gratuito**:
    - Implantação em EC2, Lambda ou ECS não gera custos adicionais.
- **Pague pelo uso**:
    - Implantação em servidores on-premises ou outros ambientes fora da AWS pode gerar custos.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS CodeDeploy como uma solução para automação de implantações.
- Reconhecer os modelos de implantação, como Rolling, Canary e Blue/Green, e quando usá-los.
- Compreender como o CodeDeploy minimiza downtime e facilita rollbacks automáticos.