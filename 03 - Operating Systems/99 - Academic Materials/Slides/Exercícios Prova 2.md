# Lista - Gerência de Memória
1. **O que é a gerência de memória e para que serve? Descreva os requisitos que devem ser satisfeitos.**
	_A gerência de memória é o controle das partes da memória que estão em uso e das partes que não estão. A gerência controla quando alocar memória e quando liberar dependendo da necessidade do sistema. Para que o gerenciamento seja efetivo, devemos satisfazer os seguintes requisitos: 
	- _Realocação: O sistema deve conseguir traduzir as referencias a memória no programa para memoria física, ou seja, se necessário, o sistema deve conseguir referenciar a memória mesmo realocada em outra posição._
	- _Proteção: Processos não podem referenciar outras areas de memória sem permissão, todas areas devem ser checadas durante execução. A MMU (Unidade de Gerencia de Memoria) é o componente hardware responsável por interceptar acessos indevidos._
	- _Compartilhamento: Um mecanismo de proteção deve ser flexível e permitir que vários processos compartilhem a mesma area de memoria, como o compartilhamento de bibliotecas, onde uma biblioteca é carregada para mais de um processo, economizando memória RAM._ 
	- _Organização Lógica: Programas são separados em módulos de memória que são escritos e compilados independentemente e referencias de um modulo para outro podem ser resolvidos em tempo de execução. Com isso, também, diferentes níveis de proteção podem ser implementados e módulos podem ser compartilhados._
	- Organização Física: O gerenciador deve ser capaz de alocar e desalocar blocos de memória física e gerenciar a hierarquia de memória.
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
	_Quando programas não podem ser executados pois falta espaço na memória, eles estão esperando o swapping. Esse processo ocorre quando um programa que esta na memória principal é movido para a memória secundaria (swap out) e quando ele é escalonado para execução ele é movido para a memória principal novamente como se nada tivesse acontecido (swap in). Utilizando um registrador de realocação, podemos guardar o endereço inicial da região da memoria onde o programa sera alocado, quando há uma referencia a um endereço seu valor é somado com o valor do registrador. Porém, um_
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
	_A memória virtual é uma técnica que combina o tamanho da memória principal e secundaria dando a impressão de uma memória continua e maior. Ela utiliza endereços virtuais que são usados nos espaços de endereçamento de um programa, esse espaço que pode estar contido fisicamente em ambas memórias. Quando há referencia a um endereço virtual, a MMU traduz esse endereço para um endereço físico, se a informação estiver na memória secundária é realizado o chamado swap, em que esse informação é trazida para a memória primaria, assim, um programa pode ultrapassar os limites físicos dela. O espaço de endereçamento virtual também permite uma programação mais simples, abstraindo a necessidade de saber onde uma informação esta contida fisicamente._
2. **Explique como um endereço virtual de um processo é traduzido para um endereço real na memória principal?**
	_Um endereço virtual de um processo é traduzido para um endereço real pela MMU (Unidade de Gerenciamento de Memória), por meio do mapeamento. A MMU e mantém uma tabela de mapeamento que registra onde o espaço de endereçamento virtual de um processo está na memória física, permitindo a tradução.
	A memória virtual por paginação utiliza uma tabela de páginas para a tradução. A paginação é uma técnica baseada em dividir os espaços físicos e virtuais de endereçamento em blocos de tamanhos iguais, evitando o ajuste de tamanhos em uma memória de tamanho dinâmico. Quando um processo é executado, suas páginas (blocos virtuais) são carregadas para um frame (block físico) disponível. Cada processo tem sua tabela de paginas, onde a informação do mapeamento se encontra e permite o sistema a encontrar o local real da página._
