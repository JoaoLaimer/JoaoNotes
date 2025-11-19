## 6.1 Finalidade da Camada de Enlace de Dados
## 6.1.1 A Camada de Enlace
A camada de enlace de dados do modelo OSI (Camada 2), prepara os dados da rede para a rede física.
A camada de enlace de dados é responsável pela placa de interface de rede (NIC) para comunicações de placa de interface de rede.
A camada de enlace de dados faz o seguinte:
- Permite que as camadas superiores acessem a mídia. O protocolo de camada superior não está completamente ciente do tipo de mídia que é usado para encaminhar os dados.
- Aceita dados, geralmente pacotes de Camada 3 (ou seja, IPv4 ou IPv6), e os encapsula em quadros da Camada 2.
- Controla como os dados são colocados e recebidos na mídia.
- Troca quadros entre pontos de extremidade através da mídia de rede.
- Recebe dados encapsulados, geralmente pacotes de Camada 3, e os direciona para o protocolo de camada superior apropriado.
- Executa a detecção de erros e rejeita qualquer quadro corrompido.
### 6.1.2 IEEE 802 Subcamadas de link de dados de LAN/MAN
Os padrões IEEE 802 LAN/MAN são específicos para LANs Ethernet, LANs sem fio (WLAN), redes pessoais sem fio (WPAN) e outros tipos de redes locais e metropolitanas. A camada de link de dados LAN/MAN IEEE 802 consiste nas seguintes duas subcamadas:
- **Logical Link Control (LLC)** - Esta subcamada IEEE 802.2 comunica entre o software de rede nas camadas superiores e o hardware do dispositivo nas camadas inferiores. Ela coloca a informação no quadro que identifica qual protocolo de camada de rede está sendo usado para o quadro. Essas informações permitem que vários protocolos da camada 3, como IPv4 e IPv6, usem a mesma interface de rede e mídia.
- **Controle de Acesso a Mídia (MAC)** - Implementa esta subcamada (IEEE 802.3, 802.11 ou 802.15) no hardware. É responsável pelo encapsulamento de dados e controle de acesso à mídia. Ele fornece endereçamento de camada de link de dados e é integrado com várias tecnologias de camada física.
A subcamada MAC fornece encapsulamento de dados:
- **Delimitação de quadros** - O processo de enquadramento fornece delimitadores importantes para identificar campos dentro de um quadro. Esses bits de delimitação promovem a sincronização entre os nós de transmissão e de recepção.
- **Endereçamento** - Fornece endereçamento de origem e destino para transportar o quadro da Camada 2 entre dispositivos na mesma mídia compartilhada.
- **Detecção de erro** - Inclui um trailer usado para detectar erros de transmissão.

Comunicações full-duplex não exigem controle de acesso de mídia.

### 6.1.3 Fornecimento de Acesso ao Meio Físico
Em cada salto ao longo do caminho, um roteador executa as seguintes funções da Camada 2:
1. Aceita um quadro de um meio;
2. Desencapsula o quadro;
3. Encapsula novamente o pacote em um novo quadro;
4. Encaminha o novo quadro apropriado para o meio desse segmento da rede física.
### 6.1.4 Padrões da Camada de Enlace de Dados
As organizações de engenharia que definem padrões abertos e protocolos que se aplicam à camada de acesso à rede (ou seja, as camadas físicas e de link de dados OSI) incluem o seguinte:

- Institute of Electrical and Electronics Engineers (IEEE)
- International Telecommunication Union (ITU)
- International Organization for Standardization (ISO)
- Instituto Nacional Americano de Padronização (ANSI)
## 6.2 Topologias
### 6.2.1 Topologias Físicas e Lógicas
Existem dois tipos de topologias usadas ao descrever redes LAN e WAN:

- **Topologia física** - Identifica as conexões físicas e como os dispositivos finais e intermediários (ou seja, roteadores, comutadores e pontos de acesso sem fio) são interconectados. A topologia também pode incluir a localização específica do dispositivo, como o número do quarto e a localização no rack do equipamento. As topologias físicas são geralmente ponto a ponto ou estrela.
- **Topologia lógica** - refere-se à maneira como uma rede transfere quadros de um nó para o próximo. Esta topologia identifica conexões virtuais usando interfaces de dispositivo e esquemas de endereçamento IP da Camada 3.
### 6.2.2 As topologias de WAN
**Ponto a Ponto**
Esta é a topologia WAN mais simples e comum. Consiste em uma ligação permanente entre dois pontos finais.
**Estrela**
Esta é uma versão WAN da topologia em estrela na qual um site central interconecta sites de filial através do uso de links ponto a ponto. Os sites de filiais não podem trocar dados com outros sites de filiais sem passar pelo site central.
**Malha**
Essa topologia fornece alta disponibilidade, mas requer que todos os sistemas finais estejam interconectados a todos os outros sistemas. Portanto, os custos administrativos e físicos podem ser significativos. Cada link é essencialmente um link ponto a ponto para outro nó.

