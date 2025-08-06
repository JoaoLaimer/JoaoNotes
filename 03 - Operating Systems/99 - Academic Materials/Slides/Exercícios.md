## Lista 1
1. **Quais são as três principais finalidades de um sistema operacional?**

_Abstrair o uso de dispositivos, gerenciar dispositivos e criar um ambiente seguro para execução de programas._

2. **Por que a abstração de recursos é importante para os desenvolvedores de aplicações? Ela tem alguma utilidade para os desenvolvedores do próprio sistema operacional?**

_O acesso e gerenciamento dos recursos é abstraído pois seria difícil desenvolver e custaria muito tempo, se não fosse. Essa abstração auxilia que desenvolvedores tenham um acesso mais facilitado ao dispositivo, apresentando interfaces e ferramentas._

3. **O que caracteriza um sistema operacional de tempo real?**

_Um sistema operacional de tempo real, é projetado para cumprir prazos e ter um comportamento de execução previsível._

4. **O que diferencia o núcleo (kernel) do restante do sistema operacional?**

_O kernel é uma estrutura do SO que é responsável pelo acesso ao hardware e pelo gerenciamento do mesmo, ele possui o maior nível de permissões sendo necessário passar para o kernel as atividades que envolvem acesso a estes recursos. Além disso, o kernel pode possuir responsabilidades adicionais dependendo da arquitetura do SO._

5. **Para permitir diferenciar os privilégios de execução dos diferentes tipos de software, os processadores modernos implementam níveis de privilégio de execução. Quais são eles?**

_Os níveis de privilégios mais básicos são: kernel/administrador e usuário/aplicação.
O nível do kernel é responsável pelo acesso de dispositivos e a gerencia dele, entregando abstrações para esse acesso, possui acesso a todas as instruções do sistema.
O nível do usuário é responsável por tarefas básicas do SO, e possuem um conjunto restrito de instruções que é possível.

6. **Seria possível construir um sistema operacional seguro usando um processador que não tenha níveis de privilégio? Por quê?**

_Não seria possível, pois o acesso a todas instruções do processador sem delegar privilégios, pode causar problemas com segurança e estabilidade do sistema._

7. **O comando em linguagem C fopen é uma chamada de sistema ou uma função de biblioteca? Por quê?**

_O comando fopen é uma função de biblioteca, que é usada para abstrair a chamada de sistema, open()._

8. **Quais vantagens e desvantagens dos sistemas monolíticos? E dos Sistemas em Camadas?**

_A vantagem dos sistemas monolíticos é seu desempenho já que seus componentes são intimamente interconectados, porém, isso causa um problema na robustez do sistema, já que se um componente falhar, o erro irá se propagar pelo sistema rapidamente, essa é sua principal desvantagem._

_O sistema de camadas possui uma maior granularidade e segurança onde cada camada é delegada um conjunto de privilégios, onde camadas mais próximas do hardware possuem maiores privilégios. Porém o seu desempenho é comprometido, pois para um dispositivo ser acessado, o processo deve passar por todas as camadas._

9. **Quais as diferenças entre interrupções e exceções em SO?**

_Interrupções são geradas por um dispositivo para tratar um evento interno. Uma exceção é gerada pelo próprio processador quando o mesmo tenta executar alguma instrução ilegal, como divisão por zero._

10. **A figura abaixo detalha o funcionamento básico da chamada de sistema write, que escreve dados em um arquivo previamente aberto. Descreva brevemente cada etapa.**

_1. No nível usuário, a aplicação chama a função write() da biblioteca do sistema._
_2. A função preenche os registradores da CPU com os parâmetros recebidos._
_3. A função write invoca uma chamada de sistema._
_4. O processador entra para nível kernel e transfere o controle para a rotina de entry._
_5. A rotina entry chama pela tabela de syscall a função desejada (sys_write())._
_6. A função sys_write() obtém os parâmetros e efetua a operação._
_7. Os resultados são retornados para função da biblioteca._
_8. Os resultados do write() voltam para a o fluxo da aplicação._
_9. Caso a operação não possa ser concluída imediatamente, sys_write passa o controle para gerencia de tarefas. Acontece quando se espera uma entrada de dispositivo._
_10. A gestão de tarefas suspende a execução da aplicação e devolve o controle do processador a alguma outra aplicação._


11. **Descreva em oito linhas, uma linha para cada uma das oito etapas do processo de uma aplicação ler dados de um arquivo, no sistema Minix 3, em Sistemas Micronúcleo.**

