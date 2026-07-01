### Arquitetura do Binário em Go

O sistema deve ser dividido em cinco componentes principais independentes.

#### 1. Entrypoint & Config Manager

O ponto de partida do binário. Ele não deve ter regras de negócio, apenas orquestrar a inicialização.

- **Função:** Ler um arquivo de configuração (YAML ou JSON) que define quais portas abrir, quais credenciais falsas serão aceitas e os caminhos dos arquivos de log.
    
- **Sugestão:** Utilize a biblioteca `viper` para gerenciar as configurações, facilitando a injeção de variáveis de ambiente quando você for conteinerizar o honeypot.
    

#### 2. Network Listeners (SSH e Telnet)

Módulos responsáveis por aceitar conexões TCP.

- **Função:** Abrir os _sockets_ (ex: portas 2222 e 2323, que depois serão mapeadas para 22 e 23 no firewall/container) e gerenciar o _handshake_ dos protocolos.
    
- **Implementação SSH:** Utilize a biblioteca oficial `golang.org/x/crypto/ssh`. Ela permite criar um servidor SSH customizado onde você intercepta a tentativa de login e, em vez de validar no sistema operacional, você valida contra a sua lista de credenciais do Config Manager.
    
- **Concorrência:** Toda vez que um listener aceitar uma conexão (`net.Accept()`), ele deve imediatamente despachar o tratamento dessa conexão para uma nova _goroutine_. Isso garante que um ataque de força bruta não trave o recebimento de novas conexões.
    

#### 3. Emulador de Terminal (Fake Shell)

O núcleo da média interação. É aqui que você engana o atacante.

- **Função:** Após uma autenticação "bem-sucedida", o atacante ganha acesso a este módulo. Ele deve simular um sistema de arquivos básico e responder a comandos comuns do Linux que as botnets usam no reconhecimento (ex: `uname -a`, `wget`, `cat /proc/cpuinfo`).
    
- **Sugestão de Design:** Crie um _parser_ de _strings_ simples. Use interfaces em Go para permitir que novos comandos falsos sejam adicionados facilmente.
    
- **Raciocínio:** Se o atacante digitar `wget http://malware.sh`, seu Fake Shell não deve baixar o arquivo de verdade, mas deve retornar a _string_ simulando a barra de progresso do download e, crucialmente, enviar a URL tentada para o módulo de logs.
    

#### 4. Logger Estruturado (Event Router)

A extração de dados é a parte mais crítica do honeypot.

- **Função:** Receber todos os eventos (tentativas de login, IPs, comandos digitados) e gravá-los em disco.
    
- **Segurança e Performance:** Nunca faça o módulo de rede ou o Fake Shell escrever diretamente no disco (I/O bloqueante). Em vez disso, crie um **Channel** no Go. Todas as sessões SSH/Telnet enviam _structs_ de eventos para esse _channel_.
    
- **Sugestão:** Tenha uma única _goroutine_ dedicada apenas a ler desse _channel_ e escrever em um arquivo `.json` ou `.log`. O formato JSON é obrigatório aqui, pois facilitará imensamente a ingestão nativa por agentes como o do Wazuh, que monitorará esse arquivo e mandará para o seu SIEM.
Para visualizar como as peças se encaixam, pense na estrutura de dados que fluirá entre os módulos:
```
// Exemplo estrutural de como o evento deve ser modelado
type HoneypotEvent struct {
    Timestamp   time.Time `json:"timestamp"`
    SourceIP    string    `json:"source_ip"`
    Protocol    string    `json:"protocol"` // SSH ou Telnet
    EventType   string    `json:"event_type"` // "auth_attempt", "command_execution"
    Payload     string    `json:"payload"` // A senha tentada ou o comando digitado
    SessionID   string    `json:"session_id"`
}
```

**Como funciona na prática:**

1. O Listener recebe o IP `192.168.1.50` no SSH. Cria um `SessionID`.
    
2. O atacante tenta o usuário `root` e senha `admin`. O módulo de Auth bloqueia (ou aceita) e envia um `HoneypotEvent` para o _channel_ do Logger.
    
3. Se aceito, o Fake Shell assume a sessão. O atacante digita `whoami`. O Fake Shell responde `root` na conexão TCP e envia outro `HoneypotEvent` para o _channel_.
    
4. O Logger consome o _channel_ e grava as linhas em JSON no arquivo isolado.
    

Essa separação de responsabilidades garante que, se o parser de comandos falhar devido a um _input_ bizarro do atacante, apenas a _goroutine_ daquela sessão específica sofrerá _panic_, mantendo o honeypot e a coleta de logs intactos para os demais ataques.