Um híbrido é uma variação ou combinação de qualquer topologia. Por exemplo, uma malha parcial é uma topologia híbrida em que alguns dispositivos finais, mas não todos, são interconectados.

### 6.2.3 Topologia de WAN ponto a ponto
Ao usar um protocolo de comunicação serial como o protocolo ponto a ponto (PPP), um nó não precisa determinar se um quadro de entrada é destinado a ele ou a outro nó. Portanto, os protocolos de enlace de dados podem ser muito simples, assim como todos os quadros no meio físico podem trafegar apenas para os dois nós ou a partir deles. O nó coloca os quadros na mídia em uma extremidade e esses quadros são retirados da mídia pelo nó na outra extremidade do circuito ponto a ponto.

Um nó de origem e destino pode ser indiretamente conectado entre si por alguma distância geográfica, usando vários dispositivos intermediários. No entanto, o uso de dispositivos físicos na rede não afeta a topologia lógica.

### 6.2.4 Topologias LAN
Em LANs multiacesso, os dispositivos finais (isto é, nós) são interligados usando topologias estelares ou estelares estendidas.

A **extended star** estende essa topologia interconectando vários switches Ethernet. As topologias em estrela e estendidas são fáceis de instalar, muito escalonáveis (fáceis de adicionar e remover dispositivos finais) e fáceis de solucionar problemas. As primeiras topologias em estrela interconectavam dispositivos finais usando hubs Ethernet.

**Topologia de redes Legadas**
As primeiras tecnologias Ethernet e Token Ring LAN legadas incluíam dois outros tipos de topologias:

- **Barramento** - Todos os sistemas finais são encadeados e terminados de alguma forma em cada extremidade. Os dispositivos de infraestrutura, como switches, não são necessários para interconectar os dispositivos finais. As redes Ethernet herdadas costumavam ser topologias de barramento usando cabos coaxiais, porque era barato e fácil de configurar.
- **Anel** - Os sistemas finais são conectados ao respectivo vizinho formando um anel. O anel não precisa ser terminado, ao contrário da topologia de barramento. As redes de interface de dados distribuídos de fibra herdada (FDDI) e Token Ring usavam topologias de anel.

### 6.2.5 Comunicação em half e full duplex
**Comunicação Half-duplex**
Ambos os dispositivos podem transmitir e receber no meio físico, mas não podem fazer isso simultaneamente. WLANs e topologias de barramento herdadas com hubs Ethernet usam o modo half-duplex
**Comunicação Full-duplex**
Ambos os dispositivos podem transmitir e receber simultaneamente na mídia compartilhada. A camada de enlace de dados supõe que o meio físico está disponível para transmissão para ambos os nós a qualquer momento. Os comutadores Ethernet operam no modo full-duplex por padrão.

É importante que duas interfaces interconectadas, como uma NIC de host e uma interface em um comutador Ethernet, operem usando o mesmo modo duplex. Caso contrário, haverá uma incompatibilidade de duplex que criará ineficiência e latência no link.

### 6.2.6 Métodos de controle de acesso
Uma rede multiacesso é uma rede que pode ter dois ou mais dispositivos finais tentando acessar a rede simultaneamente. Algumas redes multiacesso requerem regras para controlar como os dispositivos compartilham a mídia física. Existem dois métodos básicos de controle de acesso para meio físico compartilhado.
- Acesso baseado em contenção
- Acesso controlado

**Acesso baseado em Contenção**
Em redes multiacesso baseadas em contenção, todos os nós estão operando em half-duplex, competindo pelo uso do meio.
Exemplos de métodos de acesso baseados em contenção incluem o seguinte:
- Acesso múltiplo com detecção de colisão (CSMA/CD - Carrier Sense Multiple Access with Collision Detection) usado em LANs Ethernet de topologia de barramento herdada
- Acesso múltiplo por operadora com prevenção de colisão (CSMA / CA - Carrier sense multiple access with collision avoidance) usado em LANs sem fio
**Carrier sense multiple access with collision avoidance**
Em uma rede multiacesso controlada, cada nó tem seu próprio tempo para usar o meio. Esses tipos determinísticos de redes herdadas são ineficientes porque um dispositivo deve aguardar sua vez para acessar o meio. Exemplos de redes multiacesso que usam acesso controlado incluem o seguinte:
- Anel de token legados
- ARCNET legado

