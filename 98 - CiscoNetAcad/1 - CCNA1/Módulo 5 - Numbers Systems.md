## 5.1 Sistema de numeração binário
### 5.1.1 Endereços Binários e IPv4
É importante compreender o binário porque hosts, servidores e dispositivos de rede usam esse tipo de endereçamento.

Cada endereço é composto por uma string de 32 bits dividida em quatro seções, chamadas octetos. Cada octeto tem 8 bits (ou 1 byte) separados por um ponto.

### 5.1.3 Notação Posicional Binária

| Raiz              | 2   | 2   | 2   | 2   | 2   | 2   | 2   | 2   |
| ----------------- | --- | --- | --- | --- | --- | --- | --- | --- |
| Posição do número | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0   |
| Valor da posição  | 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |

### 5.1.5 Converter Binário para Decimal
Para converter IPv4 Binário para IPv4 Decimal, lembre-se da sequência de números que são potência de 2, do expoente 0 até o 7. 
Após, some primeiro o agrupamento de números binários 1s.
Preste atenção em somas que facilitarão as somas sequentes, somas que resultem em números que acabem com a unidade 0.
Números impares sempre terão, o primeiro bit como 1.
Se notar que algum digito de outro agrupamento pode ajudar em resultar em um número que acabe com a unidade 0, e seja uma soma simples, utilize-o.

Exemplo: 11101100
Somando o primeiro agrupamento: 128 + 64 + 32 = 160 + 64 = 224
Somando o segundo agrupamento: 8 + 4 = 12
Somando os dois agrupamentos: 224 + 12 = 236

Exemplo: 11010111
Primeiro agrupamento: **128** + 64
Terceiro agrupamento: **16**
Segundo agrupamento: **4** + **2** + 1

Primeiro passo: 128 + 2 = 130
Segundo passo: 16 + 4 = 20
Terceiro passo: 130 + 20 = 150
Ultimo passo: 150 + 65 = 215

### 5.1.7 Conversão de Decimal para Binário
Para converter decimal para binário, devemos ir da direita para esquerda na string binária, e comparar se o bit mais significativo é menor ou igual que o número decimal, se sim, subtraímos do número decimal e ativamos o bit, e seguimos para o próximo bit, se não, somente seguimos para o próximo bit. Faça isso até o número decimal ser zero.

Exemplo: 215
215 >= 128, então, 215-128 = 87
87 >= 64, então, 87 - 64 = 23
23 >= 32, não
23 >= 16, então, 23 - 16 = 7
7 >= 8, não
7 >= 4, então, 7 - 4 = 3
3 >= 2. então, 3 - 2 = 1
1 >= 1, então, 1 - 1 = 0

Temos: 11010111

### 5.1.11 Endereços IPv4
#### Endereço decimal com pontos
192.168.10.10 é um endereço IP atribuído a um computador.
#### Octetos
Esse endereço é composto por quatro octetos diferentes.
#### Endereço de 32 bits
O computador armazena o endereço como o fluxo de dados inteiro de 32 bits.

## 5.2 Sistema de numeração hexadecimal
### 5.2.1 Endereços hexadecimais e IPv6
Hexadecimal é um sistema de dezesseis bases.
Um número hexadecimal expressa 4 números binários.
O sistema de numeração hexadecimal é usado em rede para representar endereços IP versão 6 e endereços MAC Ethernet.
Os endereços IPv6 têm 128 bits de comprimento e a cada 4 bits é representado por um único dígito hexadecimal; para um total de 32 valores hexadecimais.

Nesse sistema número acima de 9 são representados respectivamente por A,B,C,D,E e F.

### 5.2.3 Conversões decimal para hexadecimal
Converter números decimais em valores hexadecimais é simples. Siga as etapas listadas:
1. Converta o número decimal para strings binárias de 8 bits.
2. Divida as cadeias binárias em grupos de quatro a partir da posição mais à direita.
3. Converta cada quatro números binários em seu dígito hexadecimal equivalente.
O exemplo fornece as etapas para converter 168 em hexadecimal.
Por exemplo, 168 convertidos em hexadecimal usando o processo de três etapas.
4. 168 em binário é 10101000.
5. 10101000 em dois grupos de quatro dígitos binários é 1010 e 1000.
6. 1010 é hexadecimal A e 1000 é hexadecimal 8.
**Responda:** 168 é A8 em hexadecimal.

### 5.2.4 Conversão hexadecimal em decimal
Converter números hexadecimais em valores decimais também é simples. Siga as etapas listadas:
1. Converta o número hexadecimal em cadeias binárias de 4 bits.
2. Criar agrupamento binário de 8 bits a partir da posição mais à direita.
3. Converta cada agrupamento binário de 8 bits em seu dígito decimal equivalente.
Este exemplo fornece as etapas para converter D2 em decimal.
4. D2 em cadeias binárias de 4 bits é 1101 e 0010.
5. 1101 e 0010 é 11010010 em um agrupamento de 8 bits.
6. 11010010 em binário é equivalente a 210 em decimal.
**Responda:** D2 em hexadecimal é 210 em decimal.

Para conversão direta temos que usar a base 16 da potencialização.
D2 = (D * 16^1 ) + (2 * 16 ^ 1) = (13 * 16) + (2 * 1) = 208 + 2 = 210