3. **Por que o mapeamento deve ser feito em blocos e não sobre células individuais? Apresente um exemplo numérico.**
	 _Pois isso economiza muito espaço. Suponha um espaço de endereçamento virtual de 32 bits, o que corresponde a 2³² bytes (4 Gigabytes). 
	 Em um mapeamento feito sobre células, para cada byte individual, a tabela de mapeamento precisaria de 2³² entradas. Se cada entrada armazenasse um endereço físico de 4 bytes, o tamanho total da tabela seria de 2³² * 4 = 16 GB. Um tamanho impraticável, até para memórias RAMs modernas.
	 Em um mapeamento por bloco, a memória é dividia em blocos de tamanho fixo, tipicamente 4 KB ou 2¹² bytes. O número de páginas no espaço de 4 GB seria (2³² bytes)/(2¹² bytes/pagina)  = 2²⁰ Páginas. Se cada página ocupar 4 bytes, o tamanho da tabela seria de 2²⁰ * 4 Bytes = 4 MB. Uma redução drástica de 16 GB para 4 MB, demostrando a viabilidade do mapeamento por blocos._
	_Exemplo do slide: Suponha uma memória lógica de 16 bytes, páginas de 4 bytes e memória física de 32 bytes. Cada endereço virtual tem duas partes, o número da página e seu offset dentro da página. O número da página é usado como index da tabela de páginas, que possui o endereço base de cada frame da memória física. Nessa memória podemos deduzir que um endereço virtual (2⁷ bits = 16 bytes) tem 5 bits de deslocamento, pois temos páginas de 4 bytes (2⁵ bits) de páginas, sobrando 2 bits para o número da página. No endereço da memória física temos 2⁸ bits (32 bytes), com 5 bits de deslocamento e 3 bits para referenciar frames, cada frame sendo composto por 4 bytes.
4. **Para que serve o bit de validade nas tabelas de páginas?**
	_O bit de validade indica se a página existe no espaço de endereçamento daquele processo, so o bit estiver em 0, tentativas de acesso à página irão gerar um segmentation fault.
	O bit de validade indica se a página se encontra na memória principal, se o bit estiver em 0, tentativas de acesso à página irão gerar um page fault._
5. **O que é um page fault, quando ocorre e quem controla a sua ocorrência? Como uma elevada taxa de page fault pode comprometer o sistema operacional?**
	 _Uma page fault ocorre quando é feita uma referencia à uma página que não está residindo na memória principal. Quem controla sua ocorrência é o MMU. Se a taxa de page faults, ou também chamada de taxa de paginação, for alta, o desempenho do sistema sera degradado, pois o swap é uma operação custosa, porque o acesso á disco é lento, isso se chama **thrashing**, onde o sistema passa maior tempo trocando páginas entre memoria e disco. E processos de I/O podem agravar mais o problema se acontecerem simultaneamente._
6. **Descreva como ocorre a fragmentação interna em um sistema que implementa paginação.**
	_A fragmentação interna ocorre na forma em que páginas são divididas. Ela ocorre no ultimo quadro alocado para um processo que raramente fica totalmente preenchido, assim, o espaço não usado é desperdiçado._
7. **Descreva as vantagens e desvantagens de paginação por demanda e antecipada.**
	_Quando necessitamos carregar uma página para memória principal, podemos escolher duas estratégias: paginação por demanda e antecipada.
	Na paginação por demanda, transferimos a página no momento em que ela é referenciada. Essa estratégia é vantajosa para memória principais menores e mais ocupadas, pois assim, temos somente o necessário dentro dela. Porem, sua maior desvantagem é uma taxa de paginação maior, pois há mais buscas por páginas, já que somente uma página é carregada por vez nessa estratégia.
	Na paginação antecipada, podemos nos aproveitar do principio da localidade espacial e carregar páginas próximas a página referenciada para reduzir a incidência de paginação. Contudo, se essas páginas não forem usadas, o sistema irá ter desperdiçado tempo e memória._
8. **Quais vantagens e desvantagens da política de alocação de páginas variável comparada à alocação fixa.**
	_Uma politica de alocação de páginas determina quantos frames um processo pode ter na memória principal, temos duas estratégias para essa abordagem: fixa e variável.
	Na política de alocação fixa, um processo tem um número fixo determinado na criação do processo, que pode pode ser usado durante a execução. Essa política é simples de implementar. Se o limite de frames for alto, temos menos compartilhamento da memória, gerando swap de processos inteiros, e se o limite for baixo, teremos uma maior incidência de paginação. Se o working set diminuir durante a execução do processo, memória sera desperdiçada._
	Na política de alocação variável, um processo pode ter números variáveis de frames que mudam durante sua execução. Se tivermos uma alta taxa de paginação, podemos alterar o limite de frames para controlar essa taxa, reduzindo essa taxa podemos começar a alocar frames para outros processos, permitindo um compartilhamento maior da memória entre processos._ 
9. **Um sistema com gerência de memória virtual por paginação possui tamanho de página com 512 posições, espaço de endereçamento virtual com 512 páginas endereçadas de 0 a 511 e memória real com 10 páginas numeradas de 0 a 9. O conteúdo atual da memória real contém apenas informações de um único processo e é descrito resumidamente na seguinte tabela:**

