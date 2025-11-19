## 4.1 Propósito da camada física
Uma conexão física pode ser uma conexão com fio usando um cabo ou uma conexão sem fio usando ondas de rádio. O tipo de conexão física usada depende da configuração da rede.
### 4.1.1 A conexão física
#### Roteador Sem Fio
Estes são os componentes de um ponto de acesso:
1. As antenas sem fio (Elas estão incorporadas dentro da versão do roteador mostrada na figura acima.);
2. Várias portas de comutação Ethernet;
3. Uma porta de internet.
#### Conexão com fio ao roteador sem fio
**Placas de Interface de Rede**
As placas de interface de rede (NICs) conectam um dispositivo à rede. As NICs Ethernet são usadas para uma conexão com fio, enquanto as NICs da rede local sem fio (WLAN) são usadas para a conexão sem fio.
Um dispositivo de usuário final pode incluir um ou os dois tipos de NICs.

#### Conexão com fio usando uma NIC Ethernet
Nem todas as conexões físicas são iguais, em termos de nível de desempenho, durante uma conexão com uma rede.

### 4.1.2 A Camada Física
A camada física do modelo OSI fornece os meios para transportar os bits que formam um quadro da camada de enlace de dados no meio físico de rede. Esses sinais são então enviados pela mídia, um de cada vez.
A camada física do nó destino recupera esses sinais individuais do meio físico, restaura-os às suas representações de bits e passa os bits para a camada de enlace de dados como um quadro completo.

## 4.2 Características da camada física
### 4.2.1 Padrões da Camada Física
Os protocolos e operações das camadas OSI superiores são executados usando software desenvolvido por engenheiros de software e cientistas da computação. Os serviços e protocolos na suíte TCP/IP são definidos pela Internet Engineering Task Force (IETF).

Os padrões de hardware, mídia, codificação e sinalização da camada física são definidos e governados por essas organizações de padrões (Física e Enlace de Dados):

- International Organization for Standardization (ISO)
- Telecommunications Industry Association/Electronic Industries Association (TIA/EIA)
- União Internacional de Telecomunicações (ITU)
- Instituto Nacional de Padronização Americano (ANSI)
- Institute of Electrical and Electronics Engineers (IEEE)
- Autoridades reguladoras de telecomunicações nacionais, incluem Federal Communication Commission (FCC) nos EUA e European Telecommunications Standards Institute (ETSI)

Além desses, geralmente existem grupos regionais de padrões de cabeamento, como CSA (Canadian Standards Association), CENELEC (Comitê Europeu de Padronização Eletrotécnica) e JSA / JIS (Japanese Standards Association), que desenvolvem especificações locais.

### 4.2.2 Componentes Físicos
Os padrões da camada física abordam três áreas funcionais:
- Componentes Físicos;
- Codificação;
- Sinalização.
#### Componentes Físicos
Os componentes físicos são os dispositivos de hardware eletrônico, mídia e outros conectores que transmitem os sinais que representam os bits. Os componentes de hardware, como NICs, interfaces e conectores, materiais de cabo e projetos de cabo são especificados nos padrões associados à camada física.

### 4.2.3 Codificação
A codificação ou codificação de linha é um método para converter um fluxo de bits de dados em um "código” predefinido. Os códigos são agrupamentos de bits usados para fornecer um padrão previsível que pode ser reconhecido tanto pelo emissor quanto pelo receptor.
Por exemplo, a codificação Manchester representa um bit 0 por uma transição de alta para baixa voltagem, e um bit 1 é representado como uma transição de baixa para alta voltagem. A transição ocorre no meio de cada período de bit.

Esse tipo de codificação é usado na Ethernet de 10 Mbps. Taxas de dados mais rápidas exigem uma codificação mais complexa. A codificação Manchester é usada em padrões Ethernet mais antigos, como o 10BASE-T. A Ethernet 100BASE-TX usa codificação 4B / 5B e 1000BASE-T usa codificação 8B / 10B.

### 4.2.4 Sinalização
A camada física deve gerar os sinais elétricos, ópticos ou sem fio que representam os valores “1” e “0” no meio físico. A maneira como os bits são representados é chamada de método de sinalização.

