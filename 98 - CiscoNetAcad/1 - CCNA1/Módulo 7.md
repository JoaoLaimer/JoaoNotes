## 7.1 Quadros Ethernet
### 7.1.1 Encapsulamento Ethernet
A Ethernet é uma das duas tecnologias de LAN usadas atualmente, sendo a outra LANs sem fio (WLANs). A Ethernet utiliza comunicações com fios, incluindo par trançado, ligações de fibra óptica e cabos coaxiais.
la opera na camada de enlace de dados e na camada física. É uma família de tecnologias de rede definidas nos padrões IEEE 802.2 e 802.3. A Ethernet suporta larguras de banda de dados do seguinte:
- 10 Mbps
- 100 Mbps
- 1000 Mbps (1 Gbps)
- 10,000 Mbps (10 Gbps)
- 40,000 Mbps (40 Gbps)
- 100,000 Mbps (100 Gbps)
### 7.1.2 Subcamadas de Enlace de Dados
Protocolos IEEE 802 LAN/MAN, incluindo Ethernet, usam as seguintes duas subcamadas separadas da camada de link de dados para operar. Eles são o controle de link lógico (LLC) e o controle de acesso de mídia (MAC).
Lembre-se de que LLC e MAC têm as seguintes funções na camada de link de dados:
- **Subcamada LLC Sublayer** - Essa subcamada IEEE 802.2 se comunica entre o software de rede nas camadas superiores e o hardware do dispositivo nas camadas inferiores. Ela coloca a informação no quadro que identifica qual protocolo de camada de rede está sendo usado para o quadro. Essas informações permitem que vários protocolos da camada 3, como IPv4 e IPv6, usem a mesma interface de rede e mídia.
- **Subcamada MAC** - Esta subcamada (IEEE 802.3, 802.11 ou 802.15 por exemplo) é implementada em hardware e é responsável pelo encapsulamento de dados e controle de acesso a mídia. Ele fornece endereçamento de camada de link de dados e é integrado com várias tecnologias de camada física.
### 7.1.3 Subcamada MAC
A subcamada MAC é responsável pelo encapsulamento de dados e acesso à mídia.
**Encapsulamento de Dados**
O encapsulamento de dados IEEE 802.3 inclui o seguinte:
- **Quadro Ethernet** - Esta é a estrutura interna do quadro Ethernet.
- **Endereçamento Ethernet** - O quadro Ethernet inclui um endereço MAC de origem e de destino para fornecer o quadro Ethernet da NIC Ethernet para a NIC Ethernet na mesma LAN.
- **Detecção de erro Ethernet** - O quadro Ethernet inclui um trailer de sequência de verificação de quadros (FCS) usado para detecção de erros.
**Acessando a mídia**
A subcamada MAC IEEE 802.3 inclui as especificações para diferentes padrões de comunicações Ethernet em vários tipos de mídia, incluindo cobre e fibra.

### 7.1.4 Campos de um Quadro Ethernet
O tamanho mínimo de quadro Ethernet é 64 bytes e o máximo é 1518 bytes. O campo de preâmbulo não é incluído ao descrever o tamanho do quadro.
Qualquer quadro com comprimento menor que 64 bytes é considerado um "fragmento de colisão" ou um "quadro desprezível" (runt) e é automaticamente descartado pelas estações receptoras. Quadros com mais de 1.500 bytes de dados são considerados “jumbo” ou “baby giant”.
Os quadros jumbo geralmente são suportados pela maioria dos switches e NICs Fast Ethernet e Gigabit Ethernet.

**Quadro Ethernet**
Total 64 à 1518 bytes, sem contar o Preâmbulo.

| 8 Bytes         | 6 Bytes                 | 6 Bytes                | 2 Bytes          | 46 -1500 Bytes | 4 Bytes |
| --------------- | ----------------------- | ---------------------- | ---------------- | -------------- | ------- |
| Preâmbulo e SFD | Endereço MAC de destino | Endereço MAC de origem | Tipo/Comprimento | Dados          | FCS     |

