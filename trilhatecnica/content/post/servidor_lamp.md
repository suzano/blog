---
title: "Servidor - LAMP"
date: 2023-01-10T17:46:22-03:00
draft: true
---

# Apache
O servidor HTTP Apache é o servidor Web mais amplamente usado no mundo. Ele fornece muitas características poderosas, incluindo módulos carregáveis dinamicamente, suporte robusto de mídia e uma integração extensa com outros softwares populares.

## Instalação
Atualize o cache do seu gerenciador de pacotes e, em seguida, instale o Apache com:
```
$ paru
$ paru -Sy apache
```
## Configurar o Apache
Abra o arquivo de configuração do apache:
```
$ sudo nano /etc/httpd/conf/httpd.conf
```
Comente o `unique_id_module` (você pode usar ctrl w para encontrá-lo rapidamente):
```
$ #LoadModule unique_id_module modules/mod_unique_id.so
```
Reinicie o Apache:
```
$ sudo systemctl restart httpd
```
Adicionando seu nome de host à sua configuração, caso não esteja:
```
$ sudo nano /etc/hosts
```
Adicione seu nome de host ao final da linha que começa com 127.0.0.1:
```
127.0.0.1 localhost.localdomain localhost arquimedes
```
Para experimentar rapidamente uma página de amostra adicionando um arquivo index.html ao diretório raiz de documentos do Arch, localizado em `srv/http`:
```
$ sudo nano /srv/http/index.html
```
Com o conteúdo:
```
<html> <title>Bem-vindo</title> <corpo> <h2>Olá, bem-vindo ao Arch</h2> </body> </html>
```
Visite a página de espaço reservado acessando o endereço IP do servidor no navegador. Para encontrar o endereço IP do seu servidor:
```
$ curl -s icanhazip.com
```
Habilite o serviço Apache para iniciar na inicialização e reinicie o serviço Apache usando os comandos:
```
$ sudo systemctl enable httpd
$ sudo systemctl restart httpd
```
Você pode verificar se o Apache está em execução ou não com o comando:
```
$ sudo systemctl status httpd
```

## Gerenciando o Processo Apache
Para parar seu servidor Web, digite:
```
$ sudo systemctl stop apache
```
Para iniciar o servidor quando ele for parado, digite:
```
$ sudo systemctl start apache
```
Para parar e então iniciar o serviço novamente, digite:
```
$ sudo systemctl restart apache
```
Se você estiver simplesmente fazendo alterações de configuração, o Apache geralmente pode recarregar sem quedas na conexão. Para fazer isso, utilize este comando:
```
$ sudo systemctl reload apache
```
Por padrão, o Apache está configurado para iniciar automaticamente quando o servidor for iniciado. Se isso não é o que você quer, desative este comportamento digitando:
```
$ sudo systemctl disable apache
```
Para reativar o serviço de inicialização no boot, digite:
```
$ sudo systemctl enable apache
```