| Endereço Físico | Conteúdo          |
| --------------- | ----------------- |
| 1536            | Página Virtual 34 |
| 2048            | Página Virtual 09 |
| 3072            | Tabela de Páginas |
| 3584            | Página Virtual 65 |
| 4608            | Página Virtual 10 |
	**a.** Considere que a entrada da tabela de páginas contém, além do endereço do frame, o número da página virtual. Mostre o conteúdo da tabela de páginas deste processo.
	_A Tabela de paginas está no endereço 3072, que corresponde ao frame 6 (3072/512 = 6).
	A Página Virtual 09 está no frame 4 (2048/412 = 4)_

| NPV (Numero da Pagina Virtual) | Frame |
| ------------------------------ | ----- |
| 9                              | 4     |
| 10                             | 9     |
| 34                             | 3     |
| 65                             | 7     |
	**b.** Mostre o conteúdo da tabela de páginas após a página virtual 49 ser carregada na memória a partir do endereço real 0 e a página virtual 34 ser substituída pela página virtual 12.

| NPV (Numero da Pagina Virtual) | Frame |
| ------------------------------ | ----- |
| 9                              | 4     |
| 10                             | 9     |
| 12                             | 3     |
| 49                             | 0     |
| 65                             | 7     |
	**c.** Como é o formato do endereço virtual deste sistema?
	_Temos 512 páginas ou seja, 2⁹ páginas, 9 bits para o número de página e como temos 512 entradas em cada página temos também 9 bits para deslocamento na página._
	**d.** Qual endereço físico está associado ao endereço virtual 4613?
	O endereço virtual 4613 se encontra na página virtual 9, que inicia no endereço virtual 9*512 = 4608. Como o deslocamento virtual é 5, o endereço físico é a soma deste mesmo deslocamento ao endereço inicial do frame 4, como os frames tem mesmo tamanho, (4 x 512) = 2048, mais 5 de deslocamento = 2053.
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
	_O endereço físico do ultimo byte da página 3:
	A página 3 ocupa o Frame 10, ou seja seu endereço físico inicial é calculado por 10 * 2Kb, ou seja esta no 20 Kb da memória, no byte 20000 . Como queremos o ultimo byte da página adicionamos mais 2Kb e retiramos 1 byte para indicar o inicio do ultimo byte: 20000 + 2000 - 1 = 21999._
	**b.** Qual o endereço físico de uma variável que ocupa o primeiro byte da página 2?
	A página 2 está no Frame 100, então, o primeiro endereço desse frame é 2 Kb + 100 = 200.000.
	**c.** Qual o endereço físico de uma variável que tem deslocamento 10 na página 3?
	A página 3 está no Frame 10, como vimos anteriormente, o primeiro endereço é 20000, deslocando 10, vamos para o endereço 20010.
	**d.** Quais páginas do processo estão na memória?
	As páginas 0, 1, 2, 3 e 6.
11. **Para que serve o bit de modificação nas tabelas de páginas?**
	_O bit de modificação indica se uma página dentro da memória principal teve alguma alteração de escrita, ou seja, ela necessitará ser escrita de volta para o disco quando necessário. Se não modificada (clean), a cópia do disco ainda é válida._
12. **Considere um sistema com memória virtual por paginação com endereço virtual com 24 bits e página com 2048 endereços. Na tabela de páginas a seguir, de um processo em determinado instante de tempo, o bit de validade 1 indica página na memória principal e o bit de modificação 1 indica que a página sofreu alteração.**

| Página | BV  | BM  | End. do Frame |
| ------ | --- | --- | ------------- |
| 0      | 1   | 1   | 30.720        |
| 1      | 1   | 0   | 0             |
| 2      | 1   | 1   | 10.240        |
| 3      | 0   | 0   | *             |
| 4      | 0   | 0   | *             |
| 5      | 1   | 0   | 6.144         |
	**a.** Quantos bits possui o campo deslocamento do endereço virtual?
	_24 bits de endereço virtual e  página com 2¹¹ endereços, ou seja 11 bits para deslocamento._ 
	**b.** Qual o número máximo de entradas que a tabela de páginas pode ter?
	_Como temos 11 bits para deslocamento, o resto dos bits serão para o número de página, 13 bits, que dão 2¹³ = 8192 entradas._
	**c.** Qual o endereço físico que ocupa o último endereço da página 2?
	_O endereço físico do último endereço da página 2 é: 10.240 (inicial) + 2047 (tamanho total - 1) = 12287._
	**d.** Caso ocorra um page fault e uma das páginas do processo deva ser descartada, quais páginas poderiam sofrer page out?
	_As páginas com bit de validade em 0 podem sofrer page fault se referenciadas. Assim alguma página com o bit de validade 1 deve sofrer o page out, preferencialmente as páginas 1 e 5 em que o bit de modificação não está ligado, pois isso aumentaria a performance do sistema, não necessitando uma escrita em disco._