_A aplicação manda uma mensagem ao servidor de arquivos, solicitando uma leitura.
O servidor de arquivos manda uma mensagem ao driver do disco solicitando a leitura dos dados.
O driver envia uma mensagem ao núcleo solicitando operações de I/O do disco.
O núcleo verifica se o driver tem permissão para o uso das portas e agenda a operação.
O núcleo transfere os dados lidos para a memória do driver.
O driver solicita uma cópia dos dados ao núcleo para o servidor de arquivos.
O servidor de arquivos solicita ao núcleo a cópia dos dados recebidos para a aplicação.
A aplicação recebe a resposta da solicitação e usa os dados lidos.

12. **Além das arquiteturas clássicas (monolítica, em camadas, micronúcleo), recentemente surgiram várias propostas para organizar os componentes do sistema operacional. Descreva as diferenças de Máquinas Virtuais e Contêineres**

_Uma maquina virtual é uma camada de software que transforma um sistema operacional em outro, utilizando os recursos de um (host) para construir o outro sistema (guest).
Um container é um tipo de maquina virtual, que simula um espaço de usuário isolada do resto do sistema, com suas próprias interfaces de rede e processos. Um processo em um container não consegue interagir com um processo externo._

15. **O que significa “trocas de contexto”? Dê um exemplo com todos os passos envolvidos.**

_A troca de contexto acontece quando há a alteração da tarefa em execução no momento. Com isso, é necessário que se salve o contexto de uma tarefa para que ele possa ser restaurada novamente em um momento posterior. Para a troca de contexto: é necessário uma tarefa estar executando, uma interrupção do temporizador do hardware ocorre, o despachante é ativado e ele salvo o estado da tarefa em execução em seu TCP, o despachante então resgata o estado da próxima tarefa e a reativa._

## Lista 5:
1. **Considere uma aplicação que utilize uma matriz na memória principal para a comunicação entre vários processos concorrentes. Que tipo de problema pode ocorrer quando dois ou mais processos acessam uma mesma posição da matriz?**

_O problema que pode ocorrer se chama "corrida", onde se dois processos acessam um mesmo valor simultaneamente, a operação que ocorrer por último será a que vai valer, ou seja, ao invés de duas operações serem realizadas no valor, será como apenas uma operação ocorreu._

2. **O que é exclusão mútua e como é implementada?**

_É um mecanismo que garante que somente um processo possa acessar uma sessão critica a qualquer momento. Para implementa-la é necessário definir uma sessão critica e delimita-la, e então, criar variáveis bloqueantes que garantem que somente um processo acesse a sessão critica._

3. **Como seria possível resolver os problemas decorrentes do compartilhamento da matriz, apresentado anteriormente, utilizando o conceito de exclusão mútua?**

_Podemos colocar a matrix em uma sessão critica, para garantir a exclusão mutua, onde somente um processo poderá acessa-la por vez._

4. **O que é espera ocupada e qual o seu problema?**

_Espera ocupada ocorre quando uma tarefa ou processo testa continuamente uma condição, consumindo ciclos do processador enquanto aguarda uma condição o permitir avançar. Isso causa desperdício de ciclos do CPU e prejudica a performance do sistema._

5. **Sincronização condicional é uma situação onde o acesso ao recurso
compartilhado exige a sincronização de processos vinculada a uma condição de
acesso. Dado o conceito, forneça um exemplo de utilização.**

_O problema do produtor/consumidor, onde produtores geram recursos e depositam em buffers compartilhados e consumidores retiram esses itens do buffer para processa-los. Podemos implementar a exclusão mútua no acesso ao buffer, onde apenas um produtor ou consumidor pode acessar o buffer por vez._

6. **Explique o que é semáforo, apresente um problema que contenha região crítica crie uma solução com mutex e outra com semáforo.**

_O semáforo é um mecanismo de coordenação usado para garantir a exclusão mútua. Ele é visto como uma variável composta com um contador e uma fila de tarefas, podendo ser operado somente pelas funções P e V, onde P decrementa o contador do semáforo, Se o contador se tornar negativo, a tarefa solicitante é adicionada á fila do semáforo e suspensa. V incrementa o contador do semáforo. Se houver outras tarefas esperando n fila a primeira tarefa da file é acordada e retornada á fila de tarefas prontas para execução. Esta operação não é bloqueante para a tarefa que a executa._

7. **O que é deadlock, quais as condições para obtê-lo e quais as soluções possíveis?**

