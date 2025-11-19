## 1.2 Componentes de rede
### 1.2.1 Funções do Host
Todos os computadores que estão conectados a uma rede e participam diretamente da comunicação em rede são classificados como hosts. Os hosts podem ser chamados de dispositivos finais.

### 1.2.2 Ponto a Ponto
Redes onde computadores funcionam como servidores e clientes na rede é chamado de rede ponto a ponto.
Vantagens:
- Fácil de configurar 
- Menos complexo
- Menor custo porque os dispositivos de rede e os servidores dedicados podem não ser necessários
- Pode ser usada para tarefas simples como transferir arquivos e compartilhar impressoras.

Desvantagens: 
- Nenhuma administração centralizada
- Não é tão segura
- Não é escalável
- Todos os dispositivos podem atuar como clientes e servidores, podendo deixar seu desempenho lento.

### 1.2.3 Dispositivos Finais
Um dispositivo final é a origem ou o destino de uma mensagem transmitida pela rede.

### 1.2.4 Dispositivos Intermediários
Dispositivos  intermediários  conectam os dispositivos finais individuais a rede.
(Roteadores, Switches, Firewalls, Hub).
Eles podem executar as seguintes funções:
- Regenerar e retransmitir sinais de comunicação;
- Manter informação sobre quais caminhos existem pela rede e pela rede interconectada;
- Notificar outros dispositivos sobre erros e falhas de comunicação
- Direcionar dados por caminhos alternativos quando houver falha em um link
- Classificar e direcionar mensagens de acordo com as prioridades
- Permitir ou negar o fluxo de dados, co base em configurações de segurança.

### 1.2.5 Meios de rede
Mídia que fornece o canal pelo qual a mensagem viaja da origem ao destino.
- Fios de metal dentro de cabos - Os dados são configurados em impulsos elétricos
- Fibras de vidro ou plastico nos cabos (cabo de fibra óptica) - Os dados são codificados em pulsos de luz/
- Transmissão sem fio - Os dados são codificados através da modulação de frequências especificas de ondas eletromagnéticas.

Quatro critérios para a escolha de mídia de rede são:
- Qual é a distancia máxima pela qual o meio físico consegue carregar um sinal com exito?
- Qual e o ambiente em que a mídia sera instalada?
- Qual é a quantidade de dados ea que velocidade dever transmitida?
- Qual é o custo do meio físico e da instalação?


## 1.3 Representações e topologias de rede
### 1.3.1 Representações de Rede
- Placa de interface de rede (NIC) - Uma NIC conecta fisicamente o dispositivo final a rede.
- Porta fisica - Um conector ou tomada em um dispositivo de rede onde a midia se conecta a um dispositivo final ou outro dispositivo de rede.
- Interface - Portas especializadas em um dispositivo de rede que se conectam a dredes individuais. Como os roteadores conectam redes, as portas em um roteador sao chamdas de interfaces de rede.
Obs: Os termos porta e interface são frequentemente usados alternadamente.
### 1.3.2 Diagramas de Topologia
Documentação obrigatória para qualquer pessoa que trabalhe com uma rede.
##### Diagramas de topologia física
Ilustram a localização física dos dispositivos intermediários e a instalação dos cabos.

##### Diagramas de topologia lógica
Ilustram dispositivos, portas e o esquema de endereçamento de rede.  Você pode ver quais dispositivos finais estão conectados a quais dispositivos intermediários e qual mídia esta sendo usada.

## 1.4 Tipos Comuns de redes
### 1.4.1 Redes de Vários Tamanhos
#### Redes domésticas pequenas
Conectam alguns computadores entre si e com internet.
#### Redes para pequenos escritórios e escritórios domesticos
Rede SOHO (Small Office, Home Office). Permitem que scritorio em casa ou um escritorio remoto se conectem a uma rede coporativa, ou acessem recursos compartilhados centralizados.

#### Redes médias a grandes
Usadas por empresas e escolar, podem ter muitos locais com centenas ou milhares de hosts interconectados.

