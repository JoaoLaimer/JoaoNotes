## Capítulo 1:
1. **Quais os dois principais objetivos de um sistema operacional?**

_Os principais objetivos de um SO são: A abstração de recursos e a gerencia dos mesmos_.

2. **Por que a abstração de recursos é importante para os desenvolvedores de aplicações? Ela tem alguma utilidade para os desenvolvedores do próprio sistema operacional?**

_Acesso a recursos do hardware, se não abstraídos, é muito complexo, dificultando o desenvolvimento de programas e aplicações_.

3. **A gerência de tarefas permite compartilhar o processador, executando mais de uma aplicação ao mesmo tempo. Identifique as principais vantagens trazidas por essa funcionalidade e os desafios a resolver para implementá-la.**

_Distribuir a capacidade de processamento de forma justa entre as aplicações.
Evitar que uma aplicação monopolize o recurso do processador.
Respeitar as prioridades definidas pelos usuários._

4. **O que caracteriza um sistema operacional de tempo real? Quais as duas classificações de sistemas operacionais de tempo real e suas diferenças?**

_São sistemas operacionais onde o tempo é critico para o funcionamento, ou seja, que suas aplicações tenham comportamento temporal previsível. Eles podem ser críticos ou não críticos, onde um a perde de tempo pode gerar consequências graves e o outro a perda de tempo, por mais que não desejável, não possui consequências pesadas.__

5. **Relacione as afirmações aos respectivos tipos de sistemas operacionais: distribuído (D), multi-usuário (M), desktop (K), servidor (S), embarcado (E) ou de tempo-real (T):**
( T ) Deve ter um comportamento temporal previsível, com prazos de resposta
claramente definidos.
( S ) Sistema operacional usado por uma empresa para executar seu banco de
dados corporativo.
( E ) São tipicamente usados em telefones celulares e sistemas eletrônicos
dedicados.
( D ) Neste tipo de sistema, a localização física dos recursos do sistema compu-
tacional é transparente para os usuários.
( M ) Todos os recursos do sistema têm proprietários e existem regras controlando
o acesso aos mesmos pelos usuários.
( E ) A gerência de energia é muito importante neste tipo de sistema.
( K ) Sistema que prioriza a gerência da interface gráfica e a interação com o
usuário.
( S ) Construído para gerenciar de forma eficiente grandes volumes de recursos.
( K ) O MacOS X é um exemplo típico deste tipo de sistema.
( E ) São sistemas operacionais compactos, construídos para executar aplicações
específicas sobre plataformas com poucos recursos.

6. **Sobre as afirmações a seguir, relativas aos diversos tipos de sistemas operacionais, indique quais são incorretas, justificando sua resposta:**

**(a) Em um sistema operacional de tempo real, a rapidez de resposta é menos importante que a previsibilidade do tempo de resposta.**

_Sim, em um sistema de tempo real a previsibilidade de um sistema é mais importante que sua rapidez, pois assim, podemos construir aplicações que dependem dessa previsibilidade._

**(b) Um sistema operacional multi-usuários associa um proprietário a cada recurso do sistema e gerencia as permissões de acesso a esses recursos.**

_Sim, em um sistema multi-usuários, os princípios, são o gerenciamento de permissões de acesso a diversos recurso para diferentes usuários._

**(c) Nos sistemas operacionais de rede a localização dos recursos é transparente para os usuários.**

_Não, esta definição cabe ao sistema operacional distribuído. No sistema operacional de rede, os recursos são compartilhados localmente, porém, podem não ser transparente a todos os usuários, possuindo controle de acesso aos recursos._

**(d) Um sistema operacional de tempo real deve priorizar as tarefas que interagem com o usuário.**

_Não, um sistema operacional de tempo real deve ser sensibilizado a cumprir prazos temporais e priorizando previsibilidade._ 

**(e) Um sistema operacional embarcado é projetado para operar em hardware com poucos recursos.**

_Sim, um sistema embarcado é projetado geralmente para cumprir uma tarefa em especifica, não sendo necessário diversos recursos._

## Capítulo 2:
1. **O que diferencia o núcleo do restante do sistema operacional?**

_O núcleo de um sistema operacional é responsável pela gerencia de recursos do hardware utilizado pelas aplicações, e também é o núcleo que aplica as abstrações necessárias pelos 
programas, e também, núcleo difere pelos seus privilégios de execução, o kernel mode._