13. **Considere um sistema de memória virtual que implemente paginação no qual o limite de frames por processo é igual a três. Descreva para os itens a seguir, para os quais é apresentada uma sequência de referências a páginas pelo processo, o número total de page faults para as estratégias de realocação de páginas FIFO e LRU. Indique qual a mais eficaz para cada item.**
	**a.** 1 / 2 / 3 / 1 / 4 / 2 / 5 / 3 / 4 / 3
_FIFO:_

| 1   | 1   | 1   | 4   | 4   |
| --- | --- | --- | --- | --- |
|     | 2   | 2   | 2   | 5   |
|     |     | 3   | 3   | 3   |
_Tivemos 5 page faults._
_LRU:_

| 1   | 1   | 1   | 1   | 1   | 5   | 5   | 5   |
| --- | --- | --- | --- | --- | --- | --- | --- |
|     | 2   | 2   | 4   | 4   | 4   | 3   | 3   |
|     |     | 3   | 3   | 2   | 2   | 2   | 4   |
_Tivemos 8 page faults._

_Para essa sequência o algoritmo FIFO é o que causou menos page faults._
	**b.** 1 / 2 / 3 / 1 / 4 / 1 / 3 / 2 / 3 / 3
_FIFO:_

| 1   | 1   | 1   | 4   | 4   | 4   | 3   |
| --- | --- | --- | --- | --- | --- | --- |
|     | 2   | 2   | 2   | 1   | 1   | 1   |
|     |     | 3   | 3   | 3   | 2   | 2   |
_Tivemos 7 page faults._
_LRU:_

| 1   | 1   | 1   | 1   | 1   |
| --- | --- | --- | --- | --- |
|     | 2   | 2   | 4   | 2   |
|     |     | 3   | 3   | 3   |
_Tivemos 5 page faults._

_Para essa sequência o algoritmo LRU é o que causou menos page faults._

# Lista - Gerência de Memória - Segmentação
1. **Qual a principal diferença entre os sistemas que implementam paginação e os que implementam segmentação?**
	_A diferença reside na forma como a memória é organizada e gerenciada, e na perspectiva que cada um oferece ao programador.
	Na paginação divide tanto o espaço de endereçamento lógico do processo quanto a memória física em **blocos de tamanho fixo** (páginas e quadros, respectivamente).
	E na segmentação, divide o espaço de endereçamento de um processo em **áreas lógicas de tamanhos variáveis**, chamadas segmentos (e.g., código, dados, pilha)._
2. **Para que serve o bit de validade nas tabelas de segmentos.**
	_Para indicar se o segmento reside na memória principal._
3. **Descreva o mecanismo de tradução de um endereço virtual em um endereço real em sistemas que implementam gerência de memória virtual utilizando segmentação com paginação.**
	_Em um sistema que implementa segmentação com paginação, o endereço virtual é construído pelo numero do segmento, numero da pagina virtual e seu descolocamento. A tradução ocorre quando acessamos a tabela de páginas._
4. **Na técnica de swapping, que critérios o sistema operacional pode utilizar para selecionar os processos que sofrerão swap out?**
	_Podemos escolher qual processo sofrerá swap out, vendo o tempo de espera, prioridade do processo, estado do processo, taxa da paginação e tamanho do processo._
5. **Existe fragmentação em sistemas que implementam gerência de memória virtual? Se existe, que tipo de fragmentação é encontrado em sistemas com paginação? Que tipo de fragmentação é encontrado em sistemas com segmentação?** 
	_Sim, existe fragmentação. Em sistemas que implementam paginação, temos, a fragmentação interna, na ultima página de um processo, onde o tamanho do processo não é suficiente para completar a última página. Em sistemas que implementam segmentação, temos fragmentação externa, em que durante a remoção e inserção de segmentações, são deixados blocos livres de memória entre os segmentos._
6. **O que é o thrashing em sistemas que implementam memória virtual?**
	 _Thrashing ocorre quando o sistema perde a maioria do tempo transferindo páginas entre disco e memória principal_._
