[[Tecnologia e serviços da nuvem]]
Serviço de controle de versão totalmente gerenciado que permite hospedar repositórios Git privados, facilitando a colaboração em código entre equipes de desenvolvimento.
- **Compatibilidade com Git**: Funciona com ferramentas e comandos padrão do Git, permitindo uma integração fácil em fluxos de trabalho existentes.
- **Repositórios Privados**: Permite armazenar código-fonte, binários e outros artefatos com segurança e acessibilidade.
- **Controle de Acesso**: Integração com AWS Identity and Access Management (IAM) para gerenciar permissões detalhadas por repositório ou usuário.
- **Segurança Avançada**: Criptografia em repouso e em trânsito garante a proteção dos dados.
- **Notificações e Gatilhos**: Suporte para notificações via Amazon SNS ou integração com AWS Lambda para automatizar ações com base em eventos, como commits ou merges.
- **Integração com Outras Ferramentas AWS**: Funciona bem com serviços como AWS [[CodePipeline]], AWS [[CodeBuild]] e AWS [[CodeDeploy]] para criar pipelines de CI/CD completos.
- **Sem Limite de Repositórios**: Permite criar quantos repositórios forem necessários, com cobrança baseada apenas no uso.
**Modelo de Preços**:

- **Gratuito**:
    - Inclui 5 usuários ativos mensais e até 50 GB de armazenamento e 10.000 solicitações Git/mês por repositório.
- **Pague pelo uso**:
    - Cobrança adicional para usuários, armazenamento e solicitações Git que excedam os limites gratuitos.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS CodeCommit como uma solução para controle de versão com repositórios Git privados.
- Reconhecer os benefícios de segurança e integração com outros serviços AWS para pipelines de CI/CD.
- Compreender o modelo de preços, com destaque para os limites gratuitos e cobranças por uso adicional.