2. **Seria possível construir um sistema operacional seguro usando um processador que não tenha níveis de privilégio? Por quê?**

_Não seria, pois sem delegação de privilégios para diferentes partes do sistema seria possível qualquer aplicação acessar níveis críticos do sistema e acessar diferentes 
dispositivos sem limitações._ 

3. **Os processadores da família x86 possuem dois bits para definir o nível de privilégio, resultando em 4 níveis distintos. A maioria dos sistemas operacionais para esses processadores usam somente os níveis extremos (0 e 3, ou 002 e 112). Haveria alguma utilidade para os níveis intermediários?**

_Por mais que os níveis intermediários não tenham muita utilidade atualmente, eles podem formar conceitos como o protection ring, que introduz mais granularidade no controle de acesso, e para técnicas iniciais de virtualização, onde o sistema operacional convidado operava sobre essas camadas._

4. **Quais as diferenças entre interrupções, exceções e traps?**

_Uma interrupção ocorre quando um dispositivo precisa informar o processador sobre um evento interno. Uma exceção ocorre quando o próprio processador tenta executar instruções ilegais, tentativas de divisão por zero ou outros erros de software.
Uma trap é basicamente uma interrupção que não é causada por um dispositivo e sim pelo software, no caso das chamadas de sistema._

 5. **O comando em linguagem C fopen é uma chamada de sistema ou uma função de biblioteca? Por quê?**
_O comando fopen da linguagem C é uma função, porém nesta função ela realiza uma chamada de sistema, open()._

6. **A operação em modo usuário permite ao processador executar somente parte das instruções disponíveis em seu conjunto de instruções. Quais das seguintes operações não deveriam ser permitidas em nível usuário? Por quê?**
	(a) Ler uma porta de entrada/saída
	(b) Efetuar uma divisão inteira
	(c) Escrever um valor em uma posição de memória
	(d) Ajustar o valor do relógio do hardware
	(e) Ler o valor dos registradores do processador
	(f) Mascarar uma ou mais interrupções

_A operação (a) não deveria ser permitida para em nível de usuário porque o acesso direto a I/O em modo usuário violaria a segurança e a estabilidade do sistema.
A operação (c) também não deve ser permitida em nível usuário para posições de memorias arbitrarias ou não autorizadas.
A operação (d) também não deve ser permitida pois envolve interação direta com dispositivos. 
A operação (e) não deve ser permitida pois isso permite manipular operações especificas.
A operação (f) não deve ser permitida pois isso afeta o funcionamento do escalonador de tarefas e a capacidade do sistema operacional de responder a eventos de hardware.

7. **Considerando um processo em um sistema operacional com proteção de memória entre o núcleo e as aplicações, indique quais das seguintes ações do processo teriam de ser realizadas através de chamadas de sistema, justificando suas respostas:**
	(a) Ler o relógio de tempo real do hardware.
	(b) Enviar um pacote através da rede.
	(c) Calcular uma exponenciação.
	(d) Preencher uma área de memória do processo com zeros.
	(e) Remover um arquivo do disco.

_As ações (a), (b) e (e) devem ser realizadas através de chamadas de sistema, pois elas incluem operações que necessitam de acesso privilegiado para o kernel, que mexem com a estabilidade e segurança do sistema.
É importante se notar que a operação (d) não precisa de chamadas de sistema pois as operações seriam executadas inteiramente dentro do espaço de endereçamento de memoria que SO atribuiu ao processo, ou seja, o processo possui a permissão de escrita em sua própria memoria sem intervenção do núcleo._
8. **Coloque na ordem correta as ações abaixo, que ocorrem durante a execução da função printf("Hello world") por um processo (observe que nem todas as ações indicadas fazem parte da sequência).**
	**(a)** A rotina de tratamento da interrupção de software é ativada dentro do núcleo.
	**(b)** A função printf finaliza sua execução e devolve o controle ao código do processo.
	**(c)** A função de biblioteca printf recebe e processa os parâmetros de entrada (a string “Hello world”).
	**(d)** A função de biblioteca printf prepara os registradores para solicitar a chamada de sistema write()
	**(e)** O disco rígido gera uma interrupção indicando a conclusão da operação.
	**(f)** O escalonador escolhe o processo mais prioritário para execução.
	**(g)** Uma interrupção de software é acionada.
	**(h)** O processo chama a função printf da biblioteca C.
	**(i)** A operação de escrita no terminal é efetuada ou agendada pela rotina de tratamento da interrupção.
	**(j)** O controle volta para a função printf em modo usuário.