#### Rede Global
A internet.

### 1.4.2 LANs e WANs
#### LANs
Uma LAN (Local Area Network) é uma infraestrutura de rede que abrange uma pequena área geográfica. As LANs tem características especificas:
- LANs interconectam dispositivos finais em uma área limitada, como uma casa, uma escola, um edifício de escritórios ou um campus.
- Uma LAN é geralmente administrada por uma única organização ou pessoa. O controle administrativo é imposto no nível da rede e governa as políticas de segurança e controle de acesso.
- As LANs fornecem largura de banda de alta velocidade para dispositivos finais internos e dispositivos intermediários, conforme mostrado na figura.
Uma rede que atende uma casa, prédio pequeno ou campus pequeno é considerada uma LAN

#### WANs
Uma WAN (Wide Area Network) é uma infraestrutura de rede que abrange uma ampla área geográfica. As WANs geralmente são gerenciadas por provedores de serviços (SPs) ou provedores de serviços de Internet (ISPs).
As WANs tem características especificas:
- As WANs interconectam as LANs em grandes areas geográficas, como entre cidades, estados, províncias, países ou continentes.
- As WANs são geralmente administradas por vários prestadores de serviço
- As WANs geralmente fornecem links de velocidade mais lenta entre as LANs.


### 1.4.3 A Internet 
A internet é uma coleção mundial de redes interconectadas (inter-networks, ou internet para abreviar).  
*As LANs usam serviços WAN para se interconectarem*

A internet não é propriedade de nenhum individuo ou grupo.
Organizações que ajudam a manter a estrutura e a padronização de protocolos e processos da internet. 
- Internet Engineering Task Force (IETF)
- Internet Corporation for Assigned Names and Numbers (ICANN)
- Internet Architecture Board (IAB)
- Internet Assigned Numbers Authority (IANA)

### 1.4.4 Intranets e Extranets
A intranet e um termo usado para se referir a uma conexão privada de LANs e WANs que pertence a uma organização.
Uma organização pode usar uma extranet para fornecer acesso seguro e protegido a indivíduos que trabalham para um organização diferente, mas exigem acesso aos dados da organização.

| Internet | Extranet                              | Intranet         |
| -------- | ------------------------------------- | ---------------- |
| O mundo  | Fornecedores, clientes, colaboradores | Apenas a Empresa |
## 1.5 Conexões com a Internet
### 1.5.1 Tecnologias de Acesso a Internet
Banda larga a cabo, banda larga via digital subscriber line (DSL), WANs sem fio e serviços de telefonia móvel celular. Para empresas, DSL, linhas dedicadas, Metro Ethernet.

### 1.5.2 Conexões com a Internet para Residencias e Pequenos escritórios.
- Cabo - Normalmente oferecido por provedores de serviços de televisão a cabo, o sinal de internet transmite no mesmo cabo que fornece televisão a cabo. Fornece alta largura de banda, alta disponibilidade e uma conexão sempre ativa a internet.
- DSL - Linhas de assinante digital também fornecem alta largura de banda, alta disponibilidade e uma conexão sempre ativa. O DSL funciona utilizando a linha telefônica. Em geral é usado o DSL Assimétrico (ADSL), onde a velocidade de download é maior que a de upload
- Celular - Usa uma rede de telefonia celular para se conectar. Limitado pelos recursos do telefone e da torre de celular onde esta conectado.
- Satélite - Beneficio nas areas que outras formas não teriam conectividade com a internet. Antena exige visão clara para o satélite.
- Conexão Discada (Dial-Up) - opção de baixo custo que usa qualquer linha telefônica e um modem, Baixa largura de banda, embora util para acesso móvel durante a viagem.