| Campo                                          | Descrição                                                                                                                                                                                                                                                                                                                                                                                     |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Campo Preâmbulo e Delimitador Início de Quadro | O Preâmbulo (7 Bytes) e o Delimitador de Quadro Inicial (SFD), também chamado de Inicio do Frame (1 Byte), os campos são usados para sincronização entre os dispositivos de envio e recepção. Estes primeiros oito bytes são usados para chamar a atenção do nós de recepção. Essencialmente, o primeiro poucos bytes informam aos receptores para se prepararem para receber um novo quadro. |
| Campo Endereço MAC de Destino                  | Este campo de 6 bytes é o identificador do destinatário desejado.                                                                                                                                                                                                                                                                                                                             |
| Campo Endereço MAC de Origem                   | Esse campo de 6 bytes identifica a NIC ou interface de origem do quadro.                                                                                                                                                                                                                                                                                                                      |
| Tipo/Comprimento (EtherType)                   | Esse campo de 2 bytes identifica o protocolo da camada supedrior encapsulado em no quadro Ethernet. Os valores comuns são, em hexadecimal, 0x800 para IPv4 ,0x86DD para IPv6 e 0x806 para ARP.                                                                                                                                                                                                |
| Campo de Dados                                 | Este campo (46 - 1500 bytes) contém os dados encapsulador de uma camada superior. Todos os quadros devem ter pelo menos 64 bytes. Se um pacote pequeno for encapsulado, bits adicionais chamados de pads são usados, para aumentar o tamanho do quadro para seu tamanho minimo.                                                                                                               |
| Campo Sequência de Verificação de Quadro       | O FCS (Frame Check Sequence) (4 bytes) é usado para detectar erros em um quadro. Ele utiliza uma verificação de redundância cíclica (CRC). O dispositivo de envio inclui os resultados de um CRC no campo FCS do quadro. O  dispositivo receptor recebe o quadro e gera um CRC para procurar erros. Se o cálculo não coincidem o quadro é descartado.                                         |

## 7.2 Endereços MAC Ethernet
### 7.2.1 Endereço MAC e Hexadecimal
Um endereço MAC Ethernet consiste em um valor binário de 48 bits. Hexadecimal é usado para identificar um endereço Ethernet porque um único dígito hexadecimal representa quatro bits binários. Portanto, um endereço MAC Ethernet de 48 bits pode ser expresso usando apenas 12 valores hexadecimais.
### 7.2.2 Endereços MAC Ethernet
Um endereço MAC Ethernet é um endereço de 48 bits expresso usando 12 dígitos hexadecimais.
Todos os fornecedores que vendem dispositivos Ethernet devem se registrar no IEEE para obter um código hexadecimal exclusivo de 6 (ou seja, 24 bits ou 3 bytes) chamado identificador exclusivo organizacionalmente (OUI).
Quando um fornecedor atribui um endereço MAC a um dispositivo ou interface Ethernet, o fornecedor deve fazer o seguinte:

- Use sua OUI atribuída como os primeiros 6 dígitos hexadecimais.
- Atribua um valor exclusivo nos últimos 6 dígitos hexadecimais.
É da responsabilidade do fornecedor garantir que nenhum de seus dispositivos seja atribuído o mesmo endereço MAC. No entanto, é possível que endereços MAC duplicados existam devido a erros cometidos durante a fabricação, erros cometidos em alguns métodos de implementação de máquinas virtuais ou modificações feitas usando uma das várias ferramentas de software.

### 7.2.3 Processamento de Quadros
Às vezes, o endereço MAC é referido como endereço gravado de fábrica (BIA, burned-in-address) porque o endereço é codificado na memória somente leitura (ROM) na NIC. Isso significa que o endereço é codificado no chip da ROM permanentemente.

Nos modernos sistemas operacionais de PC e NICs, é possível alterar o endereço MAC no software. Isso é útil para tentar obter acesso a uma rede que filtre com base no BIA. Consequentemente, a filtragem ou o controle de tráfego com base no endereço MAC não é mais tão seguro.

Quando uma NIC recebe um quadro Ethernet, examina o endereço MAC de destino para verificar se corresponde ao endereço MAC físico armazenado na RAM. Se não houver correspondência, o dispositivo descartará o quadro. Caso haja, ele passará o quadro para cima nas camadas OSI, onde o processo de desencapsulamento ocorre.