_(h) -> (c) -> (d) -> (g) -> (a) -> (i) -> (j) -> (b)
As operações (f) não é acionada pois não existe troca de contexto e a operação (e) não é envolvida na operação do printf.

## Capítulo 3:
1. **Monte uma tabela com os benefícios e deficiências mais relevantes das principais arquiteturas de sistemas operacionais.**

| Tipo do Sistema | Vantagens                                                                                                                                                     | Desvantagens                                                                                                                                                                                                 |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Monolítico      | Desempenho: qualquer componente do núcleo pode acessar os demais componentes diretamente.                                                                     | Problemas com robustez: se um componente falhar o erro pode propagar para o resto dos componentes.<br>Manutenção e desenvolvimento custoso: pequenas alterações na estrutura de um componente afeta o resto. |
| Micronúcleo     | Modularidade: cada serviço pode ser desenvolvido independente do outro.<br>Flexibilidade: serviços podem ser desativados e ativados conforme necessidade.<br> | Desempenho inferior: o acesso a serviços implica na mudança da metade do fluxo de execução e reconfiguração da memoria acessível pela MMU.                                                                   |
| Em Camadas      | Granularidade: camadas mais baixas tem maior privilégios e menos abstração, pois estão mais próximas ao hardware.                                             | Desempenho: o empilhamento de camadas faz que uma aplicação demore mais tempo para chegar a um dispositivo a ser acessado.<br>A ordem de empilhamento não é sempre obvia.<br>                                |
| Híbridos        | Possui uma combinação das vantagens das arquiteturas monolítica e micronúcleo.                                                                                | Possui uma combinação das desvantagens das arquiteturas monolítica e micronúcleo.                                                                                                                            |
2. **O Linux possui um núcleo similar com o da figura 3.1, mas também possui “tarefas de núcleo” que executam como os gerentes da figura 3.2. Seu núcleo é monolítico ou micronúcleo? Por quê?**

_Linux é monolítico, apesar de seu código ser modularizado em versões mais modernas, a maioria do seu código esta em modo núcleo, possuindo acesso a todos os recursos do hardware._

3. **Sobre as afirmações a seguir, relativas às diversas arquiteturas de sistemas operacionais, indique quais são incorretas, justificando sua resposta:**
	(a) Uma máquina virtual de sistema é construída para suportar uma aplicação
	escrita em uma linguagem de programação específica, como Java.
	(b) Um hipervisor convidado executa sobre um sistema operacional hospedeiro.
	(c) Em um sistema operacional micronúcleo, os diversos componentes do
	sistema são construídos como módulos interconectados executando dentro
	do núcleo.
	(d) Núcleos monolíticos são muito utilizados devido à sua robustez e facilidade
	de manutenção.
	(e) Em um sistema operacional micronúcleo, as chamadas de sistema são
	implementadas através de trocas de mensagens.

_A afirmação (a) esta incorreta, seria o caso de uma máquina virtual de aplicação.
A afirmação (b) está correta.
A afirmação (c) está incorreta, no sistema micronúcleo, os componentes não estão dentro do núcleo, o que há no núcleo é somente o necessário do núcleo.
A afirmação (d) está incorreta, núcleo monolíticos são conhecidos por não serem robustos e serem de manutenção difícil.
A afirmação (e) está correta._

## Capítulo 4:
1. **O que significa time sharing e qual a sua importância em um sistema operacional?**

_É uma técnica fundamental que surgiu para permitir que múltiplos programas pudessem usar o computador de forma aparentemente simultânea. É a ideia de compartilhar um recurso, como a CPU entre varias tarefas, o sistema operacional executa uma tarefa por um curto período de tempo, conhecido como "quantum" antes de ceder a execução para outra tarefa - conhecido como preempção._

2. **Como e com base em que critérios é escolhida a duração de um quantum de processamento?**

_O quantum deve ser escolhido de acordo com o conjunto de tarefas, pois se o quantum for pequeno, haverá muita troca de contexto no qual prejudica desempenho, porem haverá uma melhor sensação de paralelismo. 

3. **Considerando o diagrama de estados dos processos apresentado na figura a seguir, complete o diagrama com a transição de estado que está faltando (t6 ) e apresente o significado de cada um dos estados e transições.**

