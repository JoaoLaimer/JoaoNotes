## 2.1 Acesso ao [[Cisco IOS]]
### 2.1.1 Sistemas Operacionais
Todos os dispositivos finais e de rede exigem um sistema operacional (SO).  
- **Shell** - A interface de usuário que permite que os usuários solicitem tarefas ao computador. CLI ou GUI
- **Kernel** - Comunica-se entre o hardware e software e gerencia recursos de hardware.
- **Hardware** - Parte física.  
A CLI requer muito pouca sobrecarga para operar. No entanto, exige que o usuário tenha conhecimento da estrutura de comando subjacente que controla o sistema.
### 2.1.2 GUI 
Graphic User Interface como Windows, macOS, Linux KDE, Apple iOS ou Android permite que o usuário interaja com o sistema usando um ambiente de ícones gráficos, menus e janelas.
As GUIs também podem falhar, congelar ou simplesmente não funcionar como especificado. Por esses motivos, os dispositivos de rede geralmente são acessados por meio de uma CLI.

O sistema operacional nos roteadores domésticos geralmente é chamado firmware.

A família de sistemas operacionais de rede usados em muitos dispositivos Cisco é denominada Cisco Internetwork Operating System (IOS). O Cisco IOS é usado em muitos roteadores e switches Cisco, independentemente do tipo ou tamanho do dispositivo. Cada roteador de dispositivo ou tipo de switch usa uma versão diferente do Cisco IOS. Outros sistemas operacionais Cisco incluem IOS XE, IOS XR e NX-OS.

### 2.1.3 Objetivo de um SO
Os sistemas operacionais de rede são semelhantes a um sistema operacional de PCs. Por meio de uma GUI, um sistema operacional de PC permite que o usuário faça o seguinte:
- Utilizar um mouse para fazer seleções e executar programas;
- Inserir texto e comandos baseados em texto;
- Exibir a saída em um monitor.

Um sistema operacional de rede baseado em CLI (por exemplo, o Cisco IOS em um switch ou roteador) permite que um técnico de rede faça o seguinte:
- Use um teclado para executar programas de rede baseados na CLI;
- Use um teclado para inserir texto e comando s baseados em texto;
- Exibir a saída em um monitor.

### 2.1.4 Métodos de Acesso 

| Método             | Descrição                                                                                                                                                                                                                                                                             |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Console            | Esta é uma porta de gerenciamento físico que fornece acesso fora de banda a um dispositivo CISCO. A vantagem de usa-la, é que o dispositivo esta acessivel mesmo que nenhum serviço de rede esteja configurado. Um cabo console e um software de emulacao de terminal sao necessarios |
| Secure Shell (SSH) | Método na banda e recomendado para establecer conexao remota. Requer o servico configurado.                                                                                                                                                                                           |
| Telnet             | Método INSEGURO em banda. Melhor prática é usar Telnet.                                                                                                                                                                                                                               |
Alguns dispositivos, como roteadores, também podem suportar uma porta auxiliar herdada usada para estabelecer uma sessão CLI remotamente por uma conexão telefônica usando um modem. De modo semelhante a uma conexão de console, a porta AUX é do tipo fora de banda e não requer serviços de rede para ser configurada ou estar disponível.

## 2.1.5 Programas de Emulação de Terminal
- **Putty**
- **Tera Term**
- **SecureCRT**
## 2.2 Navegação IOS
### 2.2.1 Modos de Commando Primários
- **Modo EXEC de usuário (view-only)**: Recursos e comandos limitados, mas é útil para operações básicas. Não permite comandos que alterem o dispositivo. Identificado pelo símbolo `>`.
- **Modo EXEC privilegiado**: Para executar comandos de configuração. Pode acessar configuração global. Identificado por `#`.
### 2.2.2 Modo de configuração e modos de subconfiguração
No modo configuração global, são feitas alterações que afetam o dispositivo. Identificado por `(config)#`

Esse modo é acessado antes de modos especifico:
- Modo de configuração de linha - Usado para configurar o acesso ao console, SSH, Telnet ou AUX. (config-line)
- Modo de configuração de interface - Usado par configurar uma porta de switch ou interface de rede do roteador. (config-if )
### 2.2.4 Navegar Entre os Modos do IOS