### 1.5.3 Conexões Corporativas com a Internet
- Linha Alugada Dedicada - As linhas alugadas são circuitos reservados na rede do provedor de serviços que conectam escritórios geograficamente separados para redes privadas de voz e / ou dados. Os circuitos são alugados a uma taxa mensal ou anual.
- Metro Ethernet - Ethernet WAN. Ethernet metropolitanas estendem a tecnologia de acesso á LAN na WAN.
- DSL de negócios - linha de assinante digital simétrica (SDSL), fornece upload e download nas mesmas velocidades
- Satélite.

### 1.5.4 A Rede Convergente
#### Redes Separadas Tradicionais 
Um meio para cada tipo de comunicação (telefone, internet, televisão, etc.)
#### Redes Convergentes
Tipos diferentes de comunicações compartilham o mesmo meio.

## 1.6  Redes Confiáveis 
### 1.6.1 Arquitetura de Redes
Elas devem atender:
- Tolerância a falhas;
- Escalabilidade;
- Qualidade de serviço (QoS);
- Segurança.
### 1.6.2 Tolerância a Falhas
Uma rede tolerante a falhas é aquela que limita o número de dispositivos afetados durante uma falha. Recuperação rápida. Caminhos redundantes.
### 1.6.3 Escalabilidade
Uma rede escalável se expande rapidamente para oferecer suporte a novos usuários e aplicativos. Ele faz isso sem degradar o desempenho dos serviços que estão sendo acessados por usuários existentes.
### 1.6.4 Qualidade do Serviço
Uma rede onde o não há congestionamento e alta largura de banda.
### 1.6.5 Segurança da Rede
Proteger a infraestrutura de rede inclui proteger fisicamente os dispositivos que fornecem conectividade de rede e impedir o acesso não autorizado ao software de gerenciamento que reside neles
Requisitos:
- Confidencialidade
- Integridade
- Disponibilidade

## 1.7 Tendências das redes
### 1.7.1 Tendências recentes
### 1.7.2 Traga seu próprio dispositivo (BYOD)
### 1.7.3 Colaboração On-line
A colaboração é definida como o ato de trabalho com outro ou outros em um projeto em parceria. 
A colaboração é uma prioridade crítica e estratégica que as organizações estão usando para permanecer competitivas. A colaboração também é uma prioridade na educação.
### 1.7.4 Comunicações em vídeo
O vídeo é usado para comunicação, colaboração e entretenimento. Chamadas de video são feitas de e para qualquer pessoa com uma conexão e Internet, independentemente de onde elas estão localizadas.
### 1.7.6 Computação em nuvem
A computação em nuvem nos permite armazenar arquivos pessoais, até fazer backup de uma unidade inteira em servidores pela Internet. A computação em nuvem amplia os recursos de TI sem exigir investimento em nova infraestrutura, treinamento de novas equipes ou licenciamento de novo software.
A computação em nuvem é possível devido aos data centers.

**Cloud Types:**

| Tipo de nuvem       | Descricao                                                                                                                                                                                                                                                                                                                                                        |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Nuvem publica       | Recursos em uma nuvem publica são disponíveis para a população em geral, podem ser gratuitos ou em modelo de pagamento por uso, como armazenamento on-line.                                                                                                                                                                                                      |
| Nuvem privada       | Recursos destinados a uma entidade especifica. Pode ser gerenciada por uma organização externa com acesso estrito de segurança.                                                                                                                                                                                                                                  |
| Nuvens Hibridas     | Composta por duas ou mais nuvens (exemplo: parte privada, parte publica), onde cada parte permanece em objeto distinto, mas ambos são conectado usando uma unica arquitetura                                                                                                                                                                                     |
| Nuvens comunitárias | Criada para uso exclusivo por entidades ou organizações. A diferença entre a nuvem publica é que nuvem comunitárias são as necessidades funcionais que forma personalizadas para a comunidade. Por exemplo, organizações de saúde devem manter a HIPAA. AS nuvem comunitárias são usadas por varias organizações que tem necessidades e preocupações semelhantes |
### 1.7.7 Tendencias Tecnológicas em Casa
IOT.
### 1.7.8 Rede Powerline
A rede Powerline para redes domésticas usa a fiação elétrica existente para conectar dispositivos,
Usando um adaptador padrão powerline, os dispositivos podem se conectar a LAN onde quer que haja uma tomada elétrica. Nenhum cabo de dados precisa ser instalado, e há pouca ou nenhuma eletricidade adicional usada. Usando a mesma fiação que fornece a eletricidade, a rede powerline envia informações ao enviar dados em determinadas frequências. A rede Powerline é especialmente útil quando os pontos de acesso sem fio não conseguem alcançar todos os dispositivos em casa. A rede Powerline não substitui o cabeamento dedicado em redes de dados. 

