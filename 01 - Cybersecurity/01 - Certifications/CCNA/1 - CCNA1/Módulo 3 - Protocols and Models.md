## 3.1 As regras
## 3.1.2 Fundamentos das Comunicacoes
Todos os métodos de comunicação têm os seguintes três elementos em comum:
- **Fonte da Mensagem (Remetente)**- As fontes da mensagem são pessoas ou dispositivos eletrônicos que precisam enviar uma mensagem para outras pessoas ou dispositivos.
- **Destino da mensagem (destinatário)** - O destino recebe a mensagem e a interpreta.
- **Canal** - Consiste na mídia que fornece o caminho pelo qual a mensagem viaja da origem ao destino.
### 3.1.3 Protocolos de comunicação
O envio de uma mensagem, seja por comunicação presencial ou por rede, é regido por regras chamadas protocolos.
### 3.1.4 Estabelecimento de Regras
Os protocolos devem ter em conta os seguintes requisitos para entregar com êxito uma mensagem compreendida pelo receptor:
- Um emissor e um receptor identificados;
- Língua e gramática comum;
- Velocidade e ritmo de transmissão;
- Requisitos e confirmação ou recepção;
### 3.1.5 Requisitos de protocolo de rede
Protocolos de computador comuns incluem os seguintes requisitos:
- Codificação de mensagens;
- Formatação e encapsulamento de mensagens;
- Tamanho da mensagem;
- Tempo da mensagem;
- Opções de envio de mensagem.
### 3.1.6 Codificação de Mensagens
A codificação entre hosts deve estar em um formato adequado para o meio físico.
As mensagens enviadas pela rede são convertidas primeiramente em bits pelo host emissor. Cada bit é codificado em um padrão de tensões em fios de cobre, luz infravermelha em fibras ópticas ou microondas para sistemas sem fio. O host de destino recebe e decodifica os sinais para interpretar a mensagem.

### 3.1.7 Formatação e Encapsulamento de Mensagens
Semelhante ao envio de uma carta, uma mensagem enviada por uma rede de computadores segue regras específicas de formato para que ela seja entregue e processada.
O processo de colocar um formato de mensagem em outro formato de mensagem é chamado encapsulamento.
### 3.1.8 Tamanho da Mensagem
As restrições de tamanho dos quadros exigem que o host origem divida uma mensagem longa em pedaços individuais que atendam aos requisitos de tamanho mínimo e máximo. A mensagem longa será enviada em quadros separados, e cada um contém uma parte da mensagem original.
### 3.1.9 Temporização de Mensagem
A temporização da mensagem inclui o seguinte:
- **Controle de Fluxo** - Este é o processo de gerenciamento da taxa de transmissão de dados. O controle de fluxo define quanta informação pode ser enviada e a velocidade com que pode ser entregue. Na comunicação de rede, existem protocolos de rede usados pelos dispositivos de origem e destino para negociar e gerenciar o fluxo de informações.
- **Tempo limite da resposta** - Os hosts da rede usam protocolos de rede que especificam quanto tempo esperar pelas respostas e que ação executar se ocorrer um tempo limite de resposta.
- **Método de acesso** - Quando um dispositivo deseja transmitir em uma LAN sem fio, é necessário que a placa de interface de rede (NIC) da WLAN determine se a mídia sem fio está disponível.
### 3.1.10 Opções de Envio de Mensagem
Existem três tipos de comunicações de dados incluem:
- **Unicast** - As informações estão sendo transmitidas para um único dispositivo final.
- **Multicast** - Informações estão sendo transmitidas para um ou mais dispositivos finais.
- **Broadcast** - Informações estão sendo transmitidas para todos os dispositivos finais.
### 3.1.11 Uma Nota Sobre o Ícone de Nó 
Documentos e topologias de rede geralmente representam dispositivos de rede e finais usando um ícone de nó. Os nós são tipicamente representados como um círculo.