- User exec mode <-> Privileged exec mode: ```
```
Switch> enable
Switch# disable
Switch> 
```
- Privileged exec mode -> Global configuration mode:
```
Switch# configure terminal
Switch(config)# exit
Switch#
```
- Global configuration mode <-> line configuration mode:
```
Switch(config)# line console 0
Switch(config-line)# exit
Switch(config)#
```
- Global configuration mode <-> interface configuration mode:
```
Switch(config)# interface vlan 1
Switch(config-if)# exit
Switch(config)#
```
- Any configuration mode -> Privileged EXEC mode:
```
Switch(config-line)# end
Switch#
...
Switch(config)# <CTRL+Z>
Switch#
```


### 2.3.1 Estrutura Básica de Comandos do IOS
- **Palavra chave** - Este é o parâmetro específico definido no sistema operacional.
- **Argumento** - Isto não é predefinido; é um valor ou variável definido pelo usuário.
### 2.3.2 Verificação de sintaxe do comando IOS

| Convenção        | Descrição                                                                                                                                                        |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **negrito**      | Indica comandos ou palavras-chave que você digita literalmente como mostrado.                                                                                    |
| *itálico*        | Indica argumentos para os quais você fornece valores.                                                                                                            |
| [X]              | Colchetes indicam um elemento opcional (palavra-chave ou argumento).                                                                                             |
| { x }            | Chaves indicam um elemento necessário (palavra-chave ou argumento).                                                                                              |
| [ x { y \| z } ] | Chaves e linhas verticais entre colchetes indicam uma necessidade dentro de um elemento opcional. Espaços são usados para delinear claramente partes do comando. |

Exemplo: 
```
Switch(config-if)# switchport port-security aging {  static | time time |     type   {absolute | inactivity}
```

### 2.3.3 Recursos da Ajuda do IOS
O IOS tem duas formas de ajuda: ajuda sensível ao contexto e verificação da sintaxe do comando.
A ajuda contextual permite que você encontre rapidamente respostas:
- Quais comandos estão disponíveis em cada modo?
- Quais comandos começam com carácter ou grupo de carácter específico?
- Quais argumentos e palavras-chaves estão disponíveis para comandos específicos?
Para acessar a ajuda sensível ao contexto, basta inserir um ponto de interrogação,`?`na CLI.

A verificação da sintaxe de comandos verifica se um comando válido foi inserido pelo usuário.

### 2.3.5 Teclas de Atalho e Atalhos
Os comandos e as palavras-chave podem ser abreviados para o número mínimo de caracteres que identifica uma seleção exclusiva. Por exemplo, o comando **configure** pode ser reduzido para **conf**, porque **configure** é o único comando que começa com **conf**. Uma versão ainda mais curta,**con**, não funcionará porque mais de um comando começa com **con**.

| Toque de tecla             | Descrição                                                                                                         |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Tab                        | Completa um nome de comando.                                                                                      |
| Ctrl+D                     | Apaga o caracter no cursor.                                                                                       |
| Ctrl+K                     | Apaga todos os caracteres do cursor até o fim da linha.                                                           |
| Esc D                      | Apaga todos os caractere do cursor até o final da palavra.                                                        |
| Ctrl+U ou Ctrl+X           | Apaga todos os caracteres do cursor de volta ao início da linha.                                                  |
| Ctrl+W                     | Apaga a palavra à esquerda do cursor.                                                                             |
| Ctrl+A                     | Move o cursor para o inicio da linha.                                                                             |
| Ctrl+B                     | Move o cursor para a esquerda.                                                                                    |
| Esc  B                     | Move o cursor uma palavra para esquerda.                                                                          |
| Esc F                      | Move o cursor uma palavra para a direita.                                                                         |
| Ctrl+F                     | Move o cursor a direita.                                                                                          |
| Ctrl+P                     | Recupera os comandos no buffer do histórico.                                                                      |
| Ctrl+N                     | Próxima linha do buffer.                                                                                          |
| Ctrl+R ou Ctrl+I ou Ctrl+L | Exibe novamente o prompt do sistema da linha de comando depois que uma mensagem do console é exibida ou recebida. |
Quando o IOS exibe: **--More--**

| Toque de tecla        | Descrição                        |
| --------------------- | -------------------------------- |
| Tecla Enter           | Exibe a próxima linha.           |
| Barra de Espaço       | Exibe a próxima tela.            |
| Qualquer outra tecla. | Encerra a sequência de exibição. |
Comandos para sair de uma operação.

| Toque de tecla | Descrição                                                                                                                                                                          |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ctrl-C         | Quando em qualquer modo de configuração, finaliza o modo de configuração e retorna para o modo EXEC privilegiado. Quando no modo de instalação, aborta de volta ao comando pronto. |
| Ctrl-Z         | Quando em qulauqer modo de configuração, retorna ao modo EXEC privilegiado.                                                                                                        |
| Ctrl-Shift-6   | Sequência de cancelamento de qualquer operação.                                                                                                                                    |
## 2.4.1 Nomes de Dispositivo

O nome padrão deve ser alterado para algo mais descritivo. Com uma escolha sábia de nomes, é mais fácil lembrar, documentar e identificar dispositivos de rede. Aqui estão algumas diretrizes de nomenclatura importantes para hosts:
- Começar com uma letra;
- Não conter espaços;
- Terminar com uma letra ou dígito;
- Usar somente letras, números e traços;
- Ter menos de 64 caracteres.
A próxima etapa é usar a CLI para aplicar os nomes aos dispositivos.
```
Switch# configure terminal
Switch(config)# hostname Sw-floor-1
Sw-floor-1(config)#
```
Observação: Para retornar o switch ao prompt padrão, use o comando **no hostname** global config.

### 2.4.2 Diretrizes de Senha
Ao escolher senhas, use senhas fortes que não sejam facilmente adivinhadas. Existem alguns pontos-chave a serem considerados ao escolher senhas:
- Use senhas com mais de oito caracteres.
- Use uma combinação de letras maiúsculas e minúsculas, números, caracteres especiais e/ou sequências numéricas.
- Evite usar a mesma senha para todos os dispositivos.
- Não use palavras comuns porque elas são facilmente adivinhadas.
### 2.4.3 Configurar Senhas
```
Sw-floor-1# configure terminal
Sw-floor-1(config)# line console 0
Sw-floor-1(config-line)# password cisco
Sw-floor-1(config-line)# login
Sw-floor-1(config-line)# end
Sw-floor-1#
```
O acesso ao console agora exigirá uma senha antes de permitir o acesso ao modo EXEC do usuário.
Para proteger o acesso EXEC privilegiado, use o comando de configura��o:
```
Sw-floor-1# configure terminal
Sw-floor-1(config)# enable secret class
Sw-floor-1(config)# exit
Sw-floor-1#
```

As linhas de terminal virtual (VTY) permitem acesso remoto usando Telnet ou SSH ao dispositivo. Muitos switches Cisco são compatíveis com até 16 linhas VTY numeradas de 0 a 15.
Um exemplo de segurança das linhas VTY em um switch é mostrado.
```
Sw-floor-1# configure terminal
Sw-floor-1(config)# line vty 0 15
Sw-floor-1(config-line)# password cisco
Sw-floor-1(config-line)# login
Sw-floor-1(config-line)# end
Sw-floor-1#
```
### 2.4.4 Criptografar as Senhas
Os arquivos startup-config e running-config exibem a maioria das senhas em texto simples.
Para criptografar todas as senhas de texto simples:
```
Sw-floor-1# configure terminal
Sw-floor-1(config)# service password-encryption
Sw-floor-1(config)#
```

O comando aplica criptografia fraca a todas as senhas não criptografadas. Essa criptografia se aplica apenas às senhas no arquivo de configuração, não às senhas como são enviadas pela rede. O propósito deste comando é proibir que indivíduos não autorizados vejam as senhas no arquivo de configuração.
Para verificar se as senhas agora estão criptografadas:
```
Sw-floor-1(config)# end
Sw-floor-1# show running-config
!
...
!
line con 0
password 7 094F471A1A0A
login
!
line vty 0 4
password 7 094F471A1A0A
login
line vty 5 15
password 7 094F471A1A0A
login 
!
!
end
```

### 2.4.5 Mensagens de Banner
Para criar uma mensagem de faixa do dia em um dispositivo de rede, use o comando de configuração global `banner motd # a mensagem do dia #`. O "#" na sintaxe do comando é denominado caractere de delimitação. Ele é inserido antes e depois da mensagem. O caractere de delimitação pode ser qualquer caractere contanto que ele não ocorra na mensagem. Por esse motivo, símbolos como "#"  são usados com frequência. Após a execução do comando, o banner será exibido em todas as tentativas seguintes de acessar o dispositivo até o banner ser removido.