### 7.2.4 Endereço MAC Unicast
Na Ethernet, são utilizados diferentes endereços MAC para comunicação unicast, broadcast e multicast da Camada 2.
Um endereço MAC de unicast é o endereço exclusivo usado quando um quadro é enviado de um único dispositivo de transmissão para um único dispositivo de destino.

O processo que um host de origem usa para determinar o endereço MAC de destino associado a um endereço IPv4 é conhecido como ARP (Address Resolution Protocol). O processo que um host de origem usa para determinar o endereço MAC de destino associado a um endereço IPv6 é conhecido como ND (Neighbour Discovery Discovery).

**Observação:** O endereço MAC de origem deve ser sempre unicast.

### 7.2.5 Endereço MAC Broadcast
Um quadro de transmissão Ethernet é recebido e processado por cada dispositivo na LAN Ethernet. Os recursos de uma transmissão Ethernet são os seguintes:
- Possui um endereço MAC de destino de FF-FF-FF-FF-FF-FF em hexadecimal (48 números binários (sendo eles no valor de 0 ou 1)).
- É inundada todas as portas de switch Ethernet, exceto a porta de entrada.
- Ele não é encaminhado por um roteador.
Se os dados encapsulados forem um pacote de transmissão IPv4, isso significa que o pacote contém um endereço IPv4 de destino que possui todos os 1s na parte do host.

DHCP para IPv4 é um exemplo de um protocolo que usa endereços de broadcast Ethernet e IP

### 7.2.6 Endereço MAC Multicast
Um quadro de multicast Ethernet é recebido e processado por um grupo de dispositivos na LAN Ethernet que pertencem ao mesmo grupo de multicast. Os recursos de um multicast Ethernet são os seguintes:

- Há um endereço MAC de destino 01-00-5E quando os dados encapsulados são um pacote multicast IPv4 e um endereço MAC de destino de 33-33 quando os dados encapsulados são um pacote multicast IPv6.
- Há outros endereços MAC de destino multicast reservados para quando os dados encapsulados não são IP, como STP (Spanning Tree Protocol) e LLDP (Link Layer Discovery Protocol).
- São inundadas todas as portas de switch Ethernet, exceto a porta de entrada, a menos que o switch esteja configurado para espionagem multicast.
- Ele não é encaminhado por um roteador, a menos que o roteador esteja configurado para rotear pacotes multicast.
 Se os dados encapsulados forem um pacote multicast IP, os dispositivos que pertencem a um grupo multicast recebem um endereço IP do grupo multicast. O intervalo de endereços multicast IPv4 é 224.0.0.0 a 239.255.255.255. O intervalo de endereços multicast IPv6 começa com ff00::/8. Como os endereços multicast representam um grupo de endereços (às vezes chamado de grupo de hosts), eles só podem ser utilizados como destino de um pacote. A origem sempre será um endereço unicast.
## 7.3 A Tabela de Endereços MAC
### 7.3.1 Noções Básicas sobre Switches
Um switch Ethernet da camada 2 usa endereços MAC da camada 2 para tomar decisões de encaminhamento. Desconhece completamente os dados (protocolo) que estão sendo transportados na parte de dados do quadro, como um pacote IPv4, uma mensagem ARP ou um pacote ND IPv6. O switch toma suas decisões de encaminhamento com base apenas nos endereços MAC Ethernet da camada 2.

Um switch Ethernet examina sua tabela de endereços MAC para tomar uma decisão de encaminhamento para cada quadro, ao contrário dos hubs Ethernet herdados que repetem bits em todas as portas, exceto a porta de entrada.
**Observação:** A tabela de endereços MAC às vezes é chamada de tabela de memória de conteúdo endereçável (CAM). Embora o termo "tabela CAM" seja muito comum, neste curso nós a chamaremos de tabela de endereços MAC.

### 7.3.2 Alternar aprendizado e encaminhamento
O switch cria a tabela de endereços MAC dinamicamente examinando o endereço MAC de origem dos quadros recebidos em uma porta.

