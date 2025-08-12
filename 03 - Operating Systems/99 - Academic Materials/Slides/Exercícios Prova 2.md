# Lista - Gerência de Memória
1. **O que é a gerência de memória e para que serve? Descreva os requisitos que devem ser satisfeitos.**
	_A gerência de memória é o controle das partes da memória que estão em uso e das partes que não estão. A gerência controla quando alocar memória e quando liberar dependendo da necessidade do sistema. Para que o gerenciamento seja efetivo, devemos satisfazer os seguintes requisitos: 
	- _Realocação: O sistema deve conseguir traduzir as referencias a memória no programa para memoria física, ou seja, se necessário, o sistema deve conseguir referenciar a memória mesmo realocada em outra posição._
	- _Proteção: Processos não podem referenciar outras areas de memória sem permissão, todas areas devem ser checadas durante execução. A MMU (Unidade de Gerencia de Memoria) é o componente hardware responsável por interceptar acessos indevidos._
	- _Compartilhamento: Um mecanismo de proteção deve ser flexível e permitir que vários processos compartilhem a mesma area de memoria, como o compartilhamento de bibliotecas, onde uma biblioteca é carregada para mais de um processo, economizando memória RAM._ 
	- _Organização Lógica: Programas são separados em módulos de memória que são escritos e compilados independentemente e referencias de um modulo para outro podem ser resolvidos em tempo de execução. Com isso, também, diferentes níveis de proteção podem ser implementados e módulos podem ser compartilhados._
	- Organização Física: O gerenciados deve ser capaz de alocar e desalocar blocos de memória física e gerenciar a hierarquia de memória.
2. **Descreva a alocação contígua simples.**
	_Na alocação contígua simples, a memória é dividida em duas partes, uma para o SO e outra para o espaço do usuário. Nessa arquitetura somente um programa pode estar na memória a qualquer momento, se um programa não utilizar toda a memória, o restante permanecerá inutilizado, fenômeno conhecido como fragmentação interna. Para programas maiores que a memória, era utilizado a técnica do overlay._
3. **Descreva e exemplifique o uso de Overlay.**
	A técnica do overlay (superposição) foi criada para resolver o problema da memória de alocação contígua simples, em que programas eram maiores que a memória disponível, a técnica consiste em dividir um programa em módulos carregáveis para que sejam carregados na memoria em diferentes momentos. Exemplificando, supondo um programa com as funções de cadastro, impressão de dados e processamento dos dados, podemos dividir cada função em módulos, e cada modulo é carregado separadamente junto com um modulo principal. A utilização da técnica exige cuidado na transferência de módulos e também essa solução era trabalhosa e complexa para o programador.
4. **Descreva resumidamente a alocação particionada estática.**
	 _A memória era dividida em unidades de tamanho fixo chamadas partições que eram definidas na inicialização do sistema, e se necessário a mudança do tamanho, o sistema deve ser reinicializado. A alocação particionada estática possui dois tipos: de tamanho fixo, onde todas as partições tem o mesmo tamanho, assim, somente programas menores que a partição conseguem ser carregados nela. E, de tamanho variável, onde partições tem tamanhos diferentes, assim, programas podem maiores podem ficar nas partições maiores e programas menores nas partições menores. A sua maior desvantagem é a fragmentação interna pois pode ocorrer desperdício na utilização de uma partição._
5. **Considere a alocação particionada estática e apresente as vantagens e desvantagens de utilizar partições de tamanhos idênticos e de tamanhos distintos.**
	 _Em partições de tamanho idêntico, essa técnica é mais simples de implementar e processos menores podem ocupar qualquer partição disponível, porém, se um programa for maior que a partição deve se usar o overlay e se um programa for muito pequeno ele ainda utilizara uma partição inteira._ 
	 _Em partições de tamanho distintos, podemos alocar programas nas menores partições que o comportem reduzindo a fragmentação interna, porém temos que usar uma estratégia para a escolha da partição, usando filas de processos para cada partição, que pode gerar filas cheias e filas ociosas e fila unica que aumenta a ocorrência de fragmentação interna, pois coloca programas em qualquer partição disponível._  
