[[Segurança e conformidade]]

Serviço que permite compartilhar recursos da AWS de forma segura e eficiente entre contas de uma organização ou com contas confiáveis, sem a necessidade de duplicar recursos.
- **Compartilhamento de Recursos**: Permite compartilhar recursos como VPCs, sub-redes, tabelas do Route 53, AWS Transit Gateway, e mais.
- **Integração com AWS Organizations**: Facilita o compartilhamento de recursos entre contas dentro de uma organização AWS.
- **Controle Detalhado de Acesso**: Usa permissões baseadas em políticas do AWS Identity and Access Management (IAM) para definir quem pode acessar os recursos compartilhados.
- **Evita Duplicação de Recursos**: Reduz custos e simplifica a configuração, eliminando a necessidade de criar recursos separados para cada conta.
- **Monitoramento e Relatórios**: Integração com AWS [[CloudTrail]] para rastrear atividades relacionadas ao compartilhamento de recursos.
- **Segurança Avançada**: Garante que os recursos compartilhados sejam acessados apenas por contas confiáveis, com políticas claras e restritas.
**Modelo de Preços**:

- **Gratuito**:
    - Não há custos adicionais para usar o AWS RAM.
    - Cobranças são aplicadas apenas pelo uso dos recursos compartilhados (ex.: VPCs, gateways).

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS RAM como uma solução para compartilhar recursos entre contas AWS.
- Reconhecer a integração com AWS Organizations como uma forma de facilitar o gerenciamento em ambientes multi-conta.
- Compreender os benefícios de segurança e economia ao evitar duplicação de recursos.