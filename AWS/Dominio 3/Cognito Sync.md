[[Tecnologia e serviços da nuvem]]
Cognito Sync é um serviço que permite sincronizar dados de aplicativos entre dispositivos para usuários autenticados ou anônimos, armazenando-os no Amazon Cognito. Ele é voltado para aplicativos móveis e web que precisam compartilhar informações como preferências ou estados do usuário entre múltiplos dispositivos.
- **Sincronização entre Dispositivos**: Permite que aplicativos mantenham dados do usuário consistentes em diferentes dispositivos.
- **Armazenamento de Dados do Usuário**: Cada usuário tem um repositório exclusivo no Cognito Sync para armazenar pares chave-valor.
- **Funcionamento Offline**: Os dados podem ser armazenados localmente e sincronizados com a nuvem quando o dispositivo estiver online.
- **Integração com Identidades Cognito**: Trabalha em conjunto com Amazon Cognito Identity para associar os dados a identidades únicas.
- **Notificações em Tempo Real**: Usa Amazon SNS para notificar dispositivos sobre atualizações de dados sincronizados.
- **Gerenciamento Seguro**: Controle de acesso detalhado para proteger os dados do usuário com permissões configuráveis via AWS IAM.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados no número de operações de sincronização realizadas e no armazenamento de dados.
    - Notificações via SNS podem gerar custos adicionais.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Cognito Sync como uma solução para sincronização de dados entre dispositivos.
- Reconhecer sua integração com Cognito Identity para gerenciamento de identidades e acesso.
- Compreender como ele suporta sincronização offline para dados do usuário.