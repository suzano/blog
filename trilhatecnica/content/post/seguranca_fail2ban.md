---
title: "Segurança - Fail2Ban"
date: 2023-01-10T17:55:14-03:00
draft: true
---


O Fail2Ban é um software de código aberto que pode ser usada para proteger seu servidor de ataques de força bruta detectando o tráfego em rede.
O Fail2Ban funciona monitorando continuamente os arquivos de log (SSH, Apache, vsftpd, proftpd, postfix, couriersmtp, courierauth, etc) e bane de forma automática adicionando regras no firewall do sistema para bloquear de imediato essas tentativas.

### Instalação:

```
$ sudo apt install fail2ban
```

### Arquivos com mais importâncias do Fail2ban:

`/etc/fail2ban/filter.d/` \- Contém filtros fail2ban predefinidos (regex).
`/etc/fail2ban/jail.conf` \- Não recomendado para ser atualizado, use jaulas personalizadas.
`/etc/fail2ban/jail.local` \- Suas cadeias personalizadas (ou customisation.local).
`/etc/fail2ban/fail2ban.conf` \- Arquivo de configuração principal.

### Bloqueando ataques de brute force no ssh:

```
$ sudo mv /etc/fail2ban/jail.conf ⠀ /etc/fail2ban/jail.old
```

### Criando um novo arquivo com as regras ativas:

```
$ sudo nano /etc/fail2ban/jail.local
```

```
[ssh]
enabled = true
filter = sshd
action = iptables[name=ssh, port=”ssh”, protocol=tcp]
logpath = /var/log/auth.log
maxretry = 5
bantime = 3600
ignoreip = 127.0.0.0/8 10.0.0.0/8



# Fail2Ban configuration file.
#
# This file was composed for Debian systems from the original one
# provided now under /usr/share/doc/fail2ban/examples/jail.conf
# for additional examples.
#
# Comments: use '#' for comment lines and ';' for inline comments
#
# To avoid merges during upgrades DO NOT MODIFY THIS FILE
# and rather provide your changes in /etc/fail2ban/jail.local
#

# The DEFAULT allows a global definition of the options. They can be overridden
# in each jail afterwards.

[DEFAULT]

# "ignoreip" can be an IP address, a CIDR mask or a DNS host
ignoreip = 127.0.0.1 192.168.0.99
bantime = 600
maxretry = 3

# "backend" specifies the backend used to get files modification. Available
# options are "gamin", "polling" and "auto".
# yoh: For some reason Debian shipped python-gamin didn't work as expected
# This issue left ToDo, so polling is default backend for now
backend = polling

#
# Destination email address used solely for the interpolations in
# jail.{conf,local} configuration files.
destemail = root@localhost

# Default action to take: ban only
action = iptables[name=%(__name__)s, port=%(port)s]

[ssh]

enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 5

[apache]

enabled = true
port = http
filter = apache-auth
logpath = /var/log/apache*/*error.log
maxretry = 5

[apache-noscript]

enabled = false
port = http
filter = apache-noscript
logpath = /var/log/apache*/*error.log
maxretry = 5

[vsftpd]

enabled = false
port = ftp
filter = vsftpd
logpath = /var/log/auth.log
maxretry = 5

[proftpd]

enabled = true
port = ftp
filter = proftpd
logpath = /var/log/auth.log
failregex = proftpd: \(pam_unix\) authentication failure; .* rhost=<HOST>
maxretry = 5

[wuftpd]

enabled = false
port = ftp
filter = wuftpd
logpath = /var/log/auth.log
maxretry = 5

[postfix]

enabled = false
port = smtp
filter = postfix
logpath = /var/log/mail.log
maxretry = 5

[courierpop3]

enabled = true
port = pop3
filter = courierlogin
failregex = courierpop3login: LOGIN FAILED.*ip=\[.*:<HOST>\]
logpath = /var/log/mail.log
maxretry = 5

[courierimap]

enabled = true
port = imap2
filter = courierlogin
failregex = imapd: LOGIN FAILED.*ip=\[.*:<HOST>\]
logpath = /var/log/mail.log
maxretry = 5

[sasl]

enabled = true
port = smtp
filter = sasl
failregex = warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed
logpath = /var/log/mail.log
maxretry = 5
```

Explicação de cada linha acima:
`enabled = true` \- Habilitamos a verificação
`filter = sshd` \- Especificando o filtro da pasta /etc/fail2ban/filter.d/
`action = iptables[name=ssh, port=”ssh”, protocol=tcp]` \- Importando um filtro da pasta /etc/fail2ban/filter.d/
`logpath = /var/log/auth.log` \- Diretório onde ficará os logs salvos de logins que falharam.
`maxretry = 5` \- Máximo de tentativas erradas de login permitidos por cada ip até banir
`bantime = 3600` \- Tempo de banimento do ip na blacklist
`ignoreip = 127.0.0.0/8 10.0.0.0/8` \- Lista do range de ips pra não serem bloqueados

### Iniciando o serviço e verificando o seu status:

```
$ sudo service fail2ban start
$ sudo service fail2ban status
```

### Monitorando os logs em tempo real:

```
$ sudo tail -f /var/log/fail2ban.log
```

### E se utilizar o Iptables pra verificar a regra onde ele barra o IP:

```
$ sudo iptables -L
```

### Fontes:
https://blog.ffelix.eti.br/prevenindo-ataques-de-forca-bruta-com-fail2ban/