```
Sw-floor-1# configure terminal
Sw-floor-1(config)# banner motd # Authorized Access Only #
```

## 2.5 Salvar Configurações
Há dois tipos de sistema que armazenam configurações do dispositivo:
- **startup-config**: Arquivo armazenado na NVRAM (Non-Volatile). Contém todos os comandos que serão usados pelo dispositivo na inicialização. Não perde conteúdo quando o dispositivo está desligado.
- **running-config**: Armazenado na RAM. Reflete a configuração atual. A alteração do arquivo modifica o funcionamento imediatamente. Perde todo seu conteúdo quando o dispositivo é desligado.

```
Sw-floor-1# show running-config
Building configuration...
Current configuration: 1351 bytes
!
! Last configuration change at 00:01:20 UTC Mon Mar 1 1993
!
version 15.0
no service pad
service timestamps debug datetime msec
service timestamps log datetime msec
service password-encryption
!
hostname Sw-floor-1
!
...
```

Para visualizar o arquivo de configuração de inicialização, use o comando EXEC privilegiado `show startup-config`.
Para salvar alterações do `running-config` para o `startup-config` utilize o comando no modo priv EXEC: `copy running-config startup-config`.

## 2.5.2 Alterar a Configuração Ativa
Para restaurar configurações para as configurações anteriores, utilize o comando `reload` para voltar para a `startup-config`.  Um prompt será exibido para pedir que as alterações sejam salvas. Para descartar as alterações, insira `n` ou `no`.
Utilizar o comando `reload`, causará uma breve interrupção aos serviços de rede.