_e1 = Nova, a tarefa está sendo criada.
e2 = Terminada, a tarefa finalizou sua execução por completo e pode ser removida da memoria.
e3 = Executando, o processador está executando as instruções da tarefa.
e4 = Suspensa, a tarefa espera algum evento para continuar sua execução. 
e5 = Pronta, a tarefa está pronta para iniciar ou retomar sua execução._

_t1 =  Executando -> Terminada, a tarefa encerra sua execução ou é abortada.
t2 = Executando -> Suspensa, a tarefa solicita uma evento, e espera ser atendida.
t3 = Suspensa -> Pronta, a tarefa consegue o que solicitou e espera voltar a execução.
t4 = Pronta -> Executando, é a vez da tarefa ser executada pelo processador.
t5 = Nova -> Pronta, a tarefa foi criada com sucesso e espera a execução.
t6 = Executando -> Pronta, o quantum destinado a tarefa se esgota._

4. **Indique se cada uma das transições de estado de tarefas a seguir definidas é possível ou não. Se a transição for possível, dê um exemplo de situação na qual ela ocorre (N: Nova, P: pronta, E: executando, S: suspensa, T: terminada).**

- E→P - _Possível, ocorre quando uma tarefa executou durante todo o quatum._
- S→T - _Não é possível._
- E→S - _Possível, ocorre quando a tarefa depende de algum recurso/evento para continuar sua execução._
- E→T - _Possível, a tarefa completou todas suas instruções e pode ser removida._
- S→E - _Não é possível._
- N→S - _Não é possível._
- P→N - _Não é possível._
- P→S - _Não é possível._

5. **Relacione as afirmações abaixo aos respectivos estados no ciclo de vida das tarefas (N: Nova, P: Pronta, E: Executando, S: Suspensa, T: Terminada):**
(N) O código da tarefa está sendo carregado.
(P) A tarefas são ordenadas por prioridades.
(E) A tarefa sai deste estado ao solicitar uma operação de entrada/saída.
(T) Os recursos usados pela tarefa são devolvidos ao sistema.
(P) A tarefa vai a este estado ao terminar seu quantum.
(P) A tarefa só precisa do processador para poder executar.
(S) O acesso a um semáforo em uso pode levar a tarefa a este estado. - _Quando uma tarefa em "Executando" tenta acessar um semáforo que já está em uso (ou seja, executa uma operação down(s) e o contador do semáforo se torna negativo), ela é "adicionada à fila do semáforo (s.queue) e suspensa"_
(E) A tarefa pode criar novas tarefas.
(E) Há uma tarefa neste estado para cada processador do sistema.
(S) A tarefa aguarda a ocorrência de um evento externo.

## Capítulo 5:
1. **Explique o que é, para que serve e o que contém um TCB - Task Control Block.**

_O TCB - Task Control Block, é o bloco que armazena as informações e contexto de uma tarefa, ele serve para salvar a informação de uma tarefa no momento que ele para de ser executada e, quando ela volte a ser executada ela ainda mantenha seu contexto._
2. **Desenhe o diagrama de tempo da execução do código a seguir, informe qual a saída do programa na tela (com os valores de x) e calcule a duração aproximada de sua execução.**
```C
int main()
{
	int x = 0 ;
	fork () ;
	x++ ;
	sleep (5) ;
	wait (0) ;
	fork () ;
	wait (0) ;
	sleep (5) ;
	x++ ;
	printf ("Valor de x: %d\n", x) ;
}
```

![[Pasted image 20250612185018.png]]
_No final o saída é:_
```
Valor de x: 2
Valor de x: 2
Valor de x: 2
Valor de x: 2
```

3. **Indique quantas letras “X” serão impressas na tela pelo programa abaixo quando for executado com a seguinte linha de comando:**

a.out 4 3 2 1

O comando a.out resulta da compilação do programa a seguir:
```C
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include <stdlib.h>
int main(int argc, char *argv[])
{
	pid_t pid[10];
	int i;
	int N = atoi(argv[argc-2]);
	for (i=0; i<N; i++)
		pid[i] = fork();
	if (pid[0] != 0 && pid[N-1] != 0)
		pid[N] = fork();
	printf("X");
	return 0;
}
```