## 3.2 Protocolos
### 3.2.1 Visão geral de protocolo de rede
Os protocolos de rede definem um formato comum e um conjunto de regras para a troca de mensagens entre dispositivos. Os protocolos são implementados por dispositivos finais e dispositivos intermediários em software, hardware ou ambos. Cada protocolo de rede tem sua própria função, formato e regras para comunicações.


| Tipo de Protocolo                   | Descrição                                                                                                                                                                                                                                                                                                                       |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Protocolos de comunicação em rede   | Os protocolos permitem que dois ou mais dispositivos se comuniquem através de um ou mais Redes. A família de tecnologias Ethernet envolve uma variedade de Protocolos como IP, Transmission Control Protocol (TCP), HyperText Protocolo de transferência (HTTP) e muito mais.                                                   |
| Protocolos de segurança de rede     | Protocolos protegem os dados para fornecer autenticação, integridade dos dados e criptografia de dados. Exemplos de procolos seguros incluem o Secure Shell (SSH), SSL (Secure Sockets Layer) e TLS (Transport Layer Security).                                                                                                 |
| Protocolos de roteamento            | Protocolos permitem que os roteadores troquem informções de rota, compare caminho e, em seguida, selecionar o melhor caminho para o destino remoto. Exemplos de protocolos de roteamento incluem Open Shortest Path First (OSPF) e Border Gateway Protocol (BGP).                                                               |
| Protocolos de descoberta de serviço | Protocolos são usados para a detecção automática de dispositivos ou serviços. Exemplos de protocolos de detecção de serviços incluem Dynamic Host Configuration Protocol (DHCP) que detecta serviços para a alocação de endereços IP e Domain Name Service (DNS) que é usado para executar conversão de nome para endereço IP.  |
## 3.2.2 Funções de protocolo de redese

| Função                 | Descrição                                                                                                                                                                                                                                                                                  |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Endereçamento          | Identifica o remetente e o destinatário pretendido da mensagem usando um esquema de endereçamento definido. Exemplos de protocolos que fornecem incluem Ethernet, IPv4, IPv6.                                                                                                              |
| Confiabilidade         | Esta função fornece mecanismos de entrega garantidos em caso de mensagens perdidas ou corrompidas em trânsito. O TCP fornece entrega garantida.                                                                                                                                            |
| Controle de Fluxo      | Esta função garante que os fluxos de dados a uma taxa eficiente entr dois dispiositvois de comiucaçào. O TCP fornece servicos de controle de fluxo.                                                                                                                                        |
| Sequenciamento         | Esta função rotula exclusivamente cada segmento de dados transmitido. A usa as informações de sequenciamento para remontar a informações corretamente. Isso é util se os segmento de dados forem perdidos, atrasados ou recebida fora de ordem. O TCP fornece serviços de sequenciamento . |
| Detecção de erros      | Esta função é usada para determinar se os dados foram corrompidos durante transmissão. Vários protocolos que fornecem detecção de erros incluem Ethernet, IPv4, IPv6, e TCP                                                                                                                |
| Interface de aplicação | Esta função contém informações usadas para processo a processo de comunicação entre aplicações de rede. Por exemplo, ao acessar uma página da web, protocolos HTTP ou HTTPS são usados para se comunicar entre os processos da web do cliente e do servidor.                               |
### 3.2.3 Interação de Protocolos
Uma mensagem enviada através de uma rede de computadores normalmente requer o uso de vários protocolos, cada um com suas próprias funções e formato.

## 3.3 Conjunto de protocolos
### 3.3.1 Conjunto de protocolos de rede
Um conjunto de protocolos é um grupo de protocolos inter-relacionados necessários para executar uma função de comunicação.
Uma das melhores maneiras de visualizar como os protocolos dentro de uma suíte interagem é ver a interação como uma pilha. Uma pilha de protocolos mostra como os protocolos individuais dentro de uma suíte são implementados. Os protocolos são visualizados em termos de camadas, com cada serviço de nível superior, dependendo da funcionalidade definida pelos protocolos mostrados nos níveis inferiores. As camadas inferiores da pilha estão relacionadas com a movimentação de dados pela rede e o fornecimento de serviços às camadas superiores, que se concentram no conteúdo da mensagem que está sendo enviada.