_Deadlock é um empasse, onde um grupo de tarefas bloqueiam umas as outras. Existem 4 condições para um deadlock acontecer: exclusão mutua, posse e espera, não-preempção e espera circular. Para se resolver um deadlock, precisamos que uma dessas condições seja evitada.
Para evitar a exclusão mutua: Usar a técnica de spooling, um processo que gerencia o acesso aos recursos, não sendo necessário obter acesso exclusivo.
Para evitar a posse e espera: Associar um prazo a solicitação de recursos, caso o prazo expire a tarefa tenta novamente ou desiste, liberando os recursos.
Para evitar a não-preempção: "arrancar" recurso sem que a tarefa o libere explicitamente, porém precisaríamos salvar o estado interno da tarefa e restaurado novamente.
Para evitar a espera circular: ordenar os recursos do sistema de acordo com uma ordem global única, forçando tarefas a solicitar recursos obedecendo a ordem._

8. **Em uma aplicação concorrente que controla saldo bancário em contas-correntes, dois processos compartilham uma região de memória onde estão armazenados os saldos dos clientes A e B. Os processos executam concorrentemente os seguintes passos:**
```
Processo 1 (Cliente A)

/* saque em A */
1a. x := saldo_do_cliente_A;
1b. x := x - 200;
1c. saldo_do_cliente_A := x;

/* deposito em B */
1d. x := saldo_do_cliente_B;
1e. x := x + 200;
1f. saldo_do_cliente_B := x;
```

```
Processo 2 (Cliente B)

/*saque em A */
2a. y := saldo_do_cliente_A;
2b. y := y - 100;
2c. saldo_do_cliente_A := y;

/* deposito em B */
2d. y := saldo_do_cliente_B;
2e. y := y + 100;
2f. saldo_do_cliente_B := y;
```

a. **Supondo que os valores dos saldos de A e B sejam, respectivamente, 500 e 900, antes de os processos executarem, pede-se: Quais os valores corretos esperados para os saldos dos clientes A e B após o término da execução dos processos.**

_O valor esperado seria: A = 200 e B = 1200_

b. **Quais os valores finais dos saldos dos clientes se a sequência temporal de execução das operações for: 1a, 2a, 1b, 2b, 1c, 2c, 1d, 2d, 1e, 2e, 1f, 2f?**

_A = 400 e B = 1000_

c. **Utilizando semáforos, proponha uma solução que garanta a integridade dos saldos e permita o maior compartilhamento possível dos recursos entre os processos, não esquecendo a especificação da inicialização dos semáforos.**

_Utilizando semáforos para cada cliente, podemos inicia-los antes de começar a execução e então a antes e depois de cada operação de saque e deposito, chamamos wait() e post() respectivamente, para cada cliente A e B.

```
Processo 1 (Cliente A)

wait(sem_A);
/* saque em A */
1a. x := saldo_do_cliente_A;
1b. x := x - 200;
1c. saldo_do_cliente_A := x;
post(sem_A);

wait(sem_B);
/* deposito em B */
1d. x := saldo_do_cliente_B;
1e. x := x + 200;
1f. saldo_do_cliente_B := x;
post(sem_B);
```

_Mesma coisa para o processo 2._

## Sistema de I/O
1. **Compare Disco Magnético e Disco de Estado Sólido.**

_Discos Magnéticos: Possui um braço que necessita ser posicionado no local certo para realizar leitura e escrita. O disco magnético possui um tempo de vida maior, são mais baratos e possuem maior capacidade, porém são lentos e possuem mais partes mecânicas fazendo eles mais suscetíveis a falhas.
Discos de Estado sólidos: Operam de com memória flash, onde um controlador SSD, que funciona como um pequeno processador gerencia leitura e escrita. O SSD é mais confiável pois não possui partes moveis, são mais rápidos, porém, são mais caros e possuem uma vida útil menor.

2. **O que é o bus PCI e qual problema de desempenho pode estar associado ao bus PCI?**

_É um barramento de I/O geral, por causa dessa natureza generalista eles são inerentemente mais lentos ao acesso direto á memória ou ao processador._

3.  **O que é o Polling?**

_É uma técnica para monitorar dispositivos de I/O, onde o processador (através do driver) monitora continuamente o status de um dispositivo para verificar se ele está pronto para uma operação ou se uma operação foi concluída. A técnica é ineficiente e desperdiça uma grande quantidade de tempo de CPU apenas aguardando a conclusão da atividade do dispositivo. O polling também adiciona uma enunciate pois se um evento acontecer logo apos uma verificação, o sistema terá que esperar quase todo o intervalo do polling para detecta-lo._

4. **Descreva sobre o DMA.**

_O DMA (Direct Memory Access), é um mecanismo de hardware que permite que um controlador DMA gerencie o fluxo de dados diretamente entre a memória principal e um dispositivo de E/S, sem intervenção da CPU._

4. **O que é escalonamento de I/O? Dê um exemplo.**

_escalonamento de I/O refere-se á ordem em que as requisições pendentes na fila de acesso a um dispositivo são atendidas._
4. Como a estrutura do sistema de I/O é organizada?