_No código a seguir, é criado um array com 10 posições de Ids de processos, ele atribui o argumento "2" para a variável N.
O fluxo do pai cria 2 filhos no dentro do for. 
O fluxo do primeiro filho cria mais um filho dentro do for. 
Com isso temos agora 4 fluxos de execução.
Então para o pai temos: pid(0) = filho1 e pid(1) filho2
Para o filho1 temos: pid(0) = 0 e pid(1) = neto 
Para o filho2 temos: pid(0) = filho1 e pid(1) = 0
Para o neto criado por filho1 temos: pid(0) e pid(1) = 0
O if pergunta se o primeiro e ultimo pid são diferentes de 0, ou seja, se esse fluxo de execução não é pai dessas posições ou se não herdou esses valores como o filho2 que herdou o pid do filho1 em pid(0). Se sim ele cria mais um filho, se não finaliza a execução.
Finalizando, temos 5 fluxos criados contando com o main. Então serão impressos 5 "X".

_Obs: Como esse o if verifica o array que pode herdar valores de processos parentes, é correto assumir que se N aumenta, a quantidade de processos criados cresce significantemente._

4. **O que são threads e para que servem?**
_Threads são fluxos de execução independentes de um processo. Cada thread é caracterizada por um código em execução e um pequeno contexto local._

5. **Quais as principais vantagens e desvantagens de threads em relação a processos?**

_As vantagens são, compartilhamento de dados mais facilitada, menor custo e mais agilidade na criação do que processos, e melhora na responsividade. As desvantagens são, a propagação de erro pois toda thread compartilha o mesmo espaço de endereçamento e problemas com sincronização._

6. **Forneça dois exemplos de problemas cuja implementação multi-thread não tem desempenho melhor que a respectiva implementação sequencial.**

_Quando há um alto custo de sincronização aonde uma thread somente consegue executar por vez, por exemplo: threads excessivas para uma tarefa simples como somar um vetor, ou diversos eventos para poucas threads. Isso, pode causar uma implementação multi-thread não ter o desempenho melhor que uma implementação sequencial._

7. **Associe as afirmações a seguir aos seguintes modelos de threads: a) many-to-one (N:1); b) one-to-one (1:1); c) many-to-many (N:M):**
(a) Tem a implementação mais simples, leve e eficiente.
(c) Multiplexa os threads de usuário em um pool de threads de núcleo.
(b) Pode impor uma carga muito pesada ao núcleo.
(a) Não permite explorar a presença de várias CPUs pelo mesmo processo.
(c) Permite uma maior concorrência sem impor muita carga ao núcleo.
(a) Geralmente implementado por bibliotecas.
(b) É o modelo implementado no Windows NT e seus sucessores.
(a) Se um thread bloquear, todos os demais têm de esperar por ele.
(b) Cada thread no nível do usuário tem sua correspondente dentro do núcleo.
(c) É o modelo com implementação mais complexa.

8. **Considerando as implementações de threads N:1 e 1:1 para o trecho de código a seguir:
a) desenhe os diagramas de execução
b) informe as durações aproximadas de execução
c) indique a saída do programa na tela. 
	Considere a operação sleep() como uma chamada de sistema (syscall). A chamada thread_create cria uma nova thread, thread_exit encerra a thread corrente e thread_join espera o encerramento da thread informada como parâmetro.
```C
int y = 0 ;

void threadBody
{
	int x = 0 ;
	sleep (10) ;
	printf ("x: %d, y:%d\n", ++x, ++y) ;
	thread_exit();
}

int main ()
{
	thread_create (&tA, threadBody, ...) ;
	thread_create (&tB, threadBody, ...) ;
	sleep (1) ;
	thread_join (&tA) ;
	thread_join (&tB) ;
	sleep (1) ;
	thread_create (&tC, threadBody, ...) ;
	thread_join (&tC) ;
}
```

_b) Thread A, B e C, demoram 10 segundos para concluírem desde sua criação, como indicado na função threadBody(). A main thread vai demorar 21 segundos para concluir pois, as threads A e B são criadas ao quase simultaneamente e dão join também quase simultaneamente. Após isso o main "dorme" por 1 segundo, cria a thread C e espera ela concluir._
_c) Assumindo que não irá ocorrer nenhuma condição de corrida:_
```
x: 1, y: 1
x: 1, y: 2
x: 1, y: 3
```

## Capítulo 6:
1. **Explique o que é escalonamento round-robin, dando um exemplo.**

_o algoritmo Round-Robin, pode ser descrito pela adição de preempção para o algoritmo FCFS, essa preempção é adicionada com o conceito de revezamento das tarefas. Cada tarefa nesse algoritmo tem uma quantidade de tempo de execução até ela voltar a fila, esse tempo é chamado de quantum. A ordem da fila ainda permanece como no algoritmo FCFS._