### 3.3.2 Evolução dos conjuntos de protocolos
Uma suíte de protocolos é um grupo de protocolos que funciona em conjunto para fornecer serviços abrangentes de comunicação em redes.
- **Internet Protocol Suite ou TCP/IP** - Este é o conjunto de protocolos mais comum e relevante usado hoje. O conjunto de protocolos TCP/IP é um conjunto de protocolos padrão aberto mantido pela Internet Engineering Task Force (IETF).
- **Protocolos de Interconexão de Sistemas Abertos (OSI)** - Esta é uma família de protocolos desenvolvidos conjuntamente em 1977 pela Organização Internacional de Normalização (ISO) e pela União Internacional de Telecomunicações (UIT). O protocolo OSI também incluiu um modelo de sete camadas chamado modelo de referência OSI. O modelo de referência OSI categoriza as funções de seus protocolos. Hoje OSI é conhecido principalmente por seu modelo em camadas. Os protocolos OSI foram amplamente substituídos por TCP/IP.
- **AppleTalk** - Um conjunto de protocolos proprietário de curta duração lançado pela Apple Inc. em 1985 para dispositivos Apple. Em 1995, a Apple adotou o TCP/IP para substituir o AppleTalk.
- **Novell NetWare** - Um conjunto de protocolos proprietário de curta duração e sistema operacional de rede desenvolvido pela Novell Inc. em 1983 usando o protocolo de rede IPX. Em 1995, a Novell adotou o TCP/IP para substituir o IPX.
![[Screenshot_2025-11-18_15-09-45.png]]