**Observação:** Atualmente, as redes Ethernet operam em full-duplex e não exigem um método de acesso.

### 6.2.7 Acesso baseado em contenção - CSMA / CD
Exemplos de redes de acesso baseadas em contenção incluem o seguinte:
- LAN sem fio (usa CSMA/CA)
- LAN Ethernet de topologia de barramento legado (usa CSMA/CD)
- LAN Ethernet legada usando um hub (usa CSMA/CD)
Essas redes operam no modo half-duplex.
Se dois dispositivos transmitirem simultaneamente, ocorre uma colisão. Para LANs Ethernet herdadas, ambos os dispositivos detectam a colisão na rede. Esta é a parte de detecção de colisão (CD) do CSMA/CD. A NIC compara os dados transmitidos com os dados recebidos ou reconhecendo que a amplitude do sinal é maior que o normal na mídia. Os dados enviados por ambos os dispositivos serão corrompidos e precisarão ser reenviados.

### 6.2.8 Acesso baseado em contenção - CSMA / CA
O CMSA/CA usa um método semelhante ao CSMA/CD para detectar se a mídia está livre. O CMSA / CA usa técnicas adicionais. Em ambientes sem fio pode não ser possível para um dispositivo detectar uma colisão. O CMSA/CA não detecta colisões, mas tenta evitá-las esperando antes de transmitir. Cada dispositivo que transmite inclui o tempo necessário para a transmissão. Todos os outros dispositivos sem fio recebem essas informações e sabem quanto tempo a mídia ficará indisponível.
Depois que um dispositivo sem fio enviar um quadro 802.11, o receptor retornará uma confirmação para que o remetente saiba que o quadro chegou.

Os sistemas baseados em contenção não escalam bem sob uso intenso.

**Observação:** As LANs Ethernet que usam comutadores não usam um sistema baseado em contenção porque o comutador e a NIC do host operam no modo full-duplex.

## 6.3 Quadro de Enlace de Dados
### 6.3.1 O Quadro
Cada tipo de quadro tem três partes básicas:
- Cabeçalho;
- Dados;
- Trailer.
Ao contrário de outros protocolos de encapsulamento, a camada de link de dados acrescenta informações na forma de um trailer no final do quadro.
Dependendo do ambiente, a quantidade de informações de controle necessária no quadro varia para corresponder às exigências de controle de acesso ao meio físico e à topologia lógica.

### 6.3.2 Campos do Quadro
Na ordem, esquerda para direita:
- Cabeçalho:
	- Início do quadro
	- Endereçamento - indica os nós de origem e destino na mídia.
	- Tipo - identifica o protocolo da camada 3 no campo de dados.
	- Controle - Identifica serviços especiais de controle de fluxo, como qualidade de serviço (QoS). A QoS dá prioridade ao encaminhamento para certos tipos de mensagens. Por exemplo, os quadros de voz sobre IP (VoIP) normalmente recebem prioridade porque são sensíveis ao atraso.
- Pacote (Dados)
	- Dados - Contém a carga útil do quadro (ou seja, cabeçalho do pacote, cabeçalho do segmento e os dados).
- Trailer
	- Detecção de erros - Incluído após os dados para formar o trailer.
	- Fim do quadro

Um nó de transmissão cria um resumo lógico dos conteúdos do quadro, conhecido como valor de verificação de redundância cíclica (cyclic redundancy check - CRC) Este valor é colocado no campo FCS (Sequência de Verificação de Quadro) para exibição ou conteúdo do quadro. No trailer Ethernet, o FCS fornece um método para o nó de recebimento determinar se o quadro apresentou erros de transmissão.

### 6.3.3 Endereços da camada 2
Os endereços de dispositivos nesta camada são chamados de endereços físicos.
O endereço físico é um endereço exclusivo do dispositivo específico. Um dispositivo ainda funcionará com o mesmo endereço físico da Camada 2, mesmo que o dispositivo se mova para outra rede ou sub-rede.

O endereço da camada de enlace de dados é usado apenas para entrega local.

### 6.3.4 Quadros de LAN e WAN