7. **Descreva o que é anomalia de Belady e se pode ocorrer com o uso de segmentação? (Para pensar: Pode ocorrer a anomalia de Belady com um algoritmo ótimo?)**
	É um comportamento contra-intuitivo em algoritmos de substituição, como FIFO, em que o aumento do número de quadros aumenta o número de page faults.
	Algoritmos como o OPT e LRU não apresentam a anomalia.
8. **Uma visão simplificada de estados dos threads é “Pronto”, “Em Execução” e “Bloqueado”, em que um thread está pronto e esperando para ser incluído no schedule, está sendo executado no processador, ou está bloqueado (por exemplo, está esperando por I/O). Isso é ilustrado na figura abaixo. Supondo que um thread esteja no estado Em Execução, responda às perguntas a seguir e explique sua resposta:**
**a. O thread mudará de estado se incorrer em um erro de página? Se mudar, para que estado passará?**
	_Vai ir para o bloqueado, pois ele espera o I/O do disco._
b. **O thread mudará de estado se gerar uma omissão do TLB que seja resolvida na  tabela de páginas? Se mudar, para que estado passará?**
_Não muda de estado._
c. **O thread mudará de estado se uma referência de endereço for resolvida na tabela de páginas? Se mudar, para que estado passará?**
	_Não muda de estado._
9. **Suponha que você esteja monitorando a taxa segundo a qual o ponteiro do algoritmo do relógio se move. (O ponteiro indica a página candidata à substituição.) O que você pode dizer sobre o sistema se observar o comportamento a seguir:**
a. **O ponteiro está se movendo rapidamente.**
	_Se o ponteiro esta se movendo rapidamente, quer dizer que o sistema esta gerando vários page-faults._
b. **O ponteiro está se movendo lentamente.**
	_Pode ser que page-faults estão sendo gerados ou que a pagina marcada foi utilizada._

## Lista Sistema de Arquivos
1. **O que é um arquivo?**
	_Arquivos são unidades logicas que armazenam informações criadas por processos._
2. **Como arquivos podem ser organizados?**
	_Arquivos podem ser estruturados em diferentes maneiras:
	Sequencia de bytes, onde não há lógica na estrutura e tudo que o sistema vê são bytes. Oferecem muita flexibilidade e é usado pelo Windows e Linux._
	_Sequencia de registros, onde os arquivos são vistos como registros de tamanho fixo, a ideia era indexar os arquivos, esta estrategia era usada em SOs antigos.
	Arvores mantém registros em seus nodos, e podem ter tamanhos diferentes. Cada registro tem uma chave para busca do mesmo._
3. **Descreva sobre os mé todos de acesso aos arquivos.**
	 Temos duas formas, sequencial onde o SO precisa ler em ordem todos os arquivos até chegar ao alvo, e direto ou randômico, o acesso pode ser feito em qualquer ordem.
4. **Quais são as vantagens da variante da alocação encadeada que usa uma FAT para encadear juntos os blocos de um arquivo?**
	A FAT é uma tabela, armazenada no incio de cada partição, que guarda os endereços de cada bloco no disco. FAT usa uma lista encadeada, carrega na memória, sem necessidade de referenciar o disco, dando mais performance ao sistema e mais segurança no caso de um ponteiro perdido.
5. **Qual a função das rotinas de E/S?**

6. **Quais as diferentes formas de implementação de uma estrutura de diretório.**
	Temos diretório de único nível, em que todos os arquivos do sistema se encontra no mesmo local. Diretório de dois níveis, onde temos um diretório de usuário e um de master que aponta . E por ultimo em arvore, que permite diversos sub-diretórios permitindo uma organização maior dos arquivos.
7. **Descreva as vantagens e desvantagens das técnicas para gerência de espaços livres.** 
	Mapa de bits mantém uma string de bits, em que cada bit representa se um bloco da memória esta livre ou não. É fácil de implementar, porém se o disco for muito grande o verto pode consumir muito espaço na memória. 
	A lista encadeada, blocos livres são encadeados, não há problema de espaço na RAM pois não precisa de uma tabela de alocação, porem é mais lento para percorrer a lista, e se perde um espaço no bloco para armazenar o ponteiro.
8. **O que é alocação contígua de blocos e quais benefícios a desfragmentação pode proporcionar quando esta técnica é utilizada? Dê um exemplo de desfragmentador para Windows. Obs: pesquise sobre o conceito de desfragmentação (não foi abordado diretamente no conteúdo da semana).**
	_A alocação contiguá é a forma mais simples, blocos são alocados continuamente no disco. A desfragmentação periódica reorganiza arquivos a fim de existir um único bloco._