### 4.2.5 Largura de Banda
Largura de banda é a capacidade na qual um meio pode transportar dados.
A largura de banda digital mede a quantidade de dados que podem fluir de um lugar para outro durante um determinado tempo.
A largura de banda é normalmente medida em kilobits por segundo (kbps), megabits por segundo (Mbps) ou gigabits por segundo (Gbps).
### 4.2.6 Terminologia de largura de banda
Os termos usados para medir a qualidade da largura de banda incluem:
- Latência;
- Rendimento;
- Dados úteis.
#### **Latência**
O termo latência se refere ao tempo necessário para os dados viajarem de um ponto a outro, incluindo atrasos.

A taxa de transferência não pode ser mais rápida que o link mais lento no caminho da origem ao destino. Mesmo que todos ou a maioria dos segmentos tenham alta largura de banda, será necessário apenas um segmento no caminho com baixa taxa de transferência para criar um gargalo na taxa de transferência de toda a rede.

#### **Taxa de transferência**
Taxa de transferência é a medida da transferência de bits através da mídia durante um determinado período.
A taxa de transferência geralmente é menor que a largura de banda. Existem muitos fatores que influenciam a taxa de transferência:
- A quantidade de tráfego;
- O tipo de tráfego;
- A latência criada pelo número de dispositivos de rede encontrados entre a origem e o destino.

#### **Dados úteis**
Goodput é a medida de dados usáveis transferidos em um determinado período. Goodput é a taxa de transferência menos a sobrecarga de tráfego para estabelecer sessões, reconhecimentos, encapsulamento e bits retransmitidos. O goodput é sempre menor que a taxa de transferência, que geralmente é menor do que a largura de banda.

## 4.3 Cabeamento de Cobre
### 4.3.1 Características do Cabeamento de Cobre
O cabeamento de cobre é o tipo mais comum de cabeamento usado nas redes hoje em dia.
Existem três tipos diferentes de cabeamento de cobre que são usados em situações específicas.

As redes usam mídia de cobre porque é barata, fácil de instalar e tem baixa resistência à corrente elétrica. Entretanto, ela é limitada pela distância e interferência de sinal.

Quanto mais o sinal viaja, mais ele se deteriora. Isso se chama atenuação de sinal. Por isso, todas as mídias de cobre devem seguir limitações de distância rigorosas, conforme especificado nos padrões de orientação.

A temporização e a voltagem dos pulsos elétricos também são suscetíveis à interferência de duas fontes:
- **Interferência eletromagnética (EMI) ou interferência de radiofrequência (RFI)** - Os sinais EMI e RFI podem distorcer e corromper os sinais de dados que estão sendo transportados pela mídia de cobre. Possíveis fontes de EMI e RFI são dispositivos de ondas de rádio e eletromagnéticos, como luzes fluorescentes ou motores elétricos.
- **Diafonia** - Diafonia é uma perturbação causada pelos campos elétrico ou magnético de um sinal em um fio para o sinal em um fio adjacente. Nos circuitos de telefone, a diafonia pode fazer com que parte de outra conversa de voz de um circuito adjacente seja ouvida (linha cruzada). Especificamente, quando uma corrente elétrica flui através de um cabo, ela cria um pequeno campo magnético circular ao redor do cabo, que pode ser captado por um cabo adjacente.
Para contrabalançar os efeitos negativos da EMI e da RFI, alguns tipos de cabos de cobre têm proteção metálica e exigem conexões devidamente aterradas.

Para contrabalançar os efeitos negativos do crosstalk, alguns tipos de cabos de cobre têm pares de cabos de circuitos opostos juntos, o que efetivamente cancela o crosstalk.

A suscetibilidade dos cabos de cobre ao ruído eletrônico também pode ser limitada usando estas recomendações:

- Selecionando o tipo ou categoria de cabo mais adequado para um determinado ambiente de rede
- Projetar uma infraestrutura de cabos para evitar fontes conhecidas e potenciais de interferência na estrutura do edifício
- Usando técnicas de cabeamento que incluem o manuseio e a terminação adequados dos cabos
### 4.3.2 Tipos de cabeamento de cobre
Há três tipos principais de mídias de cobre usadas em redes.
- Cabo de par trançado não blindado (UTP)
- Cabo de Pares Trançados Blindados (STP)
- Cabo Coaxial
### 4.3.3 Par trançado não blindado (UTP)
O cabeamento de par trançado não blindado (UTP) é o meio físico de rede mais comum. O cabeamento UTP, terminado com conectores RJ-45, é usado para interconectar hosts de rede com dispositivos de rede intermediários, como comutadores e roteadores.

Nas LANs, o cabo UTP consiste em quatro pares de cabos codificados por cores que foram trançados e depois colocados em uma capa plástica flexível que protege contra danos físicos menores. O processo de trançar cabos ajuda na proteção contra interferência de sinais de outros cabos.

### 4.3.4 Par trançado blindado (STP)
O par trançado blindado (STP) oferece maior proteção contra ruído do que o cabeamento UTP. No entanto, em comparação com o cabo UTP, o cabo STP é significativamente mais caro e difícil instalação. Assim como o cabo UTP, o STP usa um conector RJ-45.

Os cabos STP combinam as técnicas de blindagem para contrabalançar a EMI e a RFI, e são trançados para conter o crosstalk. Para aproveitar totalmente a blindagem, os cabos STP são terminados com conectores de dados STP blindados especiais. Se o cabo não estiver devidamente aterrado, a blindagem poderá atuar como uma antena e captar sinais indesejados.

### 4.3.5 Cabo coaxial
O cabo coaxial, ou coax para abreviar, recebeu seu nome porque tem dois condutores que compartilham o mesmo eixo.
- Um condutor de cobre é usado para transmitir os sinais eletrônicos.
- Uma camada de isolamento plástico flexível envolve um condutor de cobre.
- O material de isolamento é envolvido em uma malha de cobre com tecido, ou uma folha metálica, que atua como o segundo cabo no circuito e uma proteção para o condutor interno. Essa segunda camada, ou blindagem, também reduz a quantidade de interferência eletromagnética externa.
- Todo o cabo é coberto com um revestimento para evitar danos físicos menores.
Há tipos diferentes de conectores utilizados com o cabo coax. Os conectores Bayonet Neill-Concelman (BNC), tipo N e tipo F.

Embora o cabo UTP tenha substituído essencialmente o cabo coaxial nas modernas instalações Ethernet, o design do cabo coaxial é usado nas seguintes situações:

- **Instalações sem fio** - Os cabos coaxiais conectam antenas a dispositivos sem fio. O cabo coaxial transporta a energia de radiofrequência (RF) entre as antenas e o equipamento de rádio.
- **Instalações de Internet a cabo** - Os provedores de serviços a cabo fornecem conectividade à Internet para seus clientes, substituindo partes do cabo coaxial e suportando elementos de amplificação por cabo de fibra óptica. No entanto, o cabeamento dentro das instalações do cliente ainda é coaxial.
## 4.4 Cabeamento UTP
### 4.4.1 Propriedades do Cabo UTP

O cabo UTP não usa blindagem para contrabalançar os efeitos de EMI e RFI. Em vez disso, os projetistas de cabos descobriram outras maneiras de limitar o efeito negativo da diafonia:

- **Cancelamento** - os designers agora emparelham os fios em um circuito. Quando dois fios de um circuito elétrico são colocados próximos um do outro, seus campos magnéticos serão opostos. Assim, os dois campos magnéticos cancelam um ao outro e também podem cancelar sinais externos de EMI e RFI.
- **Variando o número de torções por par de fios** - Para aumentar ainda mais o efeito de cancelamento de fios de circuito emparelhados, os projetistas variam o número de torções de cada par de fios em um cabo. O cabo UTP deve seguir especificações precisas que orientam quantas tranças são permitidas por metro (3,28 pés) do cabo. Observe na figura que o par laranja/laranja e branco é menos trançado do que o par azul/azul e branco. Cada par colorido é trançado um número de vezes diferente.
O cabo UTP depende exclusivamente do efeito de cancelamento produzido pelos pares de fios trançados para limitar a degradação de sinal e fornecer efetivamente a autoblindagem para cabos trançados na mídia de rede.