6. **Descreva resumidamente a alocação particionada dinâmica.**
	 _Quando um processo é trazido para a memória, sera alocado um espaço de memória que ele precisar. Porém quando um programa termina, ele deixa seu espaço na memória, assim, quanto mais programas de diferentes tamanhos são alocados e desalocados, ocorre a fragmentação externa, onde pequenos espaços inutilizados não contíguos são deixados entre os programas. Uma solução é compactar a memória de tempos em tempos. A alocação particionada dinâmica também comporta programas de tamanho variável, onde se o programa crescer pode se escolher varias estrategias para o comportar, e se não for possível o programa deve esperar ou é terminado._
7. **Cite e descreva as estratégias para Escolha da Partição.**
	_First Fit: escolhe o primeiro block livre com tamanho suficiente para caber o programa. Algoritmo simples de implementar. A free list é ordenada por endereços._
	_Best Fit: escolhe a partição com menor tamanho que comporte o programa. Há tendencia de fragmentação externa. Algoritmo complexo._
	_Worst Fit: escolhe a maior partição possível que comporte o programa. A ideia é deixar espaços maiores entre programas reduzindo a fragmentação._
	_Quick Fit: Mantem uma lista de blocos mais utilizados por tamanho. Quando um processo termina devemos atualizar a lista para não fragmentar a memória._
8. **Descreva como gerenciar as áreas livres da memória?**
	_Podemos usar a estrategia do Bitmap, onde a memória é dividia em unidades, quanto menor a unidade maior sera o bitmap. Nessa estratégia, uma string de bits, representa se um espaço da memoria esta sendo utilizado ou não. Se a unidade ser muito grande, o mapa sera menor, porém, memoria é desperdiçada na ultima unidade de alocação._
	_Outra estratégia é usar listas encadeadas, onde cada elemento representa um fragmento de memória livre ou alocada, em ordem crescente. Cada elemento possui: uma flag de livre/alocada, o primeiro endereço do fragmento, o tamanho, e o endereço do próximo fragmento._
9. **O que é swapping e qual seu funcionamento?**
	_Quando programas não podem ser executados pois falta espaço na memória, eles estão esperando o swapping. Esse processo ocorre quando um programa que esta na memória principal é movido para a memória secundaria (swap out) e quando ele é escalonado para execução ele é movido para a memória principal novamente como se nada tivesse acontecido (swap in). Utilizando um registrador de realocação, podemos guardar o endereço inicial da região da região da memoria onde o programa sera alocado, quando há uma refeceria a um endereço seu valor é somado com o valor do registrador. Porém, um_
10. **Descreva com suas próprias palavras a Memória Virtual e evidencie a sua importância.**
	_Memória Virtual é uma técnica sofisticada de gerenciamento de memória. Essa técnica combina memória principal e secundária, dando a impressão de uma memória maior que a memória principal. Essa técnica é importante pois, melhora o referenciamento de endereços e também podemos utilizar um programa maior que a memória principal em que parte dele reside na memoria primaria e outra parte na secundaria._
	_Essa técnica permite melhor abstração e facilidade de programação e proteção e isolamento entre processos, pois cada processo possui seu próprio espaço de endereçamento virtual._
11. **O que é o espaço de endereçamento virtual?**
	_O espaço de endereçamento virtual é o espaço virtual criado para o processo pelo SO, onde as referencias de endereços que o processo faz, condizem com os endereços virtuais, que depois são traduzidos para endereços físicos, assim permitindo que o programa referencie endereços fora dos limites físicos da memoria principal, dando a impressão de espaço de memoria privado, continuo e maior._ 
12. **O que é e como funciona o mapeamento em relação a memória virtual?**
	 _O mapeamento é a tradução de endereços virtuais para endereços físicos. Ela é feita pela MMU (Unidade de Gerenciamento de Memoria), a MMU ativa quando há uma referência a um endereço virtual. O mecanismo de tradução mantem uma tabela de mapeamento exclusiva para cada processo. O sistema deve referenciar a tabela de mapeamento durante a execução do processo. Essa tabela é usada para mapear blocos de dados, onde o tamanho do bloco define o número de entradas na tabela de mapeamento._
