---
title: "Seguranca_openssh"
date: 2023-01-10T17:57:51-03:00
draft: true
---

# Segurança
## OpenSSH
### Descrição:
### Instalação:
```
$ sudo apt install openssh-server
```
### Ativando o serviço do SSH:
```
$ sudo service ssh status
```
### Liberando as portas SSH no Firewall UFW:
```
$ sudo ufw allow ssh
```
### Configurando o SSH:
```
$ sudo nano /etc/ssh/sshd_config
```

### Conectando-se ao sistema remoto da sua máquina local:
```
$ sudo apt install openssh-client
$ ssh nomedeusuario@endereco
```
### Fontes:
https://sempreupdate.com.br/saiba-como-instalar-ativar-e-usar-o-ssh-no-ubuntu-linux/
https://sempreupdate.com.br/saiba-como-instalar-ativar-e-usar-o-ssh-no-ubuntu-linux/

