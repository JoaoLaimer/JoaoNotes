[[Segurança e conformidade]]
Amazon Inspector é um serviço de avaliação de segurança automatizado que ajuda a melhorar a segurança e a conformidade das aplicações implantadas na AWS. Ele automatiza a identificação de vulnerabilidades e desvios de melhores práticas em instâncias do Amazon EC2 e em aplicações, fornecendo recomendações detalhadas para remediação.
- **Avaliações de Segurança Automatizadas**: Executa varreduras contínuas ou agendadas para identificar vulnerabilidades de segurança, falhas de configuração e práticas inseguras em sistemas operacionais e aplicativos.
- **Detecção de Vulnerabilidades**: Identifica vulnerabilidades conhecidas em pacotes de software, configurações de rede e práticas de segurança, utilizando uma base de dados atualizada de vulnerabilidades.
- **Relatórios Detalhados**: Fornece relatórios claros e acionáveis que priorizam achados com base na gravidade e no impacto, facilitando a tomada de decisões para remediação.
- **Integração com Outros Serviços AWS**: Integra-se com AWS Security Hub para centralizar achados de segurança, AWS Lambda para automação de respostas e Amazon CloudWatch para monitoramento contínuo.
- **Escalabilidade**: Capaz de avaliar milhares de instâncias EC2 e aplicações em grande escala sem necessidade de gerenciamento manual.
- **Customização de Avaliações**: Permite definir escopos personalizados para avaliações, incluindo a seleção de pacotes de regras específicas e a aplicação de políticas de segurança personalizadas.
- **Agendamento Flexível**: Oferece a capacidade de agendar avaliações em horários que minimizam o impacto operacional, garantindo que a segurança seja mantida sem interromper as operações.
- **Suporte a Compliance**: Auxilia no cumprimento de normas de segurança e regulamentações como PCI DSS, HIPAA, e CIS Benchmarks, fornecendo insights e relatórios alinhados com esses padrões.
- **Conformidade de Rede**: Avalia configurações de rede, como grupos de segurança e listas de controle de acesso (ACLs), para identificar configurações que possam expor recursos de forma insegura.
- **Atualizações Contínuas**: Recebe atualizações regulares para suportar novas vulnerabilidades e melhores práticas de segurança, garantindo que as avaliações estejam sempre alinhadas com o estado atual da segurança.
**Modelo de Preços**:

- **Pague pelo uso**:
    
    - **Avaliações**: Cobrança baseada no número de instâncias avaliadas e no tipo de avaliação realizada.
    - **Tipos de Avaliação**: Diferentes tipos de avaliações podem ter preços variados, dependendo da profundidade e do escopo da análise.
    - **Recursos Adicionais**: Custos adicionais podem se aplicar para integrações com outros serviços AWS, como AWS Security Hub ou AWS Lambda.
- **Camada Gratuita**:
    
    - Geralmente, novas contas AWS podem ter acesso a uma quantidade limitada de avaliações gratuitas durante um período promocional, mas isso pode variar. Verifique a [página de preços do Amazon Inspector](https://aws.amazon.com/inspector/pricing/) para detalhes atualizados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- **Identificar o Amazon Inspector como uma ferramenta de avaliação de segurança**: Reconhecer o papel do Inspector na identificação de vulnerabilidades e na melhoria da postura de segurança.
- **Compreender a integração com outros serviços AWS**: Saber como o Inspector se conecta com AWS Security Hub, AWS Lambda e outros serviços para fornecer uma solução de segurança integrada.
- **Conhecer os modelos de preços e quando utilizá-los**: Entender que o Amazon Inspector cobra com base no uso, facilitando a escalabilidade conforme as necessidades de segurança aumentam.
- **Reconhecer os benefícios de conformidade**: Compreender como o Inspector auxilia no cumprimento de normas de segurança e regulamentações através de avaliações automatizadas e relatórios detalhados.