2. **Considere um sistema de tempo compartilhado com valor de quantum tq e duração da troca de contexto ttc . Considere tarefas de entrada/saída que usam em média p% de seu quantum de tempo cada vez que recebem o processador. Defina a eficiência E do sistema como uma função dos parâmetros tq , ttc e p.**

$$
E = \frac{p \cdot tq}{(p \cdot tq) + tcc}
$$
3. **Explique o que é, para que serve e como funciona a técnica de aging.**

_A técnica do aging é atribuir uma idade para as tarefas a serem escalonadas, ele atribui uma prioridade conforme a idade da tarefa. Quanto mais "velha" a tarefa mais prioridade ela vai ter na fila de escalonamento. Desta forma, evitando o starvation._

4. **No algoritmo de envelhecimento definido na Seção 6.4.6, o que seria necessário modificar para suportar uma escala de prioridades negativa?**

_Podemos somente inverter o critério de seleção para selecionar a menor prioridade e abaixar o numero da prioridade durante o tempo para evitar starvation._

5. **As tabelas a seguir representam um conjunto de tarefas prontas para utilizar um processador:**
a)

| Tarefa     | t1  | t2  | t3  | t4  | t5  |
| ---------- | --- | --- | --- | --- | --- |
| ingresso   | 0   | 0   | 3   | 5   | 7   |
| duração    | 5   | 4   | 5   | 6   | 4   |
| prioridade | 2   | 3   | 5   | 9   | 6   |
b)


| Tarefa     | t1  | t2  | t3  | t4  | t5  |
| ---------- | --- | --- | --- | --- | --- |
| ingresso   | 0   | 0   | 1   | 7   | 11  |
| duração    | 5   | 6   | 2   | 6   | 4   |
| prioridade | 2   | 3   | 4   | 7   | 9   |


**Represente graficamente a sequência de execução das tarefas e calcule os tempos médios de vida (tournaround time) e de espera (waiting time), para as políticas de escalonamento a seguir:**

**(a) FCFS cooperativa**
a.
![[Pasted image 20250616152815.png]]
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1:  9 - 0 = 9 uT
T2: 4 - 0 = 4 uT
T3: 14 - 3 = 11 uT
T4: 20 - 5 = 15 uT
T5: 24 - 7 = 17 uT

Waiting time (tempo total esperando na fila):
T1: 4 uT
T2: 0 uT
T3: 9 - 3 = 6 uT
T4: 14 - 5 = 9 uT
T5: 20 - 7 =  13 uT

b.
![[Pasted image 20250616153508.png]]
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1: 11 - 0 = 11 uT
T2: 6 - 0 = 6 uT
T3: 13 - 1 = 12 uT
T4: 19 - 7 = 12 uT
T5: 23 - 11 = 12 uT

Waiting time (tempo total esperando na fila):
T1: 6 uT
T2: 0 uT
T3: 11 - 1 = 10 uT
T4: 13 - 7 = 6 uT
T5: 19 - 11 = 8 uT

**(b) SJF cooperativa**
a. ![[Pasted image 20250616154403.png]]
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1: 18 uT
T2: 4 uT
T3: 9 - 3 = 6 uT
T4: 24 - 5 = 19 uT
T5: 13 - 7 = 6 uT

Waiting time (tempo total esperando na fila):
T1: 13 uT
T2: 0 uT
T3: 1 uT
T4: 18 - 5 = 13 uT
T5: 2 uT

b.![[Pasted image 20250616155523.png]]
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1: 5 uT
T2: 23 uT
T3: 7 - 1 = 6 uT
T4: 13 - 7 = 6 uT
T5: 17 - 11 = 6 uT

Waiting time (tempo total esperando na fila):
T1: 0 uT
T2: 17 uT
T3: 5 - 1 = 4 uT
T4: 0 uT
T5: 2 uT

**(c) SJF preemptiva (SRTF)**
a.![[Pasted image 20250616154403.png]]
Tempos iguais ao SJF Cooperativo.

b.
![[Pasted image 20250616162100.png]]
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1: 7 uT
T2: 23 uT
T3: 2 uT
T4: 13 - 7 = 6 uT
T5: 17 - 11 = 6 uT

Waiting time (tempo total esperando na fila):
T1: 2 uT
T2: 17 uT
T3: 0 uT
T4: 0 uT
T5: 2 uT

