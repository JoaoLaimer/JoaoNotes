## Arquiteturas
- Cliente-Servidor
- Peer-to-peer (P2P)
## Comunicacao de Processos
**Processo**: programa executado num hospedeiro
processo envia/recebe mensagens para/do seu socket
**identificadores**: ip e port

## HTTP 1.0
- Não persistente, não mantem informação sobre a conexão
Passos:
1. cliente HTTP incia conexao com server
2. servidor aceita
3. cliente envia requisição
4. servidor recebe requisição e envia resposta
5. servidor http fecha a conexão tcp
6. cliente http recebe mensagem de resposta e arquivo.
7. passos são repetidos para cada requisição.

### Tempo de resposta
**RTT (Round Trip Time)**: tempo de viagem de ida e volta
**Tempo de resposta HTTP**: Do inicio do lançamento da mensagem ate quando a resposta chegar.

## Correio Eletronico
- Agentes de Usuario
- Servidores de correio
- SMTP (simple mail transfer protocol)

### Agent Usuario
POP3/IMAP para receber msgs
SMTP cliente para enviar msgs

### Servidores de Correio
Caixa postal contém mensagens que chegaram para o usuário.
Fila de mensagens de saída (a serem enviadas)
Simple Mail Transfer Protocol
protocolo SMTP entre servidores de correio para enviar mensagens
- cliente: servidor que envia a mensagem
- “servidor”: servidor que recebe a mensagem

## SMTP
PORT 25 ou 587
Transferência direta: servidor remetente para servidor receptor; sem intermédio.

## Protocolos de Acesso ao Correio
- SMTP: entrega/armazenamento para o servidor do receptor
- protocolo de acesso ao correio: recuperação do servidor
-  POP: Post Office Protocol [RFC 1939]: autorização, download
-  IMAP: Internet Mail Access Protocol [RFC 1730]: mais funções, incluindo manipulação de mensagens armazenadas no servidor (143)
-  HTTP: Gmail, Hotmail, Yahoo! Mail, etc.
## POP3 (Post Office Protocol Version 3)
110 995
comandos do cliente:
▪ user: declara username
▪ pass: password
respostas do servidor:
▪ +OK
▪ -ERR
list: lista número de mensagens
retr: recupera a mensagem por número
dele: deleta
quit

no POP3 o usuário pode classificar localmente (no agente de usuário) as mensagens em pastas

no IMAP, cada mensagem que chega na caixa postal é diretamente associada a uma pasta (INBOX)

usuário pode organizar as mensagens em pastas no servidor, pesquisá-las, deletar, mover, etc.

Pulei FTP fodace nao tenm nada novo
port 21 e 20
21 pra controle e 20 pra dados

## DNS (DOMAIN NAME SYSTEM)
Record = (name, value, type, ttl)
Tipo A = Nome para Ipv4
TIPO NS  = Qual servidores de nomes são autoritativos para um dominio, indicando onde encontrar os registros DNS daquele dominio.
Tipo CNAME = Apelido do server, value e o nome canonico.
Tipo MX = valor é o nome canonico do servidor correio