# Exercícios Slide Gerência de Memória

1. **Considere um sistema computacional com 40 Kb de memória principal e que utilize um sistema operacional de 10 Kb que implemente alocação contígua de memória. Qual a taxa de subutilização da memória principal para um programa que ocupe 20 Kb de memória?**
	 MP = 40Kb
	 MP + SO = 30Kb
	 MP + SO + Programa = 10Kb
	 Taxa de subutilização = 10/40 = 0.25
	_Considerando que o sistema operacional e o programa somados ocupam 3/4 da memória principal, temos  25% de subutilização de memória._
2. **Suponha um sistema computacional com 64 Kb de memória principal e que utilize um sistema operacional de 14 Kb que implemente alocação contígua de memória. Considere também um programa de 80 Kb, formado por um módulo principal de 20 Kb e três módulos independentes, cada um com 10 Kb, 20 Kb e 30 Kb. Como o programa poderia ser executado utilizando se apenas a técnica de overlay?**
	MP = 64 Kb
	MP + SO = 64 + (- 14) = 50 Kb
	MP + SO + Prog(Modulo principal) = 50 + (- 20) = 30 Kb
	_Com 30 Kb sobrando para os módulo, podemos usá-los usando overlay._
3. **Considerando o exercício anterior, se o módulo de 30 Kb tivesse seu tamanho aumentado para 40 Kb, seria possível executar o programa? Caso não seja possível, como o problema poderia ser contornado?**
	 _Não seria possível executar o programa, somente se pudêssemos modularizar o modulo de 40 Kb para cada parte poder caber nos 30 Kb que sobraram para os módulos._
4. **Considere que os processos da tabela a seguir estão aguardando para serem executados e que cada um permanecerá na memória durante o tempo especificado.**
	**O sistema operacional ocupa uma área de 20 Kb no início da memória e gerencia a memória utilizando um algoritmo de particionamento dinâmico modificado.**
	**A memória total disponível no sistema é de 64 Kb e é alocada em blocos múltiplos de 4 Kb. Os processos são alocados de acordo com sua identificação (em ordem crescente), e irão aguardar até obter a memória de que necessitam.**
	**Calcule a perda de memória por fragmentação interna e externa sempre que um processo é colocado ou retirado da memória. O sistema operacional compacta a memória apenas quanto existem duas ou mais partições livres adjacentes.**

| Processos | Memória | Tempo |
| --------- | ------- | ----- |
| 1         | 30Kb    | 5     |
| 2         | 6Kb     | 10    |
| 3         | 36Kb    | 5     |
_No instante inicial temos:_

| Processo            | Memória           |
| ------------------- | ----------------- |
| SO                  | 20Kb              |
| Partição Processo 1 | 32Kb (30kb Uteis) |
| Partição Processo 2 | 8Kb (6Kb Uteis)   |
| Area Livre          | 4Kb               |
_Fragmentação interna nos processos 1 e 2, sendo 2Kb de fragmentação para os dois processos._
_Não há fragmentação externa._
_No instante de tempo 5, o processo 1 termina sua execução:_

| Processo        | Memória         |
| --------------- | --------------- |
| SO              | 20Kb            |
| Área Livre      | 32Kb            |
| Part Processo 2 | 8Kb (6Kb Uteis) |
| Área Livre      | 4Kb             |
_Fragmentação interna no processo 2, de 2 Kb e fragmentação externa de 36 Kb._
_No instante de tempo 10, o processo 2 termina sua execução:_