**(d) PRIO cooperativa**
a.![[Pasted image 20250616163138.png]]
(T1 vai até 23 na imagem mas na realidade vai até 24).
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1: 24 uT
T2: 4 uT
T3: 9 - 3 = 6 uT
T4: 15 - 5 = 10 uT
T5: 19 - 7 = 12 uT

Waiting time (tempo total esperando na fila):
T1: 19 uT
T2: 0 uT
T3: 1 uT
T4: 9 - 5 = 4 uT
T5: 15 - 7 = 8 uT

b.![[Pasted image 20250616164333.png]]
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1: 5 uT
T2: 23 uT
T3: 6 uT
T4: 13 - 7 = 6 uT
T5: 17 - 11 = 6 uT

Waiting time (tempo total esperando na fila):
T1: 0 uT
T2: 17 uT
T3: 5 - 1 = 4 uT
T4:  0 uT
T5: 13 - 11 = 2 uT

**(e) PRIO preemptiva**
a.![[Pasted image 20250616165142.png]]
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1: 20 uT
T2: 24 uT
T3: 18 - 3 = 15 uT
T4: 11 - 5 = 6 uT
T5: 15 - 7 = 8 uT

Waiting time (tempo total esperando na fila):
T1: 18 - 3 = 15 uT
T2: 20 uT
T3: 15 - 5 = 10 uT
T4:  0 uT
T5: 11 - 7 = 4 uT
**(f) RR com tq = 2, sem envelhecimento**
a.![[Pasted image 20250616170956.png]]
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1: 17 uT
T2: 6 uT
T3: 22 - 3 = 19 uT
T4: 24 - 5 = 19 uT
T5: 21 - 7 = 14 uT

Waiting time (tempo total esperando na fila):
Desta vez, irei usar o tempo de turnaround menos o tempo de execução total.
T1: 17 - 5 = 12 uT
T2: 6 - 4 = 2 uT
T3: 19 - 5 = 14 uT
T4:  19 - 6 = 13 uT
T5: 14 - 4 = 10 uT

b.
![[Pasted image 20250616172058.png]]
Turnaround time (calculado pelo tempo de chegada até o encerramento da tarefa):
T1: 17 uT
T2: 14 uT
T3: 6 - 1 = 5 uT
T4: 23 - 7 = 16 uT
T5: 21 - 9 = 12 uT

Waiting time (tempo total esperando na fila):
Desta vez, irei usar o tempo de turnaround menos o tempo de execução total.
T1: 17 - 5 = 12 uT
T2: 14 - 6 = 8 uT
T3: 5 - 2 = 4 uT
T4:  16 - 6 = 10 uT
T5: 12 - 4 = 8 uT

Considerações: todas as tarefas são orientadas a processamento; as trocas de contexto têm duração nula; em eventuais empates (idade, prioridade, duração, etc), valores maiores de prioridade indicam maior prioridade.3
## Capítulo 14:
1. **Explique a diferença entre endereços lógicos e endereços físicos e as razões que justificam o uso de endereços lógicos.**

_Endereços físicos mapeiam todo o espaço físico da memória principal, correspondendo aos bytes diretos na memória, e os endereços lógicos mapeiam uma parte da memória onde um programa foi alocado, estes que então são traduzidos para endereços físicos quando referenciados. Os endereços lógicos melhoram o desempenho e desenvolvimento de programas, deixam o sistema mais seguro._

2. **O que é uma MMU – Memory Management Unit?**

_A MMU é um componente de hardware, geralmente integrada a CPU, que gerência referências a memória principal e traduz endereços virtuais para físicos. Para melhorar o desempenho de busca de páginas, a MMU implementa seu próprio cache, a TLB (Translation Lookaside Buffer)._

3. **Seria possível e/ou viável implementar as conversões de endereços realizadas pela MMU em software, ao invés de usar um hardware dedicado? Por que?**
_Sim seria possível, isso ocorre em maquinas virtuais, porém, não é recomendado. Um componente em hardware garante maior performance do sistema e segurança, pois se um componente do software falhar o sistema todo pode ficar comprometido._

4. **Explique as principais formas de alocação de memória.**