### 3.3.3 Exemplo de Protocolo TCP/IP
Os protocolos TCP / IP estão disponíveis para as camadas de aplicativo, transporte e Internet. Não há protocolos TCP/IP na camada de acesso à rede. Os protocolos LAN da camada de acesso à rede mais comuns são os protocolos Ethernet e WLAN (LAN sem fio). Os protocolos da camada de acesso à rede são responsáveis por entregar o pacote IP pela mídia física.
### 3.3.4 Suíte de Protocolos TCP/IP
![[Pasted image 20251118151156.png]]
#### **Camada de aplicação**
Sistema de nomes
- **DNS** - Sistema de nomes de domínio. Converte nomes de domínio, como [cisco.com](http://cisco.com), em endereços IP.
Configuração de hosts
- **DHCPv4** - Protocolo de configuração de host dinâmico para IPv4. Um servidor DHCPv4 atribui dinamicamente informações de endereçamento IPv4 aos clientes DHCPv4 na inicialização e permite que os endereços sejam reutilizados quando não forem mais necessários.
- **DHCPv6** - Protocolo de Configuração do Host Dinâmico para IPv6. DHCPv6 é semelhante ao DHCPv4. Um servidor DHCPv6 atribui dinamicamente informações de endereçamento IPv6 aos clientes DHCPv6 na inicialização.
- **SLAAC** - Configuração automática de endereço sem estado. Um método que permite que um dispositivo obtenha suas informações de endereçamento IPv6 sem usar um servidor DHCPv6.
E-mail
- **SMTP** -Protocolo de transferência de correio simples. Permite que os clientes enviem e-mails para um servidor de e-mail e permite que os servidores enviem e-mails para outros servidores.
- **POP3** - Post Office Protocol versão 3. Permite que os clientes recuperem e-mails de um servidor de e-mail e baixem o e-mail para o aplicativo de e-mail local do cliente.
- **IMAP** - Protocolo de Acesso à Mensagem na Internet. Permite que os clientes acessem o e-mail armazenado em um servidor de e-mail e também mantenham o e-mail no servidor.
Transferência de arquivos
- **FTP** - Protocolo de transferência de arquivos. Define as regras que permitem que um usuário em um host acesse e transfira arquivos para e de outro host em uma rede. O FTP é um protocolo de entrega de arquivos confiável, orientado a conexão e reconhecido.
- **SFTP** - Protocolo de transferência de arquivos SSH. Como uma extensão do protocolo Secure Shell (SSH), o SFTP pode ser usado para estabelecer uma sessão segura de transferência de arquivos na qual a transferência é criptografada. SSH é um método para login remoto seguro que normalmente é usado para acessar a linha de comando de um dispositivo.
- **TFTP** - Protocolo de Transferência de Arquivos Trivial. Um protocolo de transferência de arquivos simples e sem conexão com entrega de arquivos não confirmada e de melhor esforço. Ele usa menos sobrecarga que o FTP.
Web e serviço Web
- **HTTP** - Protocolo de transferência de hipertexto. Um conjunto de regras para a troca de texto, imagens gráficas, som, vídeo e outros arquivos multimídia na World Wide Web.
- **HTTPS** - HTTP seguro. Uma forma segura de HTTP que criptografa os dados que são trocados pela World Wide Web.
- **REST** - Representational State Transfer. Um serviço Web que utiliza interfaces de programação de aplicações (APIs) e pedidos HTTP para criar aplicações Web.
**Camada de transporte**
Conexão orientada
- **TCP** - Protocolo de controle de transmissão. Permite a comunicação confiável entre processos executados em hosts separados e fornece transmissões confiáveis e reconhecidas que confirmam a entrega bem-sucedida.
Sem Conexão
- **UDP** - Protocolo de datagrama do usuário. Permite que um processo em execução em um host envie pacotes para um processo em execução em outro host. No entanto, o UDP não confirma a transmissão bem-sucedida do datagrama.
**Camada de Internet**
Protocolo IP (Internet Protocol)
- **IPv4** - Protocolo da Internet versão 4. Recebe segmentos de mensagem da camada de transporte, empacota mensagens em pacotes e endereça pacotes para entrega de ponta a ponta através de uma rede. O IPv4 usa um endereço de 32 bits.
- **IPv6** - IP versão 6. Semelhante ao IPv4, mas usa um endereço de 128 bits.
- **NAT** - Tradução de endereços de rede. Converte endereços IPv4 de uma rede privada em endereços IPv4 públicos globalmente exclusivos.
Mensagens
- **ICMPv4** - Protocolo de mensagens de controle da Internet para IPv4. Fornece feedback de um host de destino para um host de origem sobre erros na entrega de pacotes.
- **ICMPv6** - ICMP para IPv6. Funcionalidade semelhante ao ICMPv4, mas é usada para pacotes IPv6.
- **ICMPv6 ND** - Descoberta de vizinho ICMPv6. Inclui quatro mensagens de protocolo que são usadas para resolução de endereço e detecção de endereço duplicado.
Protocolos de roteamento
- **OSPF** - Abrir o caminho mais curto primeiro. Protocolo de roteamento de estado de link que usa um experimento hierárquico baseado em áreas. OSPF é um protocolo de roteamento interno padrão aberto.
- **EIGRP** - Protocolo de roteamento de gateway interno aprimorado. Um protocolo de roteamento de padrão aberto desenvolvido pela Cisco que usa uma métrica composta com base na largura de banda, atraso, carga e confiabilidade.
- **BGP** - Protocolo de gateway de fronteira. Um protocolo de roteamento de gateway externo padrão aberto usado entre os Internet Service Providers (ISPs). O BGP também é comumente usado entre os ISPs e seus grandes clientes particulares para trocar informações de roteamento.
**Camada de acesso à rede**
Resolução de endereços
- **ARP** - Protocolo de Resolução de Endereço. Fornece mapeamento de endereço dinâmico entre um endereço IPv4 e um endereço de hardware.
    **Observação**: Você pode ver outro estado de documentação que o ARP opera na Camada da Internet (Camada OSI 3). No entanto, neste curso, afirmamos que o ARP opera na camada de Acesso à Rede (OSI Camada 2) porque seu objetivo principal é descobrir o endereço MAC do destino. Um endereço MAC é um endereço da camada 2.

Protocolos de link de dados
- **Ethernet** - Define as regras para os padrões de fiação e sinalização da camada de acesso à rede.
- **WLAN** - Rede local sem fio. Define as regras para sinalização sem fio nas frequências de rádio de 2,4 GHz e 5 GHz.

## 3.4 Empresas de padrões
### 3.4.1 Padrões Abertos
Os padrões abertos incentivam a interoperabilidade, a concorrência e a inovação. Eles também garantem que o produto de nenhuma empresa possa monopolizar o mercado ou ter uma vantagem injusta sobre a concorrência.
As organizações padronizadoras geralmente são organizações sem fins lucrativos e independentes de fornecedores estabelecidas para desenvolver e promover o conceito de padrões abertos.
### 3.4.2 Padrões da Interne
Várias organizações têm responsabilidades diferentes para promover e criar padrões para a Internet e o protocolo TCP / IP:

- **Internet Society (ISOC)** - Responsável por promover o desenvolvimento aberto e a evolução do uso da Internet em todo o mundo.
- **Internet Architecture Board (IAB)** - Responsável pelo gerenciamento e desenvolvimento geral dos padrões da Internet.
- **Força-tarefa de Engenharia da Internet (IETF)** - Desenvolve, atualiza e mantém as tecnologias de Internet e TCP / IP. Isso inclui o processo e os documentos para o desenvolvimento de novos protocolos e a atualização de protocolos existentes, conhecidos como documentos RFC (Request for Comments).
- **Força-Tarefa de Pesquisa na Internet (IRTF)** - Focada em pesquisas de longo prazo relacionadas à Internet e aos protocolos TCP / IP, como o Grupo de Pesquisa Anti-Spam (ASRG), o Grupo de Pesquisa do Fórum Criptografado (CFRG) e o Ponto a Ponto Grupo de Pesquisa (P2PRG).
Organizações de padrões envolvidas no desenvolvimento e suporte do TCP/IP e inclui a IANA e a ICANN.
- **Corporação da Internet para nomes e números atribuídos (ICANN)** - sediada nos Estados Unidos, a ICANN coordena a alocação de endereços IP, o gerenciamento de nomes de domínio e a atribuição de outras informações usadas nos protocolos TCP / IP.
- **Autoridade para atribuição de números da Internet (IANA)** - Responsável pela supervisão e gerenciamento da alocação de endereços IP, gerenciamento de nomes de domínio e identificadores de protocolo da ICANN.

## 3.4.3 Padrões eletrônicos e de comunicações
Outras organizações de padrões têm responsabilidades em promover e criar os padrões eletrônicos e de comunicação usados para entregar os pacotes IP como sinais eletrônicos em um meio com ou sem fio.
Essas organizações padrão incluem o seguinte:

- **Institute of Electrical and Electronics Engineers** (**IEEE**, pronuncia-se “I-três-E”) - Organização padronizadora de engenharia elétrica e eletrônica que se dedica ao progresso da inovação tecnológica e à criação de padrões em vários setores, inclusive força e energia, saúde, telecomunicações e redes. Os padrões de rede IEEE importantes incluem o padrão 802.3 Ethernet e 802.11 WLAN. Pesquise na Internet para outros padrões de rede IEEE.
- **Aliança das Indústrias Eletrônicas (EIA)** - A organização é mais conhecida por seus padrões relacionados à fiação elétrica, conectores e racks de 19 polegadas usados para montar equipamentos de rede.
- **Associação da Indústria de Telecomunicações (TIA)** - Organização responsável pelo desenvolvimento de padrões de comunicação em uma variedade de áreas, incluindo equipamentos de rádio, torres celulares, dispositivos de Voz sobre IP (VoIP), comunicações via satélite e muito mais. A figura mostra um exemplo de um cabo Ethernet certificado que foi desenvolvido cooperativamente pela TIA e pela EIA.
- **Setor de Normalização das Telecomunicações da União Internacional de Telecomunicações (ITU-T)** - Uma das maiores e mais antigas organizações de padrões de comunicação. A ITU-T define padrões para a compactação de vídeo, televisão por IP (IPTV) e comunicações de banda larga, como DSL.
## 3.5 Modelos de Referência
### 3.5.1 Os Benefícios de Se Usar um Modelo de Camadas
Conceitos complexos, como a forma como uma rede opera, podem ser difíceis de explicar e compreender. Por esta razão, um modelo em camadas é usado para modularizar as operações de uma rede em camadas gerenciáveis.
Estes são os benefícios do uso de um modelo em camadas para descrever protocolos e operações de rede:
- Auxiliar no projeto de protocolos porque os protocolos que operam em uma camada específica definiram as informações sobre as quais atuam e uma interface definida para as camadas acima e abaixo
- Fomentar a concorrência porque produtos de diferentes fornecedores podem trabalhar juntos
- Impedir que alterações de tecnologia ou capacidade em uma camada afetem outras camadas acima e abaixo
- Fornecer uma linguagem comum para descrever funções e capacidades de rede
Existem dois modelos em camadas que são usados para descrever operações de rede:
- Modelo de referência OSI (Open System Interconnection)
- Modelo de referência TCP / IP
### 3.5.2 O Modelo de Referência OSI
Ele descreve a interação de cada camada com as camadas diretamente acima e abaixo.

| Camada de modelo OSI | Descrição                                                                                                                                                                                                     |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 7 - Aplicação        | A camada de aplicação contém protocolos usados para comunicação processos a processo.                                                                                                                         |
| 6 - Apresentação     | A camada de apresentação fornece um representação comum dos dados transferidos entre serviços da camada de aplicação.                                                                                         |
| 5 - Sessão           | A camada de sessão fornece serviços para a camada de apresentação para organizar seu diálogo e gerenciar o intercâmbio de dados.                                                                              |
| 4 - Transporte       | A camada de transporte define serviços para segmentar, transferir e remontar os dados para comunicações individuais entre os dispositivos finais.                                                             |
| 3 - Rede             | A camada de rede fornece serviços para trocar as partes individuais de dados através da rede entre dispositivos finais identificados.                                                                         |
| 2 - Enlace de dados  | Os protocolos da camada de enlace descrevem métodos para troca de quadros entre dispositivos em uma mídia comum                                                                                               |
| 1 - Físico           | Os protocolos da camada física descrevem o mecânico, elétrico, meios funcionais e processuais para ativar, manter e desativar conexões físicas para uma transmissão de bits de e para um dispositivo de rede. |
**Observação:** Enquanto as camadas do modelo TCP / IP são referidas apenas pelo nome, as sete camadas do modelo OSI são mais frequentemente referidas pelo número do que pelo nome. Por exemplo, a camada física é chamada de Camada 1 do modelo OSI, a camada de vínculo de dados é a Camada 2 e assim por diante.

### 3.5.3 O Modelo de Protocolo TCP/IP
O modelo de protocolo TCP / IP para comunicações entre redes foi criado no início dos anos 70 e às vezes é chamado de modelo da Internet. Esse tipo de modelo corresponde à estrutura de um conjunto de protocolos específico. O modelo TCP/IP é um modelo de protocolo porque descreve as funções que ocorrem em cada camada de protocolos dentro da suíte TCP/IP.

| Camada do modelo TCP/IP | Descrição                                                                      |
| ----------------------- | ------------------------------------------------------------------------------ |
| 4 - Aplicação           | Representa dados para o usuário, além do controle de codificação e de diálogo. |
| 3 - Transporte          | Permite a comunicação entre vários dispositivos diferentes em redes distintas. |
| 2 - Internet            | Determina o melhor caminho pela rede.                                          |
| 1 - Acesso à Rede       | Controla os dispositivos de hardware e o meio físico que formam a rede.        |
As definições do padrão e dos protocolos TCP / IP são discutidas em um fórum público e definidas em um conjunto disponível ao público de RFCs da IETF. Um RFC é criado por engenheiros de rede e enviado a outros membros do IETF para comentários.

### 3.5.4 Comparação de modelos OSI e TCP / IP
Os protocolos que compõem a suíte de protocolos TCP/IP também podem ser descritos em termos do modelo de referência OSI. No modelo OSI, a camada de acesso à rede e a camada de aplicação do modelo TCP/IP são, divididas para descrever funções discretas que devem ocorrer nessas camadas.

As principais semelhanças estão nas camadas de transporte e rede; no entanto, os dois modelos diferem em como eles se relacionam com as camadas acima e abaixo de cada camada:

- A Camada OSI 3, a camada de rede, é mapeada diretamente para a camada de Internet TCP / IP. Essa camada é usada para descrever os protocolos que endereçam e encaminham mensagens em uma rede interconectada.
- A Camada OSI 4, a camada de transporte, mapeia diretamente para a camada de transporte TCP / IP. Essa camada descreve os serviços e as funções gerais que fornecem uma entrega ordenada e confiável de dados entre os hosts origem e destino.
- A camada de aplicativos TCP / IP inclui vários protocolos que fornecem funcionalidade específica para uma variedade de aplicativos do usuário final. As camadas 5, 6 e 7 do modelo OSI são usadas como referências para desenvolvedores e fornecedores de software de aplicação para produzir aplicaçõesque operam em redes.
- Ambos os modelos TCP/IP e OSI são usados geralmente para referenciar protocolos em várias camadas. Como o modelo OSI separa a camada de enlace de dados da camada física, geralmente é usado para referenciar as camadas inferiores.

| Modelo OSI                                  | Modelo TCP/IP<br><br> |
| ------------------------------------------- | --------------------- |
| Aplicação<br><br>Apresentação<br><br>Sessão | Aplicação<br><br>     |
| Transporte                                  | Transporte<br><br>    |
| Rede                                        | Internet<br><br>      |
| Enlace de Dados<br><br>Física<br>           | Acesso à Rede         |
## 3.6 Encapsulamento de dados
### 3.6.1 Segmentando Mensagens
Segmentação é o processo de dividir um fluxo de dados em unidades menores para transmissões através da rede. A segmentação é necessária porque as redes de dados usam o conjunto de protocolos TCP/IP enviar dados em pacotes IP individuais. Cada pacote é enviado separadamente, semelhante ao envio de uma carta longa como uma série de cartões postais individuais. Pacotes que contêm segmentos para o mesmo destino podem ser enviados por caminhos diferentes.
Isso leva à segmentação de mensagens com dois benefícios principais:
- **Aumenta a velocidade** - Como um fluxo de dados grande é segmentado em pacotes, grandes quantidades de dados podem ser enviadas pela rede sem amarrar um link de comunicação. Isso permite que muitas conversas diferentes sejam intercaladas na rede chamada multiplexação.
- **Aumenta a eficiência** -Se um único segmento não conseguir alcançar seu destino devido a uma falha na rede ou no congestionamento da rede, somente esse segmento precisa ser retransmitido em vez de reenviar todo o fluxo de dados.
### 3.6.2 Sequenciamento
Nas comunicações em rede, cada segmento da mensagem deve passar por um processo semelhante para garantir que chegue ao destino correto e possa ser remontado no conteúdo da mensagem original.
### 3.6.3 Unidades de Dados de Protocolo (PDU)
O formato que uma parte de dados assume em qualquer camada é chamado de unidade de dados de protocolo (PDU). Durante o encapsulamento, cada camada sucessora encapsula a PDU que recebe da camada superior de acordo com o protocolo sendo usado. Em cada etapa do processo, uma PDU possui um nome diferente para refletir suas novas funções.

As PDUs são nomeadas de acordo com os protocolos do conjunto TCP / IP.
- Dados - o termo genérico para a PDU usada na camada de aplicação;
- Segmento - PDU da camada de transporte;
- Pacote - PDU da camada de rede;
- Quadro - PDU da camada de enlace de dados
- Bits - PDU da camada física usada ao transmitir dados fisicamente pela mídia.
Obs: Se o cabeçalho de transporte é TCP, então é um segmento. Se o cabeçalho Transporte é UDP, então é um datagrama.
## 3.7 Acesso a dados
### 3.7.1 Endereços
- **Endereços de origem e destino da camada de rede** - Responsável por entregar o pacote IP da origem original ao destino final, que pode estar na mesma rede ou em uma rede remota.
- **Endereços de origem e destino da camada de enlace de dados** - Responsável por fornecer o quadro de enlace de dados de uma placa de interface de rede (NIC) para outra NIC na mesma redes
## 3.7.2 Endereço Lógico da Camada 3
Um endereço IP é o endereço lógico da camada de rede, ou camada 3, usado para entregar o pacote IP da origem original ao destino final.
O pacote IP contém dois endereços IP:

- **Endereço IP de origem** - O endereço IP do dispositivo de envio, que é a fonte original do pacote.
- **Endereço IP de destino** - O endereço IP do dispositivo receptor, que é o destino final do pacote.
Os endereços IP indicam o endereço IP de origem original e o endereço IP de destino final. Isso é verdadeiro se a origem e o destino estão na mesma rede IP ou redes IP diferentes.

Um endereço IP contém duas partes:

- **Parte da rede (IPv4) ou Prefixo (IPv6)** - A parte mais à esquerda do endereço que indica a rede na qual o endereço IP é um membro. Todos os dispositivos na mesma rede terão a mesma parte da rede no endereço.
- **Parte do host (IPv4) ou ID da interface (IPv6)** - A parte restante do endereço que identifica um dispositivo específico na rede. Essa parte é exclusiva para cada dispositivo ou interface na rede.
**Observação:** A máscara de sub-rede (IPv4) ou comprimento do prefixo (IPv6) é usada para identificar a parte da rede de um endereço IP da parte do host.
### 3.7.4 Função dos endereços da camada de enlace de dados - Mesma rede IP
Quando o remetente e o destinatário do pacote IP estiverem na mesma rede, o quadro de enlace de dados será enviado diretamente para o dispositivo receptor. Em uma rede Ethernet, os endereços do link de dados são conhecidos como endereços Ethernet Media Access Control (MAC).

Os endereços MAC são embutidos fisicamente na NIC Ethernet.

### 3.7.6 Função dos Endereços da Camada de Rede - Rede Remota
Quando o remetente do pacote estiver em uma rede diferente do destinatário, os endereços IP de origem e destino representarão hosts em redes diferentes.

ORIGEM PRIMEIRO E DEPOIS DESTINO NO PACOTE
### 3.7.7 Função dos endereços da camada de enlace de dados - Redes IP diferentes
Quando o remetente e o destinatário do pacote IP estiverem em redes diferentes, não será possível enviar o quadro de enlace de dados Ethernet diretamente ao host de destino, pois ele não poderá ser alcançado diretamente na rede do remetente. O quadro Ethernet deve ser enviado a outro dispositivo conhecido como o roteador ou gateway padrão.
É importante que o endereço IP do gateway padrão seja configurado em cada host na rede local. Todos os pacotes para destinos em redes remotas são enviados para o gateway padrão.

### 3.7.8 Endereços de Enlace de Dados
Antes que um pacote IP possa ser enviado por uma rede com ou sem fio, ele deve ser encapsulado em um quadro de enlace de dados, para que possa ser transmitido pela mídia física.

Conforme o pacote IP viaja do host para o roteador, de roteador para roteador e de roteador para host, em cada ponto ao longo do caminho, o pacote IP é encapsulado em um novo quadro de enlace de dados. Cada quadro de enlace de dados contém o endereço de enlace de dados origem da placa NIC que envia o quadro, e o endereço de enlace de dados destino da placa NIC que recebe o quadro.

DESTINO PRIMEIRO E DEPOIS ORIGEM NO FRAME