**Aprendizado**
Todo quadro que entra em um switch é verificado quanto ao aprendizado de novas informações. Isso é feito examinando o endereço MAC de origem do quadro e o número da porta em que o quadro entrou no comutador. Se o endereço MAC de origem não existe, é adicionado à tabela juntamente com o número da porta de entrada. Se o endereço MAC de origem existir, o switch atualizará o cronômetro de atualização para essa entrada na tabela. Por padrão, a maioria dos switches Ethernet mantém uma entrada na tabela por 5 minutos.
**Nota:** Se o endereço MAC de origem não existir na tabela, mas em uma porta diferente, o switch tratará isso como uma nova entrada. A entrada é substituída usando o mesmo endereço MAC, mas com o número de porta mais atual.
**Encaminhamento**
Se o endereço MAC de destino for um endereço unicast, o switch procurará uma correspondência entre o endereço MAC de destino do quadro e uma entrada em sua tabela de endereços MAC. Se o endereço MAC de destino estiver na tabela, ele encaminhará o quadro pela porta especificada. Se o endereço MAC de destino não estiver na tabela, o switch encaminhará o quadro por todas as portas, exceto a de entrada. Isso é chamado de unicast desconhecido.
**Nota:** Se o endereço MAC de destino for um broadcast ou multicast, o quadro também inundará todas as portas, exceto a porta de entrada.

### 7.3.3 Filtragem de Quadros
A medida que um switch recebe quadros de dispositivos diferentes, ele é capaz de preencher sua tabela de endereços MAC examinando o endereço MAC de origem de cada quadro. Quando a tabela de endereços MAC do switch contém o endereço MAC de destino, ele pode filtrar o quadro e encaminhar uma única porta.

Um quadro é **flooded** para todas as portas (exceto a origem) somente se o switch não tiver o MAC de destino dentro da tabela MAC.

## 7.4 Métodos de encaminhamento e velocidades de switches
### 7.4.1 Métodos de Encaminhamento de Quadros em Switches da Cisco
Com os switches Cisco, existem realmente dois métodos de encaminhamento de quadros e há boas razões para usar um em vez do outro, dependendo da situação.

Os switches usam um dos seguintes métodos de encaminhamento para o switching (comutação) de dados entre suas interfaces de rede:

- **Switching store-and-forward** - Este método de encaminhamento de quadros recebe o quadro inteiro e calcula o CRC. O CRC usa uma fórmula matemática, baseada no número de bits (valores 1) no quadro, para determinar se o quadro recebido apresenta erro. Se o CRC é válido, o switch procura o endereço de destino, que determina a interface de saída. Em seguida, o quadro é encaminhado para fora da porta correta.
- **Switching cut-through** - Esse método de encaminhamento de quadros encaminha o quadro antes de ser totalmente recebido. Pelo menos o endereço de destino do quadro deve ser lido para que o quadro possa ser encaminhado.

Uma grande vantagem da troca de armazenamento e encaminhamento é que ele determina se um quadro tem erros antes de propagar o quadro. Quando um erro é detectado em um quadro, o switch o descarta. O descarte de quadros com erros reduz o consumo de largura de banda por dados corrompidos. O switch store-and-forward é necessário para a análise de qualidade de serviço (QoS) em redes convergentes onde a classificação de quadros para priorização de tráfego é necessária. Por exemplo, os fluxos de dados de voz sobre IP (VoIP) precisam ter prioridade sobre o tráfego de navegação na web.
### 7.4.2 Switching cut-through
No switching cut-through, o switch atua nos dados assim que eles são recebidos, mesmo que a transmissão não tenha sido concluída. O switch armazena em buffer apenas o quadro suficiente para ler o endereço MAC de destino, para que possa determinar para qual porta deve encaminhar os dados. O switch não realiza nenhuma verificação de erros no quadro.
Há duas formas de switching cut-through:
- **Comutação Fast-forward** - A comutação de avanço rápido oferece o menor nível de latência. e encaminha imediatamente um pacote depois de ler o endereço de destino. Como o switching fast-forward começa o encaminhamento antes de receber todo o pacote, alguns pacotes podem ser retransmitidos com erros. No modo fast-forward, a latência é medida do primeiro bit recebido até o primeiro bit transmitido. Switching fast-forward é o método cut-through típico de switching.
- **Comutação Fragment-free** - Na alternância sem fragmentos, o switch armazena os primeiros 64 bytes do quadro antes de encaminhar. Esse tipo de switching pode ser encarado como um compromisso entre o switching store-and-forward e o switching fast-forward. O motivo de o switching fragment-free armazenar somente os primeiros 64 bytes do quadro é que a maioria dos erros e das colisões de rede ocorre durante os primeiros 64 bytes. O switching fragment-free é um compromisso entre a alta latência e a alta integridade do switching store-and-forward e a baixa latência e a integridade reduzida do switching fast-forward.
Alguns switches são configurados para executar o switching cut-through por porta até que um limite de erro definido pelo usuário seja atingido e, depois, mudam automaticamente para store-and-forward. Quando a taxa de erros fica abaixo do limite, a porta retorna automaticamente para o switching cut-through.