### 4.4.2 Padrões e conectores de cabeamento UTP
O cabeamento de UTP está em conformidade com os padrões estabelecidos conjuntamente pela TIA/EIA. Especificamente, o TIA/EIA-568 estipula os padrões de cabeamento comerciais para instalações de LAN e é o padrão mais usado em ambientes de cabeamento de LAN. Alguns dos elementos definidos são os seguintes:

- Tipos de cabos;
- Comprimentos do cabo;
- Conectores;
- Terminação de cabo;
- Métodos de teste de cabo.
As características elétricas do cabeamento de cobre são definidas pelo Instituto de Engenharia Elétrica e Eletrônica (IEEE). IEEE classifica o cabeamento UTP de acordo com o desempenho. Por exemplo, o cabo Categoria 5 é usado normalmente em instalações 100BASE-TX Fast Ethernet.

- A categoria 3 foi originalmente utilizada para comunicação de voz através de linhas de voz, mas mais tarde utilizada para transmissão de dados.
- As categorias 5 e 5e são utilizadas para a transmissão de dados. Categoria 5 suporta 100Mbps e Categoria 5e suporta 1000 Mbps.
- A categoria 6 tem um separador adicional entre cada par de fios para suportar velocidades mais altas. Categoria 6 suporta até 10 Gbps.
- Categoria 7 também suporta 10 Gbps.
- Categoria 8 suporta 40 Gbps.
O cabo UTP geralmente é terminado com um conector RJ-45. O padrão TIA/EIA-568 descreve os códigos de cores de cabos para atribuições dos pinos (pinagem) para cabos Ethernet.

### 4.4.3 Cabos UTP diretos e cruzados
Estes são os principais tipos de cabo obtidos com o uso de convenções de cabeamento específicas:
- **Ethernet direta** - O tipo mais comum de cabo de rede. Geralmente é usado para interconectar um host a um switch e um switch a um roteador.
- **Ethernet Crossover** - Um cabo usado para interconectar dispositivos semelhantes. Por exemplo, para conectar um switch a um switch, um host a um host ou um roteador a um roteador. No entanto, os cabos cruzados agora são considerados legados, pois as NICs usam o cruzamento de interface dependente médio (Auto-MDIX) para detectar automaticamente o tipo de cabo e fazer a conexão interna.
**Observação:** Outro tipo de cabo é um cabo de rollover, que é proprietário da Cisco. É usado para conectar uma estação de trabalho a uma porta do console do roteador ou do switch.

### T568A and T568B Standards
![[Pasted image 20251118211011.png]]

## 4.5 Cabeamento de Fibra Óptica
### 4.5.1 Propriedades do Cabeamento de Fibra Óptica
A fibra óptica é um fio flexível, extremamente fino e transparente de vidro muito puro, não muito maior do que um fio de cabelo humano. Os bits são codificados na fibra como pulsos de luz.

### 4.5.2 Tipos de Fibra
Os cabos de fibra óptica são amplamente classificados em dois tipos:

- Fibra monomodo (SMF)
- Fibra multimodo (MMF)

##### **Fibra monomodo**
O SMF (Single Mode Fiber) consiste em um núcleo muito pequeno (9 mícrons) e usa a tecnologia laser cara para enviar um único raio de luz, conforme mostrado na figura. O SMF é popular em situações de longa distância que se estendem por centenas de quilômetros, como os exigidos em aplicações de telefonia de longo curso e TV a cabo.

##### **Fibra multimodo**
O MMF consiste em um núcleo maior (50/62,5 mícrons) e usa emissores de LED para enviar pulsos de luz. Especificamente, a luz de um LED entra na fibra multimodo em diferentes ângulos, como mostrado na figura. Popular nas LANs porque pode ser acionada por LEDs de baixo custo. Ela fornece largura de banda até 10 Gb/s por links de até 550 metros.