9. **Descreva as vantagens e desvantagens das técnicas de alocação encadeada e indexada na gerência de alocação de espaço em disco.**
	A alocacao encadeada não tem fragmentacao externa e não necessario definir o tamanho maximo do arquivos. Porém, não possui acesso direto quando acessar um bloco e se perde espaço com ponteiros.
	A alocação indexada suporta acesso direto ao blocos e também não sofre de fragmentação externa, porem, um bloco inteiro é perdido para alocar o index do bloco do arquivo.
10. **Quais os tipos de proteção de acesso a arquivos existentes e quais suas principais vantagens?**
	 Podemos definir o tipo de acesso a um arquivo e a qual usuário, um arquivo pode ser lido, escrito e executado e podemos granularizar esses acessos a diferentes usuários, por exemplo, um usuário pode somente ler enquanto outro pode ler e escrever.
11. **Um problema da alocação contígua é que o usuário deve pré -alocar espaço suficiente para cada arquivo. Se o arquivo crescer e ficar maior do que o espaço alocado para ele, devem ser tomadas medidas especiais. Uma solução para esse problema é definir uma estrutura de arquivo composta por uma área contígua inicial (de tamanho especificado). Se essa área for preenchida, o sistema operacional definirá automaticamente uma área de estouro que será encadeada à área contígua inicial. Se a área de estouro for preenchida, outra área de estouro será alocada. Compare essa implementação de um arquivo com as implementações-padrão contígua e encadeada.**
	_Em uma implementação encadeada podemos contornar esse problema pois cada bloco pode ficar separado na memória, já que cada bloco contem um ponteiro para o próximo bloco do arquivo, assim, se o arquivo crescer em tamanho podemos somente continuar encadeando-o._
12. **Qual vantagem de utilizar uma Lista Encadeada de Blocos em Disco para monitorar os blocos livres? Qual desvantagem (cite exemplo)?**
	_Nessa implementação mantemos somente o endereço inicial do primeiro bloco livre e também não há problema de espaço na memoria principal pois não precisamos de uma tabela de alocação. Porém, requer mais tempo para achar blocos livres, pois a lista deve ser percorrida e também perdemos espaço no bloco para armazenar o endereço do próximo bloco._
13. **Descreva estratégias de alocação de arquivos em disco.**
	 _Alocação contiguá, estratégia mais simples, aloca arquivos em blocos contínuos no disco. Nessa estrategia a tabela de diretórios armazena somente o endereço inicial e a area alocada. Essa estratégia é simples e tem bom desempenho porem é suscetível a fragmentação de disco.
	 Alocação encadeada, mantem uma lista encadeada dos blocos de um arquivo, onde a primeira "word" de cada bloco é usada como um ponteiro para o próximo. Essa implementação não tem fragmentação externa, porém não possui acesso direto ao bloco. Pode implementar a FAT, que armazena os ponteiros dos blocos, para melhorar o acesso dos arquivos.
	 Alocação indexada, implementa um bloco de index que mantem ponteiros para todos os blocos de um arquivo, a tabela de diretório mantem somente o endereço do bloco de index. Nessa estratégia, temos acesso direto aos blocos e não sofremos de fragmentação externa, porem espaço é perdido na alocação de blocos de index._
14. **Descreva o que é desfragmentação e cite alguma estratégia de como realizar uma desfragmentação.**
	_A desfragmentação é o processo de mover os blocos utilizados do disco para mante-los contíguos, assim, também, mantendo o espaço livre contíguo, facilitando o acesso e alocação de arquivos. Podemos mover blocos de arquivos de diversas formas para alcançar a desfragmentação: movendo todos os blocos para um lado do disco ou tapando "buracos" com arquivos que comportem._
15. **Qual o objetivo do MBR e como o disco é particionado?**
	_A MBR (Master Boot Record) é responsável pela tarefa de boot do computador, ele possui a tabela de partição, com endereço inicial e final de cada partição.
	O disco é geralmente particionado, com o MBR na primeira partição, a tabela de partições logo após e depois o resto das partições do sistema._
16. **Explique sobre a implementação por Journaling.**
	O Journaling é uma técnica implementada em sistemas de arquivos, que aumenta a robustez do mesmo. Ela funciona mantendo registros das acoes de tomadas no disco, para que se o mesmo falhe durante uma operação, podemos recuperar seu estado antes da falha.