### 7.4.3 Buffers de Memória em Switches
O buffer também pode ser usado quando a porta de destino está ocupada devido ao congestionamento. O switch armazena o quadro até que ele possa ser transmitido.
### Memory Buffering Methods

| Método                | Descrição                                                                                                                                                                                                                                                                                                                     |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Memória por porta     | Os quadros são armazenados em filas vinculadas a entradas e saída de portas.<br>Um único quadro pode atrasar a transmissão dos outros, devido a porta de destino estar ocupada.                                                                                                                                               |
| Memória compartilhada | Deposita todos os quadros em um buffer comum compartilhado por todos os switches e a quantidade de memória é alocada dinamicamente.<br>Os quadros são vinculados dinamicamente ao destino permitindo que um pacote seja recebido em uma porta, e em seguida, transmitida em outra porta, sem movê-lo para uma fila diferente. |
O buffer de memória compartilhada também resulta na capacidade de armazenar quadros maiores com potencialmente menos quadros descartados. Isso é importante com a comutação assimétrica, que permite taxas de dados diferentes em portas diferentes, como ao conectar um servidor a uma porta de switch de 10 Gbps e PCs a portas de 1 Gbps.

### 7.4.4 Configurações de Interface - Velocidade e Transmissão Duplex
Há dois tipos de configurações duplex usadas para comunicação em uma rede Ethernet:

- **Full-duplex** - As duas extremidades da conexão podem enviar e receber simultaneamente.
- **Half-duplex** - Somente uma extremidade da conexão pode enviar por vez.
A negociação automática é uma função opcional encontrada na maioria dos switches Ethernet e das placas de interface de rede (NICs). Ele permite que dois dispositivos negociem automaticamente as melhores capacidades de velocidade e duplex. Full-duplex será escolhido se os dois dispositivos o tiverem para a largura de banda mais alta comum entre eles.

A incompatibilidade duplex ocorre quando uma ou ambas as portas em um link são redefinidas e o processo de negociação automática não resulta nos dois parceiros de link com a mesma configuração. Também pode ocorrer quando os usuários reconfiguram um lado de um link e esquecem de reconfigurar o outro. Os dois lados de um link devem estar ambos com a negociação automática ligada ou desligada. A prática recomendada é configurar ambas as portas de switch Ethernet como full-duplex.

### 7.4.5 MDIX Automático
As conexões entre dispositivos exigiram uma vez o uso de um cabo cruzado ou direto. O tipo de cabo necessário dependia do tipo de dispositivos de interconexão.
A maioria dos dispositivos de switch agora suporta o recurso de (Auto-MDIX) interface dependente automática. Quando ativado, o switch detecta automaticamente o tipo de cabo conectado à porta e configura as interfaces de acordo. Com isso, você pode utilizar um cabo cruzado ou direto para conexões a uma porta 10/100/1000 de cobre no switch, seja qual for o tipo de dispositivo na outra extremidade da conexão.

O Auto-MDIX pode ser reativado usando o comando de configuração de **mdix auto** interface