### 1.7.9 Banda Larga Sem Fio
**Provedor de serviços de Internet sem fio**
Um provedor de serviços de Internet sem fio (WISP) é um provedor de serviços de Internet que conecta assinantes a um ponto de acesso ou hot spot designado usando tecnologias sem fio semelhantes encontradas em redes locais sem fio domésticas (WLANs). Os WISPs são mais comumente encontrados em ambientes rurais onde DSL ou serviços a cabo não estão disponíveis.
Uma antena parabólica pequena ou grande é instalada no teto do assinante dentro do alcance do transmissor WISP. A unidade de acesso do assinante é conectada à rede com fio dentro de casa. Da perspectiva de usuário doméstico, a configuração não é muito diferente do serviço de cabo ou DSL.

**Serviços de banda larga sem fio**
Outra solução sem fio para casas e pequenas empresas é a banda larga sem fio.
Esta solução usa a mesma tecnologia celular que um telefone inteligente. Uma antena é instalada fora da residência, fornecendo conectividade com ou sem fio para dispositivos na casa. Em muitas áreas, a banda larga sem fio doméstica estão competindo diretamente com serviços DSL e a cabo.

## 1.8 Segurança de Redes
### 1.8.1 Ameaças à Segurança
- Vírus, worms e cavalos de Troia  - Eles contém software ou código malicioso em execução no dispositivo do usuário.
- Spyware e adware - Estes são tipos de software que são instalados no dispositivo de um usuário. O software, em seguida, coleta secretamente informações sobre o usuário.
- Ataques de dia zero - Também chamados de ataques de hora zero, ocorrem no primeiro dia em que uma vulnerabilidade se torna conhecida.
- Ataques de ator de ameaça - Uma pessoa mal-intencionada ataca dispositivos de usuário ou recursos de rede.
- Ataques de negação de serviço - Esses ataques atrasam ou travam aplicativos e processos em um dispositivo de rede.
- Interceptação de dados e roubo - Esse ataque captura informações privadas da rede de uma organização.  
- Roubo de identidade- Esse ataque rouba as credenciais de login de um usu�rio para acessar informações privadas.
### 1.8.2 Soluções de Segurança
Estes são os componentes básicos de segurança para uma rede doméstica ou de pequeno escritório:
- Antivirus e antispyware - Esses aplicativos ajudam a proteger os dispositivos finais contra a infecção por software malicioso.
- Filtragem por firewall - A filtragem por firewall bloqueia o acesso não autorizado dentro e fora da rede. Isso pode incluir um sistema de firewall baseado em host que impede o acesso não autorizado ao dispositivo final ou um serviço básico de filtragem no roteador doméstico para impedir o acesso não autorizado do mundo externo à rede.
Redes maiores e redes corporativas usam antivírus, antispyware e filtragem por firewall, mas também têm outros requisitos de segurança:
- Sistemas de firewall dedicados - Eles fornecem recursos de firewall mais avançados que podem filtrar grandes quantidades de tráfego com mais granularidade.
- Listas de controle de acesso (ACL) - Eles filtram ainda mais o acesso e o encaminhamento de tráfego com base em endereços e aplicativos IP.
- Sistemas de prevenção de intrusões (IPS) - Identificam ameaças de rápida disseminação, como ataques de dia zero ou hora zero.
- Redes privadas virtuais (VPN) - Fornecem acesso seguro a uma organização para trabalhadores remotos.