Para restaurar o dispositivo para configurações de fábrica utilize o comando `erase startup-config`.

Alterações entram em vigor no momento que o comando é inserido, é importante que as alterações sejam planejadas antes de salva-las na NVRAM.

### 2.5.4 Capturar a configuração em um arquivo texto
Arquivos de configurações podem ser salvos em arquivos de texto.  
É possível capturar o arquivo do running-config utilizando emuladores de terminal, capturando a saída de configuração.

## 2.6 Portas e Endereços 
### 2.6.1 Endereços IP
É o principal meio para dispositivos se localizarem e conectarem um ao outro. Cada dispositivo final em uma rede deve ter um endereço IP.

A estrutura de um endereço IPv4 é chamada notação decimal com ponto, representada por quatro grupos de números entre 0 e 255.

Uma máscara de sub-rede é um valor de 32 bits que diferencia a parte da rede do endereço da parte do host. 

Endereços IPv6 têm 128 bits e são escritos em uma sequência de 8 grupos de valores hexadecimais, separados por 4 dígitos cada e dois pontos (:).

### 2.6.2 Interfaces e Portas
Diferenças essenciais entre mídias:
- A distância pela qual o meio físico consegue carregar um sinal com êxito;
- O ambiente no qual o meio físico deve ser instalado;
- A quantidade e a velocidade de dados nas quais eles devem ser transmitidos;
- O custo do meio físico e da instalação.
Cada link na internet não exige apenas um tipo de mídia de rede específico, mas também requer um tecnologia de rede específica.
Portas Ethernet são encontradas nos dispositivos finais e intermediários, para conectar fisicamente à rede por meio de um cabo.

Switches camada 2 têm portas físicas compatíveis com endereços IP camada 3. Switches tem interfaces virtuais (SVIs), existem porque não há hardware físico no dispositivo associado. Uma SVI é criada no software.

A interface virtual permite gerenciar remotamente um switch em uma rede usando IPv4 e IPv6. Todo switch tem um SVI na configuração padrão pronta para uso. A SVI padrão é a interface VLAN 1.

Um switch da camada 2 não precisa de endereço IP. O IP é atribuído à SVI.

## 2.7 Configurar Endereços IP
### 2.7.1 Configuração Manual de Endereços IP Para Dispositivos Finais
As informações de endereço IPv4 podem ser inseridas nos dispositivos finais manualmente ou automaticamente usando o DHCP (Dynamic Host Configuration Protocol).

Manualmente no Windows, abra o Control Panel > Network Sharing Center > Change adapter settings e escolha o adaptador. Selecione Properties e abra Internet Protocol Version 4 (TCP/IPv4) Properties. As configurações de IPv6 são semelhantes.

### 2.7.2 Configuração Automática de Endereço IP para Dispositivos Finais
Os dispositivos finais usam DHCP para configuração automática de endereços IPv4

### 2.7.4 Configuração da Interface Virtual de Switch#
Para configurar um SVI em um switch: 
```
Sw-floor-1# configure terminal
Sw-floor-1(config)# interface vlan 1
Sw-floor-1(config-if)# ip address 192.168.1.20 255.255.255.0
Sw-floor-1(config-if)# no shutdown
Sw-floor-1(config-if)# exit
Sw-floor-1(config)# ip default-gateway 192.168.1.1
```
O comando `no shutdown` mantém a interface virtual funcionando após a configuração.

## 2.8 Verificar a conectividade
### 2.8.1 Testar a atribuição de interface

O comando `show ip interface brief` mostra a condição das interfaces.

### 2.8.2 Testar a conectividade de ponta a pronta
Uma forma de testar a conectividade ponta a ponta é utilizando o comando `ping`.