| Processo            | Memória |
| ------------------- | ------- |
| SO                  | 20Kb    |
| Partição Processo 3 | 36Kb    |
| Área Livre          | 8Kb     |
_Nesse estado o sistema não tem nenhum tipo de fragmentação._
# Lista - Gerência de Memória - Paginação
1. **Quais os benefícios oferecidos pela técnica de memória virtual? Como este conceito permite que um programa e seus dados ultrapassem os limites da memória principal?**
2. Explique como um endereço virtual de um processo é traduzido para um endereço real na memória principal?
3. Por que o mapeamento deve ser feito em blocos e não sobre células individuais? Apresente um exemplo numérico.
4. Para que serve o bit de validade nas tabelas de páginas?
5. O que é um page fault, quando ocorre e quem controla a sua ocorrência? Como uma elevada taxa de page fault pode comprometer o sistema operacional?
6. Descreva como ocorre a fragmentação interna em um sistema que implementa paginação.
7. Descreva as vantagens e desvantagens de paginação por demanda e antecipada.
8. Quais vantagens e desvantagens da política de alocação de páginas variável comparada à alocação fixa.
9. Um sistema com gerência de memória virtual por paginação possui tamanho de página com 512 posições, espaço de endereçamento virtual com 512 páginas endereçadas de 0 a 511 e memória real com 10 páginas numeradas de 0 a 9. O conteúdo atual da memória real contém apenas informações de um único processo e é descrito resumidamente na seguinte tabela:

| Endereço Físico | Conteúdo          |
| --------------- | ----------------- |
| 1536            | Página Virtual 34 |
| 2048            | Página Virtual 09 |
| 3072            | Tabela de Páginas |
| 3584            | Página Virtual 65 |
| 4608            | Página Virtual 10 |
	**a.** Considere que a entrada da tabela de páginas contém, além do endereço do frame, o número da página virtual. Mostre o conteúdo da tabela de páginas deste processo.
	**b.** Mostre o conteúdo da tabela de páginas após a página virtual 49 ser carregada na memória a partir do endereço real 0 e a página virtual 34 ser substituída pela página virtual 12.
	**c.** Como é o formato do endereço virtual deste sistema?
	**d.** Qual endereço físico está associado ao endereço virtual 4613?
10. **Um sistema operacional implementa gerência de memória virtual por paginação, com frames de 2 Kb. A partir da tabela que se segue, que representa o mapeamento de páginas de um processo em um determinado instante de tempo, responda:**

| Página | Residente | Frame |
| ------ | --------- | ----- |
| 0      | Sim       | 20    |
| 1      | Sim       | 40    |
| 2      | Sim       | 100   |
| 3      | Sim       | 10    |
| 4      | Não       | 50    |
| 5      | Não       | 70    |
| 6      | Sim       | 1000  |
	**a.** Qual o endereço físico de uma variável que ocupa o último byte da página 3?
	**b.** Qual o endereço físico de uma variável que ocupa o primeiro byte da página 2?
	**c.** Qual o endereço físico de uma variável que tem deslocamento 10 na página 3?
	**d.** Quais páginas do processo estão na memória?
11. **Para que serve o bit de modificação nas tabelas de páginas?**
12. **Considere um sistema com memória virtual por paginação com endereço virtual com 24 bit se página com 2048 endereços. Na tabela de páginas a seguir, de um processo em determinado instante de tempo, o bit de validade 1 indica página na memória principal e o bit de modificação 1 indica que a página sofreu alteração.**

| Página | BV  | BM  | End. do Frame |
| ------ | --- | --- | ------------- |
| 0      | 1   | 1   | 30.720        |
| 1      | 1   | 0   | 0             |
| 2      | 1   | 1   | 10.240        |
| 3      | 0   | 0   | *             |
| 4      | 0   | 0   | *             |
| 5      | 1   | 0   | 6.144         |
	**a.** Quantos bits possui o campo deslocamento do endereço virtual?
	**b.** Qual o número máximo de entradas que a tabela de páginas pode ter?
	**c.** Qual o endereço físico que ocupa o último endereço da página 2?
	**d.** Caso ocorra um page fault e uma das páginas do processo deva ser descartada, quais páginas poderiam sofrer page out?
13. **Considere um sistema de memória virtual que implemente paginação no qual o limite de frames por processo é igual a três. Descreva para os itens a seguir, para os quais é apresentada uma sequência de referências a páginas pelo processo, o número total de page faults para as estratégias de realocação de páginas FIFO e LRU. Indique qual a mais eficaz para cada item.**
	**a.** 1 / 2 / 3 / 1 / 4 / 2 / 5 / 3 / 4 / 3
	**b.** 1 / 2 / 3 / 1 / 4 / 1 / 3 / 2 / 3 / 3