## Configurando Hosts Virtuais (Recomendado)
Ao usar o servidor Web Apache, você pode usar hosts virtuais (similares a blocos de servidor no Nginx) para encapsular detalhes de configuração e hospedar mais de um domínio de um único servidor. Vamos configurar um domínio chamado `your_domain`, mas você deve `substituí-lo por seu próprio nome de domínio`.
O Apache no Ubuntu 20.04 tem um bloco de servidor habilitado por padrão que está configurado para servir documentos do diretório `/var/www/html`. Enquanto isso funciona bem para um único site, ele pode tornar-se indevido se você estiver hospedando vários sites. Ao invés de modificar o `/var/www/html`, vamos criar uma estrutura de diretórios dentro do `/var/www` para um site `your_domain`, deixando o `/var/www/html` no lugar como o diretório padrão para ser exibido se um pedido de cliente não corresponder a nenhum outro site.
Crie o diretório para o `your_domain` como segue:
```
$ sudo mkdir /var/www/your_domain
```
Em seguida, atribua a propriedade do diretório com a variável de ambiente $USER:
```
$ sudo chown -R $USER:$USER /var/www/your_domain
```
As permissões dos seus web roots devem estar corretas se você não tiver modificado seu valor de umask, que define permissões padrão de arquivos. Para garantir que suas permissões estejam corretas e permitam que o proprietário leia, escreva e execute os arquivos, enquanto concede apenas permissões de leitura e execução para grupos e outros, você pode digitar o seguinte comando:
```
$ sudo chmod -R 755 /var/www/your_domain
```
A seguir, crie uma página de amostra index.html utilizando o nano ou seu editor favorito:
```
$ sudo nano /var/www/your_domain/index.html
```
Dentro, adicione a seguinte amostra HTML:
```
<html>
    <head>
        <title>Welcome to Your_domain!</title>
    </head>
    <body>
        <h1>Success!  The your_domain virtual host is working!</h1>
    </body>
</html>
```
Salve e feche o arquivo quando você terminar.
Para que o Apache sirva este conteúdo, é necessário criar um arquivo de host virtual com as diretivas corretas. Em vez de modificar o arquivo de configuração padrão localizado em `/etc/apache2/sites-available/000-default.conf` diretamente, vamos criar um novo em `/etc/apache2/sites-available/your_domain.conf`:
```
$ sudo nano /etc/apache2/sites-available/your_domain.conf
```
Cole no seguinte bloco de configuração, que é similar ao padrão, mas atualizado para nosso novo diretório e nome de domínio:
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName your_domain
    ServerAlias www.your_domain
    DocumentRoot /var/www/your_domain
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
Note que atualizamos o `DocumentRoot` para nosso novo diretório e o `ServerAdmin` para um e-mail que o administrador do site `your_domain` pode acessar. Também adicionamos duas diretivas: o `ServerName`, que estabelece o domínio base que deve corresponder e essa definição de host virtual, e o `ServerAlias`, que define nomes adicionais que devem corresponder como se fossem o nome base.
Salve e feche o arquivo quando você terminar.
Vamos habilitar o arquivo com a ferramenta `a2ensite`:
```
$ sudo a2ensite your_domain.conf
```
Desabilite o site padrão definido em 000-default.conf:
```
$ sudo a2dissite 000-default.conf
```
Em seguida, vamos testar à procura de erros de configuração:
```
$ sudo apache2ctl configtest
```
Você deve receber a seguinte saída:
```
$ Syntax OK
```
Reinicie o Apache para implementar as suas alterações:
```
$ sudo systemctl restart apache2
```
O Apache agora deve estar atendendo seu nome de domínio. Você pode testar isso navegando para `http://your_domain`.

## Familiarizando-se com Arquivos e Diretórios Importantes do Apache
Agora que você sabe como gerenciar o serviço do Apache, você deve gastar alguns minutos para familiarizar-se com alguns diretórios e arquivos importantes.

### Conteúdo
- `/var/www/html`: O conteúdo Web em si, que por padrão apenas consiste na página Apache padrão que você viu antes, é servido do diretório `/var/www/html`. Isso pode ser alterado mudando os arquivos de configuração do Apache.

### Configuração do Servidor
- `/etc/apache2`: o diretório de configuração do Apache. Todos os arquivos de configuração do Apache residem aqui.
- `/etc/apache2/apache2.conf`: O arquivo de configuração principal do Apache. Isso pode ser modificado para fazer alterações na configuração global do Apache. Este arquivo é o responsável por carregar muitos dos outros arquivos no diretório de configuração.
- `/etc/apache2/ports.conf`: Este arquivo especifica as portas nas quais o Apache irá escutar. Por padrão, o Apache escuta na porta 80 e adicionalmente escuta na porta 443 quando um módulo que fornece capacidades SSL está ativo.
- `/etc/apache2/sites-available/`: O diretório onde hosts virtuais de cada site podem ser armazenados. O Apache não usará os arquivos de configuração encontrados neste diretório a menos que estejam ligados ao diretório sites-enabled. Normalmente, todas as configurações de bloco do servidor são feitas neste diretório e então habilitadas ligando-as ao outro diretório com o comando `a2ensite`.
- `/etc/apache2/sites-enabled/`: O diretório onde hosts virtuais habilitados de cada site são armazenados. Normalmente, eles são criados ligando arquivos de configuração encontrados no diretório sites-available com o `a2ensite`. O Apache lê os arquivos de configuração e links encontrados neste diretório quando inicia ou recarrega para compilar uma configuração completa.
- `/etc/apache2/conf-available/`, `/etc/apache2/conf-enabled/`: Estes diretórios têm a mesma relação que os diretórios `sites-available` e `sites-enabled`, mas são usados para armazenar fragmentos de configuração que não pertencem em um host virtual. Arquivos no diretório `conf-available` podem ser habilitados com o comando `a2enconf` e desabilitados com o comando `a2disconf`.
- `/etc/apache2/mods-available/`, `/etc/apache2/mod-enabled/`: Estes diretórios contêm os módulos disponíveis e habilitados, respectivamente. Arquivos com final `.load` contêm fragmentos para carregar módulos específicos, enquanto os arquivos com final `.conf` contêm a configuração para esses módulos. Módulos podem ser habilitados e desabilitados utilizando os comandos `a2enmod` e `a2dismod`.

