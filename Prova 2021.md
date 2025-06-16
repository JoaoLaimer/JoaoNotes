1. **Qual a vantagem de termos tamanhos diferentes para o quantum de tempo em níveis distintos de um sistema de enfileiramento multinível?**

_Podemos usar diferentes quantums para cada caso, numa fila de processos interativos podemos ter um quantum menor para aumentar a responsividade do processo e em uma fila de processos em batch o quantum pode ser maior, pois só estamos interessados na resposta final e aumentando a performance dos mesmos._

2. **Cite vantagens e desvantagens de três arquiteturas utilizadas para a organização de Sistemas Operacionais.**

_Sistemas Monoliticos:_
	_Vantagens: Melhor desempenho._
	_Desvantagens: Menor robustez e custo elevado de manutenção._
_Sistemas Microkernel:_
	_Vantagens: Maior robustez, modularidade e flexibilidade._
	_Desvantagens: Menos desempenho._
_Sistemas Híbridos:_
	_Vantagens:_ Incorporam aliar as boas propriedades dos sistemas monolíticos e microkernel.
	Desvantagens: Maior complexidade de concepção e implementação.

3. **Descreva como o PCB é utilizado pelo Sistema Operacional? Além disso, como o PCB poderia ser utilizado para prevenir o Deadlock?**

_O PCB armazena as informações de contexto de um processo, sendo seus recursos utilizados, identificadores, estados, espaço de endereçamento entre outros. Com as informações que o PCB possui, podemos atacar uma das 4 condições para a ocorrência do deadlock, por exemplo, a não-preempção: podemos acessar quais recursos um processo esta mantendo e assim identificar o deadlock e "arrancar" esse recurso do processo, salvando seu processo anteriormente e restaurando-o após._

4. **Como o escalonamento por prioridade pode levar ao problema da inanição (dê um exemplo e explique)? Cite uma forma de resolver.**

_O escalonamento por prioridade leva a inanição quando um processo de menor prioridade está em um conjunto de tarefas de prioridades maiores, causando a inanição. Para resolver esse problema, podemos implementar um mecanismo de "agging", onde as tarefas na fila ganham maior prioridade conforme o tempo que ela passa na fila._

5. **Muitos algoritmos de scheduling da CPU são parametrizados. Por exemplo, o algoritmo RR requer um parâmetro que indique a parcela de tempo. Filas multiníveis com retroalimentação requerem parâmetros que definam o número de filas, o algoritmo de scheduling para cada fila, os critérios usados para mover processos entre as filas, e assim por diante.
	Portanto, na verdade, esses algoritmos são conjuntos de algoritmos (por exemplo, o conjunto de algoritmos RR para todas as parcelas de tempo etc.). Um conjunto de algoritmos pode incluir outro (por exemplo, o algoritmo FCFS é o algoritmo RR com um quantum de tempo infinito). Que relação existe, se existir alguma (configuração de parâmetro, situação, caso especifico, ...) entre os conjuntos de pares de algoritmos a seguir?**
**a) Shortest Job Next (SJN) e Shortest Remaining Time First (SRTF)**
_O algoritmo SRTF é a versão preemptiva do algoritmo SJF._
**b) Por prioridades e FCFS(First-Came, First-Served)**
_O algoritmo por prioridades pode virar o algoritmo FCFS se a prioridade definida for o momento da chegada da tarefa, ou seja, o mais recente tem mais prioridade._

6. **Analise o programa abaixo que é composto por dois processos que executam as seguintes funções:**
```C
P1 () {
	shared int x;
	x = 10;
	while (1) {
		x = x - 1;
		x = x + 1;
		if (x != 10)
			printf("x is $d", x);
	}
}

P2 () {
	shared int x;
	x = 10;
	while (1) {
		x = x - 1;
		x = x + 1;
		if (x != 10)
			printf("x is %d", x);
	}
}
```

**a) O programa acima pode imprimir o valor de x igual a 10? Se sim, mostre uma sequência de execução que produza este resultado.**

_Sim o programa pode imprimir o valor x igual a 10. Uma sequência de execução que produziria este resultado, seria se o processo P2 estivesse 2 instruções a frente do P1._
``` C
P2: x = x - 1; (x = 9)
P1: while (1)
P2: x = x + 1; (x = 10)
P1: x = x - 1; (x = 9)
P2: if (x != 10) (True)
P1: x = x + 1; (x = 10)
P2: printf("x is %d", x); -> "x is 10"
```

**b) Se a sua resposta para a letra a da questão for igual a Sim, apresente uma solução para o problema.**

_Podemos alterar o código adicionando um mutex e inserindo a area critica no momento de verificar o condicional._
``` C
P2 () {
	shared int x;
	x = 10;
	while (1) {
		pthread_mutex_lock(&mutexlock);
		x = x - 1;
		x = x + 1;
		if (x != 10)
			printf("x is %d", x);
		pthread_mutex_unlock(&mutexlock);
	}
}
```
_Mesmo procedimento para o outro processo._

7. **Sobre deadlocks:**
**a) Cite as condições necessárias para um Deadlock.**

_Existem 4 condições que devem ser alcançadas para o deadlock: Exclusão Mutua, Resource Holding, Espera Circular e Não-Preempção._

**b) É correto afirmar que se um grafo de alocação de recurso usado na detecção de deadlocks possui um ciclo, necessariamente, um deadlock ocorre? Explique e mostre através de um exemplo sua resposta.**

_Não podemos afirmar que um deadlock irá ocorrer toda vez que um grafo possuir um ciclo. Um exemplo, é um grafo que possui um ciclo entre dois processos e e recursos, porém existem, dois recursos de cada para os processos no ciclo._
![[Pasted image 20250616120513.png]]

**c) Podemos dizer então que se o grafo possui um ciclo e existe apenas uma instância de cada recurso, necessariamente temos um deadlock? Explique e mostre através de um exemplo sua resposta.**

_Sim, podemos afirmar, contanto que as 4 condições ainda estejam presentes. No grafo apresentado anteriormente se R1 e R2 tivessem somente uma instância de recurso, eventualmente isso iria causar um deadlock, devido a espera circular entre P1 e P3, onde P1 espera P3 liberar seu recurso e P3 espera P1 liberar seu recurso também._

8. **Quando existem várias cópias de vários recursos em um sistema computacional, é necessária a adoção de uma abordagem que utiliza vetores e matrizes para a detecção de deadlocks. Considerando E o vetor de recursos existentes, D o vetor de recursos disponíveis, C a matriz de alocação corrente dos processos e R a matriz de requisições, responda:**

**a) Se existir cinco processos sendo executados, quantas linhas terão as matrizes C e R**

_Se cinco processos estão sendo executados cada matriz conterá cinco linhas, uma para cada processo._

**b) Em que situação o vetor E é igual ao vetor D?**

_Quando todos os recursos tiverem sido utilizados e processos finalizados, assim teremos todos os recursos existentes disponíveis._

**c) O que estará acontecendo se a primeira linha da matriz C e a primeira linha da matriz R estiverem zeradas?**

_O processo não necessita de nenhum recurso e assim nenhum recurso esta alocado para o processo que representa a primeira linha._

**d) Respondendo em função dos valores das matrizes e dos vetores, em que situação o sistema detectaria um deadlock?**

_Quando o vetor D não consegue atender processos da matriz R pois a recursos já alocados estão sendo segurados por processos na matriz C, impedindo a execução dos processos._