Uma das diferenças destacadas entre MMF e SMF é a quantidade de dispersão. O termo dispersão se refere ao espalhamento do pulso de luz com o tempo. Maior dispersão significa aumento da perda de força do sinal.

### 4.5.3 Uso de cabeamento de fibra óptica
Agora, o cabeamento de fibra óptica é usado em quatro setores:

- **Redes corporativas** - Usadas para aplicativos de cabeamento de backbone e dispositivos de infraestrutura de interconexão.
- **FTTH (Fiber-to-the-Home)** - Usado para fornecer serviços de banda larga sempre ativos para residências e pequenas empresas.
- **Redes de longo curso** - Utilizadas por provedores de serviços para conectar países e cidades.
- **Redes de cabos submarinos** - Utilizadas para fornecer soluções confiáveis de alta velocidade e alta capacidade, capazes de sobreviver em ambientes submarinos adversos até distâncias transoceânicas. Pesquise na internet por “mapa de telegeografia de cabos submarinos” para visualizar vários mapas on-line.
### 4.5.4 Conectores de Fibra Óptica
Alguns switches e roteadores têm portas que suportam conectores de fibra óptica por meio de um transceptor SFP (Small Form Factor Pluggable). Pesquise na internet para vários tipos de SFPs.
#### Conectores de ponta Reta (Straight-Tip - ST)
Os conectores ST foram um dos primeiros tipos de conectores usados. O conector trava firmemente com um mecanismo do tipo baioneta “Twist-on / twist-off”.
#### Conectores SC (Conectores de Assinante)
Às vezes, os conectores SC são chamados de conector quadrado ou conector padrão. Eles são um conector LAN e WAN amplamente adotado que usa um mecanismo push-pull para garantir uma inserção positiva. Esse tipo de conector é usado com fibra multimodo e monomodo.

#### Conectores Lucent (LC) SImplex
Os conectores LC simplex são uma versão menor do conector SC. Às vezes, eles são chamados de conectores pequenos ou locais e estão crescendo rapidamente em popularidade devido ao seu tamanho menor.

#### Conectores LC Duplex, Multimodo
Um conector LC multimodo duplex é semelhante a um conector LC simples, mas usa um conector duplex.

Alguns conectores de fibra aceitam fibras de transmissão e de recepção em um único conector, conhecido como conector duplex. Padrões BX, como 100BASE-BX, usam comprimentos de onda diferentes para enviar e receber através de uma única fibra.
### 4.5.5 Cabos de conexão de fibra
Os cabos de fibra são necessários para interconectar dispositivos da infraestrutura. O uso das cores diferencia entre cabos monomodo e multimodo. A cor amarela indica cabos de fibra monomodo e o laranja é para cabos de fibra multimodo.
**Observação:** Os cabos de fibra devem ser protegidos com uma pequena tampa de plástico quando não estiverem em uso.
- Cabo multimodo SC-SC
- Cabo multimodo ST-LC
- Cabo monomodo LC-LC
- Cabo monomodo SC-ST
### 4 .5.6 Fibra Versus Cobre
Atualmente, na maioria dos ambientes empresariais, a fibra óptica é usada principalmente como cabeamento de backbone para conexões ponto a ponto de alto tráfego entre instalações de distribuição de dados. Ele também é usado para a interconexão de edifícios em campus multi-construção. Como os cabos de fibra ótica não conduzem eletricidade e têm uma baixa perda de sinal, eles são adequados para esses usos.

| Problemas de implementação                                          | Cabeamento UTP                | Cabeamento de fibra óptica               |
| ------------------------------------------------------------------- | ----------------------------- | ---------------------------------------- |
| Largura de banda suportada                                          | 10 Mb/s - 10 Gb/s             | 10 Mb/s - 100 Gb/s                       |
| Distância                                                           | Relativamente curto (1 a 100) | Relativamente longo (1 - 100.000 metros) |
| Imunidade a interferência eletromagnética e de frequências de rádio | Baixa                         | Alto (totalmente imune)                  |
| Imunidade a perigos elétricos                                       | Baixa                         | Alto (totalmente imune)                  |
| Custos da mídia e dos conectores                                    | Menor                         | Mais alta                                |
| Habilidades necessárias para a instalação                           | Menor                         | Mais alta                                |
| Precauções de segurança                                             | Menor                         | Mais alta                                |
## 4.6 Meios sem Fio
### 4.6.1 Propriedades do Meio Físico Sem Fio
O meio físico sem fio transporta sinais eletromagnéticos que representam os dígitos binários de comunicações de dados usando frequências de rádio ou de micro-ondas.
Estas são algumas das limitações da rede sem fio:

- **Área de cobertura** - As tecnologias de comunicação de dados sem fio funcionam bem em ambientes abertos. No entanto, alguns materiais de construção utilizados em prédios e estruturas, e o terreno local, limitarão a eficácia da cobertura.
- **Interferência** - A conexão sem fio é suscetível a interferências e pode ser interrompida por dispositivos comuns, como telefones sem fio domésticos, alguns tipos de luzes fluorescentes, fornos de microondas e outras comunicações sem fio.
- **Segurança** - A cobertura de comunicação sem fio não requer acesso a uma parte física da mídia. Portanto, os dispositivos e usuários que não estão autorizados a acessar a rede podem obter acesso à transmissão. A segurança da rede é o principal componente da administração de uma rede sem fio.
- **AS WLANs e os meios compartilhados Cabos de conexão de fibra** - Operam em half-duplex, o que significa que apenas um dispositivo pode enviar ou receber por vez. O meio sem fio é compartilhado com todos os usuários sem fio. Muitos usuários acessando a WLAN simultaneamente resultam em largura de banda reduzida para cada usuário.
### 4.6.2 Tipos de Meio Físico Sem Fio
Em cada um dos padrões, as especificações da camada física são aplicadas a áreas que incluem o seguinte:

- Codificação de dados para sinal de rádio;
- Frequência e potência de transmissão;
- Requisitos de recepção e decodificação de sinal;
- Projeto e construção de antenas.

Estes são os padrões sem fio:
- **Wi-Fi (IEEE 802.11)** - Tecnologia de LAN sem fio (WLAN), geralmente chamada de Wi-Fi. A WLAN usa um protocolo baseado em contenção conhecido como acesso múltiplo / detecção de colisão de portadora (CSMA / CA). A NIC sem fio deve ouvir primeiro, antes de transmitir, para determinar se o canal de rádio está limpo. Se houver outro dispositivo sem fio transmitindo, a NIC deverá esperar até o canal estar limpo. Wi-Fi é uma marca comercial registrada da Wi-Fi Alliance. O Wi-Fi é usado com dispositivos WLAN certificados com base nos padrões IEEE 802.11.
- **Bluetooth (IEEE 802.15)** - Este é um padrão de rede pessoal sem fio (WPAN), comumente conhecido como “Bluetooth”. Ele usa um processo de emparelhamento de dispositivo para se comunicar em distâncias de 1 a 100 metros.
- **WiMAX (IEEE 802.16)** - Comumente conhecido como Interoperabilidade mundial para acesso por microondas (WiMAX), esse padrão sem fio usa uma topologia ponto a multiponto para fornecer acesso à banda larga sem fio.
- **Zigbee (IEEE 802.15.4)** - Zigbee é uma especificação usada para comunicações de baixa taxa de dados e baixa potência. Destina-se a aplicações que exigem taxas de dados de curto alcance, baixas e longa duração da bateria. Zigbee é normalmente usado para ambientes industriais e de Internet das Coisas (IoT), como interruptores de luz sem fio e coleta de dados de dispositivos médicos.
### 4.6.3 LAN Sem Fio
Em geral, uma WLAN requer os seguintes dispositivos de rede:

- **Ponto de acesso sem fio (AP)** - Estes concentram os sinais sem fio dos usuários e se conectam à infraestrutura de rede existente baseada em cobre, como Ethernet. Os roteadores sem fio domésticos e de pequenas empresas integram as funções de um roteador, comutador e ponto de acesso em um dispositivo, conforme mostrado na figura.
- **Adaptadores de NIC sem fio** - fornecem recursos de comunicação sem fio para hosts de rede.