_Temos a alocação contiguá simples, em que a memória é dividida entre SO e programas do usuário, e permite somente um programa rodando na memória por vez.
Particionada estática, onde a memória é particionada em espaços de tamanhos fixos que são definidos na inicialização do sistema, sendo necessário a reinicialização do mesmo para mudar os tamanhos da partição. Nessa estratégia temos duas técnicas, tamanhos fixos onde todas as partições tem o mesmo tamanho e tamanho variável, onde partições podem ter tamanhos diferentes.
Particionada dinâmica, onde quando um processo é trazido da memória, o sistema aloca um tamanho que o comporta. Este é o único caso onde ocorre fragmentação externa diferente dos outros._

5. **Por que os tamanhos de páginas e quadros são sempre potências de 2?**

_Pois isso simplifica o trabalho da MMU, em traduzir endereços e a deixa mais eficiente pois as operações são feitas bit a bit._

6. **Considerando a tabela de segmentos a seguir (com valores em decimal), calcule os endereços físicos correspondentes aos endereços lógicos 0:45, 1:100, 2:90, 3:1.900 e 4:200.**

| Segmento | 0   | 1   | 2    | 3    | 4    |
| -------- | --- | --- | ---- | ---- | ---- |
| Base     | 44  | 200 | 0    | 2000 | 1200 |
| Limite   | 810 | 200 | 1000 | 1000 | 410  |
8. **Considere um sistema com endereços físicos e lógicos de 32 bits, que usa tabelas de páginas com três níveis. Cada nível de tabela de páginas usa 7 bits do endereço lógico, sendo os restantes usados para o offset. Cada entrada das tabelas de páginas ocupa 32 bits. Calcule, indicando seu raciocínio:**
(a) O tamanho das páginas e quadros, em bytes.
(b) O tamanho máximo de memória que um processo pode ter, em bytes e
páginas.
(c) O espaço ocupado pela tabela de páginas para um processo com apenas uma
página de código, uma página de dados e uma página de pilha. As páginas
de código e de dados se encontram no inicio do espaço de endereçamento
lógico, enquanto a pilha se encontra no final do mesmo.
(d) Idem, caso todas as páginas do processo estejam mapeadas na memória.

9. **Explique o que é TLB, qual a sua finalidade e como é seu funcionamento**
	_A TLB é a cache do MMU, onde ele armazena os endereços das páginas usadas recentemente, sem precisarmos acessar a memória principal, entregando maior desempenho ao sistema. Se uma referencia não estiver na TLB, ela pode estar na tabela de páginas, e se não estiver então será gerado um page-fault._

10. **Sobre as afirmações a seguir, relativas á alocação por páginas, indique quais são incorretas, justificando sua resposta:**
	a) Um endereço lógico com N bits é dividido em P bits para o número de página e N - P bits para o deslocamento em cada página.
	_Correto._
	b) As tabelas de páginas multiníveis permitem mais rapidez na conversão de endereços lógicos em físicos.
	_O uso de tabelas multinível não permitem mais rapidez, porém reduzem o espaço ocupado na memória principal._
	c) O bit de referência R associado a cada página é "ligado" pela MMU sempre que a página é acessada.
	_Correto._
	d) O cache TLB é usado para manter páginas frequentemente usadas na memória.
	_Correto._
	e) O bit de modificação M associada a cada página é "ligado" pelo núcleo sempre que um processo modificar o conteúdo da mesma.
	_Ligado pela MMU._
	f) O cache TLB deve ser esvaziado a cada troca de contexto entre processos.
	_O TLB geralmente precisa ser esvaziado para garantir a correção das traduções para o novo processo, a menos que o hardware forneça suporte para identificadores de espaço de endereço (ASIDs)._
	
## Capitulo 16
1. **Explique o que é fragmentação externa. Quais formas de alocação de memória estão livres desse problema?**
	_A fragmentação externa ocorre quando há lacunas entre espaços ocupados na memória, se essas lacunas forem pequenas o espaço da efetivo da memória é reduzido. Alocações encadeadas e indexadas (para arquivos) não sofrem desse fenômeno, pois os blocos não precisam estar contíguos. Para virtualização de memória, a paginação não sofre desse fenômeno pois ela divide toda a memória em blocos de tamanhos fixos._
2. **Explique o que é fragmentação interna. Quais formas de alocação de memória estão livres desse problema?**
	_A fragmentação interna ocorre quando há espaços livres dentro de espaços ocupados para processos. Alocação contiguá (para arquivos) não sofre desse fenômeno. Segmentação, no contexto de memória virtual, não sofre de fragmentação interna, pois cada segmento tem tamanho necessário para cada parte do processo._
