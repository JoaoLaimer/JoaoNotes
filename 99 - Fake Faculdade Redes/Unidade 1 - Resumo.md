Hosts = Hospedeiros
Enlaces (links) = Meios de comunicação
- fibra, cobre, rádio, satélite

Comutadores de pacotes = Dispositivos intermediários
- Roteadores e switches
- comutadores?

Resto é nada haver

### Núcleo da rede
Roteadores conectados.
- Transmissão "armazena e reenvia"
	- O comutador (intermediário) de pacotes deve receber o pacote inteiro antes de poder começar a transmitir o primeiro bit para o enlace (meio) de saída.
	- Fila de pacotes armazenados no roteador.
	- Leva  L/R segundos para transmitir um pacote de L bits no enlace a R bps.
	- Atraso fim-fim = 2L/R (assumindo atraso de propagação zero).
	- Exemple:  L = 7.5 Mbits, R = 1.5 Mbits: Atraso de transmissão de "um passo" = 5s, Atraso fim-fim = 10s.
## TCP/IP Stack
Originalmente : Application  -> Transport -> Internet (IP) ->  Network Access
Segundo o livro esquisito do professor: 
- Aplicação: FTP, SMTP, HTTP
- Transport: TCP,UDP
- Rede: IP
- Enlace: Ethernet, 802.11x,
- Física: bits 

## OSI Stack
- Aplicação
- Apresentação: (**Data translation, Encryption and decryption, data compression, formatting** ) Permite às aplicações interpretar significado de dados, realizar criptografia, compressão, etc.
- Sessão: (**Dialogue Control, duplex, Session Establishment and Release, Synchronization, Session maintenance, NetBIOS, SMB**) sincronização, checagem de dados, recuperação de perda de dados, etc.
- Transporte
- Rede
- Enlace 
- Física