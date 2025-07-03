1. **Descreva, brevemente, três (dos seis) principais serviços de um Sistema Operacional visto em aula.**

_1) Interface do usuário: Linha de comando e gráfica._
_2) Execução d programa: carregamento do programa em memória, escalonamento._
_3) Operações de entrada e saída: gerenciamento dos dispositivos I/O._
_4) Manipulação do sistema de arquivos: abstrair tipo do dispositivo e formato do arquivo, e mecanismos de proteção._
_5) Acesso ao sistema (recursos): proteger contra acesso não autorizado e disputas._
_6) Detecção e correção de error: erros de HW e SW._

2. **O que caracteriza um sistema operacional de tempo real? Quais as duas classificações de sistemas operacionais de tempo real e suas diferenças?

_Sistemas de tempo real são projetados para cumprir prazos e ter um comportamento previsível sendo possível projetar aplicações que dependem do tempo. Temos dois tipos de sistemas operacionais de tempo real: soft real-time, que se preocupa cumprir prazos, porém se não os cumprir o sistema continua normalmente, pois não haverá consequências catastróficas, porém elas ainda são visíveis, e hard real-time, onde o cumprimento de prazos deve ser garantido pois o não cumprimento dos prazos pode acarretar em consequências graves, levando a danos estruturais e humanos._

3. **Explique brevemente (uma característica para cada) sobre três estruturas típicas de SO, são elas: Sistemas Monolíticos, Modelo Microkernel, Modelo Cliente-Servidor.

_Sistemas Monolíticos possuem um bloco massivo de serviços todos rodando ao nível kernel, assim todos os serviços possuem acesso de mais alto nível._
_Em modelos Microkernel somente o necessário para o acesso ao hardware e abstrações básicas estão no kernel, o resto dos serviços rodam no espaço do usuário, e podem ser modularizar, aumentando a flexibilidade do sistema._
_No modelo Cliente-Servidor, o cliente envia mensagens ao serviços, requisitando serviços, e o servidor realiza o trabalho e envia uma mensagem resposta ao cliente. O kernel neste modelo, é somente responsável pela troca de mensagens._

4. **Considere o seguinte conjunto de 5 processos onde chegada é o instante de tempo que o processo se tornou apto pela primeira vez, t é o tempo necessário a execução do processo (tempo total de CPU) e p a sua prioridade.**

| Processo/Pid | Chegada | Tempo de CPU (t) | Prioridade (p) |
| ------------ | ------- | ---------------- | -------------- |
| P0           | 0       | 60               | 0              |
| P1           | 15      | 25               | 1              |
| P2           | 20      | 15               | 0              |
| P3           | 65      | 15               | 1              |
| P4           | 70      | 10               | 2              |
**Assumindo que a execução inicie no tempo zero, desenho o diagrama de execução desses 5 processos, isto é, quem está ocupando a CPU em casa instante de tempo, considerando um escalonamento em múltiplas filas com as seguintes politicas de escalonamento em cada fila:
(i) FIFO não preemptivo;
![[Pasted image 20250616184415.png]]
(ii) PRIOp; por prioridades, preemptivo.
![[Pasted image 20250616184904.png]]
Supor que processos com prioridades de valores numéricos menores são os mais prioritários. EM caso de empates, considerar como critério de desempate o pid do processo (o processo de menor pid ganha a disputa).**

5. **Em relação aos componentes de um espaço de endereçamento (código, dados globais, monte e pilha), qual a diferença entre se criar dez processos e se criar dez threads dentro de um processo? O modelo de threads (N:1 , 1:1 e M:N) tem impacto na sua resposta? Se SIM, EXPLIQUE como.**

A diferença de usar dez threads ou dez processos, é que utilizando 10 threads possuímos o compartilhamento do espaço de endereçamento, evitando a troca de contexto e simplificando o compartilhamento dos recursos, porém o paralelismo muda dependendo do modelo de threads utilizado. O modelo N:1, não possui paralelismo, pois somente uma thread sera mapeada para a unica thread de kernel por vez. No modelo 1:1 possuímos paralelismo, porém o desempenho é prejudicado pois precisamos de uma thread de kernel para cada uma de usuário. E por fim, no modelo M:N, temos um equilíbrio entre os dois outros modelos ao custo de uma implementação mais complexa e gerenciamento mais custoso.

6. **Qual, ou quais, entre os algoritmos básicos de escalonamento listados a seguir, podem resultar em inanição (starvation)? Para cada algoritmo que POSSA gerar inanição EXPLIQUE como, SE possível, essa situação pode ser evitada.**
a) First Come, First Server (FCFS);
 _Não gera starvation._
b) Shortest Job First (SJF);
_O SJF pode causar starvation em tarefas que possuem grande tempo de execução, sendo "afogadas" por diversas tarefas menores._
c) Round Robin;
_Não gera starvation._
d) Por prioridade;
_Se existir uma tarefa com a menor prioridade possível, pode ser que ela nunca seja executada, pois diversas outras tarefas com a prioridade maior continuem a ser executadas. Para evitar esse cenário, é utilizado a técnica do "aging", que aumenta a prioridade de uma tarefa conforme o tempo passa, quando mais tempo ela estiver na fila maior sera sua prioridade, consequentemente ela sera executada._