### Registros do Servidor
- `/var/log/apache2/access.log`: Por padrão, cada solicitação feita para seu servidor é gravada neste arquivo de registro a menos que o Apache esteja configurado para fazer de outro modo.
- `/var/log/apache2/error.log`: Por padrão, todos os erros são gravados neste arquivo. A diretiva `LogLevel` na configuração do Apache especifica quanto detalhe os registros de erros irão conter.

# MariaDB
MariaDB é um sistema de gerenciamento de banco de dados relacional de código aberto, comumente usado como alternativa para o MySQL como a parte do banco de dados do popular LAMP (Linux, Apache, MySQL, PHP / Python / Perl). Ele pretende ser um substituto para o MySQL

## Instalar o MariaDB
Utilize o apt para adquirir e instalar este software:
```
$ paru
$ paru -Sy mariadb
```
## Configurando o MariaDB
Inicializar o diretório de dados do MariaDB antes de iniciar o serviço. Para isso, execute:
```
$ mysql_install_db --user=mysql --basedir=/usr --datadir=/var/lib/mysql
```
Habilite o serviço Apache para iniciar na inicialização e reinicie o serviço Apache usando os comandos:
```
$ sudo systemctl enable mysqld
$ sudo systemctl restart mysqld
$ sudo systemctl status mysqld
```
É recomendável que você execute um script de segurança que vem pré-instalado
com o MariaDB. Inicie o script interativo executando:
```
$ sudo mysql_secure_installation
```
Isso levará você a uma série de prompts onde você pode fazer algumas alterações nas opções de segurança da sua instalação do MariaDB. O primeiro prompt solicitará que você insira a senha raiz do banco de dados atual. Como você ainda não configurou um, pressione `ENTER` para indicar `none`.
O próximo prompt pergunta se você deseja configurar uma senha de root do banco de dados. No Ubuntu, a conta root do MariaDB está intimamente ligada à manutenção automatizada do sistema, portanto, não devemos alterar os métodos de autenticação configurados para essa conta. Isso possibilitaria que uma atualização de pacote quebrasse o sistema de banco de dados removendo o acesso à conta administrativa. Digite `N` e pressione `ENTER`.
Mais tarde, abordaremos como configurar uma conta administrativa adicional para acesso por senha se a autenticação de soquete não for apropriada para seu caso de uso.
A partir daí, você pode pressionar `Y` e depois `ENTER` para aceitar os padrões para todas as perguntas subsequentes. Isso removerá alguns `usuários anônimos` e o `banco de dados de teste`, `desabilitará logins root remotos` e carregará essas novas regras para que o MariaDB implemente imediatamente as alterações feitas.
## Criando um usuário administrativo que emprega autenticação de senha
Nos sistemas Ubuntu que executam o MariaDB 10.3, o usuário root do MariaDB é configurado para autenticar usando o plug-in `unix_socket` por padrão, em vez de uma senha. Isso permite maior segurança e usabilidade em muitos casos, mas também pode complicar as coisas quando você precisa permitir direitos administrativos de um programa externo (por exemplo, phpMyAdmin).
Como o servidor usa a conta root para tarefas como de `log` e `iniciar` e `parar` o servidor, é melhor não alterar os detalhes de autenticação da conta root. Alterar as credenciais no arquivo de configuração `/etc/mysql/debian.cnf` pode funcionar inicialmente, mas as atualizações de pacotes podem sobrescrever essas alterações. Em vez de modificar a conta root, os mantenedores do pacote recomendam a criação de uma conta administrativa separada para acesso baseado em senha.
Para isso, criaremos uma nova conta chamada `admin` com os mesmos recursos da conta `root`, mas configurada para autenticação por senha.
Abra o prompt do MariaDB no seu terminal:
```
$ sudo mariadb
```
Em seguida, crie um novo usuário com privilégios de root e acesso baseado em senha. Certifique-se de alterar o nome de usuário e a senha para corresponder às suas preferências:
```
$ GRANT ALL ON *.* TO 'admin'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;
```
Esvazie os privilégios para garantir que eles sejam salvos e estejam disponíveis na sessão atual:
```
MariaDB [(none)]> FLUSH PRIVILEGES;
```
Depois disso, saia do shell MariaDB: 
```
MariaDB [(none)]> exit
```
Por fim, vamos testar a instalação do MariaDB.
## Testando o MariaDB
Quando instalado a partir dos repositórios padrão, o MariaDB começará a ser executado automaticamente. Para testar isso, verifique seu status.
```
$ sudo systemctl status mariadb
```
Se o MariaDB não estiver rodando, você pode iniciá-lo com o comando:
```
$ sudo systemctl start mariadb
```
Para uma verificação adicional, você pode tentar se conectar ao banco de dados usando a ferramenta mysqladmin, que é um cliente que permite executar comandos administrativos. Por exemplo, este comando diz para se conectar ao MariaDB como root usando o soquete Unix e retornar a versão:
```
$ sudo mysqladmin version
```
Se você configurou um usuário administrativo separado com autenticação de senha, poderá realizar a mesma operação digitando:
```
$ mysqladmin -u admin -p version
```
Isso significa que o MariaDB está funcionando e que seu usuário pode se autenticar com sucesso.

