TCP IP STACK NOME DOS PACOTES
APPLICATION -> DATA
TRANSPORT -> SEGMENT (TCP) OR DATAGRAM (UDP)
INTERNET -> PACOTE
LINK -> FRAME

Go-Back-N
Remetente pode ter até N pacotes nao reconhecidos no pipeline, receptor envia paenas ACK cumulativo.
Remetente tem temporizador para o pacote sem ACK mais antigo

Janela de remetente = N <- é o timeout 
manda 1, 2, 3, 4 ->
<- ack 1 2 3 4
-> 5 6 7 8 ( 7 nao chega)
<- ack 5 6 6 (mais um ack 6 pois a sequencia foi quebrada, ignora )
-> manda 7 8 9 10 (depois od timeout do pck 7)

Reenvia pacotes desde o que foi perdido

Repeticao Seletiva (SR)
Não reenvia pacotes

## TCP Controle de Congestionamento
Controle de congestionamento fim-a-fim:
- sem feedback 
- congestionamento inferido da perda e do atraso
- abordagem usada pelo TCP
Controle de congestionamento assistido pela rede:
- roteadores provêm feedback aos sistema finais.
- um bit indicando congestionamento(SNA, Decbit, TCP/IP, ECN, ATM)
- taxa explicita para o remetente enviar.

Abordagem: remetente aumenta taxa de trasmissao (janela) até que perda ocorra
- aumento aditivo: auimento de `cwnd` em 1 MSS a cada RTT até que perda seja detectada.
- reducao multiplicativa: reduz `cwnd` á metada após perda
`cwnd` = janela de congestionamento.

Três etapas:
- Partida Lenta
- Prevenção de Congestionamento
- Recuperação Rápida
 Remetente limita Transmissao
## TCP: Partida Lenta (PL)
- Quando conexão começa, aumenta a taxa exponencialmente até primeira perda:
- início: `cwnd` = 1 MSS
- dobra `cwnd` a cada RTT
- feito por incremento de `cwnd` a cada ACK recebido
Perda indicada por um timeout:
    Reinicia Partida Lenta (PL) e cresce exponencialmente até limiar, depois passa à Prevenção de Congestionamento (PC) e cresce linearmente.
Perda indicada por 3 ACKs duplicados
- rede é capaz de entregar alguns segmentos!
- `cwnd` é cortado à metade
- Retransmite o segmento que falta e passa para a Recuperação Rápida (RR)

## TCP: Prevenção de Congestionamento (PC)
O aumento exponencial para quando o `cwnd` chega ao `ssthresh`
Em evento de perda `ssthresh` é setado à metade do `cwnd` antes do evento de perda (`cwnd`/2)

Termina quando á perda indicada por um timeout: 
- `cwnd` colocado em 1 e calcula limiar `sshtresh` 
- volta à Partida Lenta (PL) e cresce exponencialmente até limiar, depois passa á Prevenção de Congestionamento (PC e cresce linearmente)
Perda indicada por 3 ACKs duplicados:
- `cwnd` é cortado à metade.
- Retransmite o segmento que falta e passa para a Recuperação Rápida (RR).

## TCP: Recuperação Rápida (RR)
inicia por decorrência de 3 ACKs duplicados.
Segmento perdido foi retransmitido
O valor de `cwnd` aumenta 1 MSS para cada ACK duplicado recebido no segmento perdido.
Quando chega o ACK de retransmissão, volta para PC 
Se houver timeout:
- `cwnd` colocado em 1;
- calcula limiar `sshtresh`
- volta à Partida Lenta (PL)