# PHP
O PHP é o componente de nossa configuração que processará o código para exibir conteúdo dinâmico ao usuário final. Além do pacote php, você precisará do `php-mysql`, um módulo PHP que permite que o PHP se comunique com bancos de dados baseados em MySQL. Você também precisará do `libapache2-mod-php` para permitir que o Apache manipule arquivos PHP. Os pacotes PHP principais serão instalados automaticamente como dependências.

## Instalando o PHP
Para instalar esses pacotes, execute:
```
$ paru
$ paru -Sy php php-apache
$ paru -Sy php-apache php-cgi php-fpm php-gd  php-embed php-intl php-imap  php-redis php-snmp
```
Quando a instalação estiver concluída, você pode executar o seguinte comando para confirmar sua versão do PHP:
```
$ php -v
```
O PHP também deve ser adicionado ao arquivo de configuração do apache:
```
$ sudo nano /etc/httpd/conf/httpd.conf
```
Encontre a seguinte linha e comente-a:
```
#LoadModule mpm_event_module modules/mod_mpm_event.so
```
Em seguida, adicione as seguintes linhas na parte inferior:
```
[...]
#comment the line:
#LoadModule mpm_event_module modules/mod_mpm_event.so

#and uncomment the line:
LoadModule mpm_prefork_module modules/mod_mpm_prefork.so

#Append this at the end of the LoadModule list:
LoadModule php_module modules/libphp.so
AddHandler php-script .php

#Append this at the end of the Include list:
Include conf/extra/php_module.conf
```
Dar uma olhada e ver os detalhes do PHP criando uma página rápida de informações do php
```
$ sudo nano /srv/http/info.php
```
Adicione na seguinte linha:
```
<?php
 phpinfo();
?>
```

Reinicie o apache para que todas as alterações entrem em vigor:
```
$ sudo systemctl restart httpd
```
Visite sua página de informações do php (certifique-se de substituir o endereço IP de exemplo pelo correto): http://localhost/info.php

## Instalando o phpMyAdmin
Como a interface do phpMyAdmin é totalmente baseada em seu navegador, você precisará de um servidor web (como Apache, nginx, IIS) para instalar os arquivos do phpMyAdmin.

É recomendável que você também instale estes pacotes:
- php-mbstring: um módulo para gerenciar strings não-ASCII e converter strings para diferentes codificações
- php-zip: esta extensão possui suporte de upload de arquivos .zip para o phpMyAdmin
- php-gd: habilita o suporte para a biblioteca gráfica do GD
- php-json: fornece o PHP com suporte para a serialização JSON
- php-curl: permite que o PHP interaja com diferentes tipos de servidores usando protocolos diferentes
```
$ paru -Sy phpmyadmin
```
Na seleção do servidor, escolha `apache2`, aperte as teclas SPACE, TAB e, então, ENTER para selecionar o Apache.
Selecione `Yes` quando indagado quanto a se usará o `dbconfig-common` para configurar o banco de dados. Será solicitado que escolha e confirme a senha do aplicativo MySQL para o phpMyAdmin


## Passo 6 - Instalando o phpMyAdmin
1. Usando o apt instalá-los em seu sistema:
`$ sudo apt update`
`$ sudo apt install phpmyadmin php-mbstring`
2. A única coisa que você precisa fazer é habilitar explicitamente a mbstring extensão PHP, o que pode ser feito digitando:
`$ sudo phpenmod mbstring`
3. Em seguida, reinicie o Apache para que suas alterações sejam reconhecidas:
`$ sudo systemctl restart apache2`
4. Ajustando a autenticação do usuário e os privilégios
`$ sudo mysql`
`SELECT user,authentication_string,plugin,host FROM mysql.user;`
`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'NOVO_PASSWORD';`
`CREATE USER 'suzano'@'localhost' IDENTIFIED BY 'SENHA';`
`GRANT ALL PRIVILEGES ON *.* TO 'suzano'@'localhost';`
`FLUSH PRIVILEGES;`


# Fontes
- https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-arch-linux
- https://ostechnix.com/install-apache-mariadb-php-lamp-stack-on-arch-linux-2016/
- https://pt.linux-console.net/?p=887
- https://techviewleo.com/how-to-install-php-on-garuda-arch-manjaro/
- https://techviewleo.com/install-phpmyadmin-on-arch-manjaro-garuda-linux/

