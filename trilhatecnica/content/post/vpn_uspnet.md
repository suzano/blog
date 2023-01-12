---
title: "Configurar a VPN USPnet no Linux"
date: "2023-01-10T12:00:00-03:00"
thumbnail:
  src: "/post/vpn_uspnet/vpn.jpg"
categories:
  - "Redes"
tags:
  - "Linux"
  - "USP"
  - "VPN"
---

Procedimento para configurar uma conexão VPN da USP. O tutorial a seguir foi testado no Arch Linux e Ubuntu.

<!--more-->

# VPN no Arch Linux (pela interface gráfica)

## 1 - Instalar o OpenConnect

Comece abrindo o "terminal" do linux e execute as linhas de comandos no terminal:
```
$ sudo pacman -Syu
$ sudo pacman -S openconnect
$ sudo pacman -S networkmanager-openconnect
```

## 2 - Configurar uma nova conexão VPN com o OpenConnect
Entre em "Configurações de Rede" no seu linux. No campo VPN, clique no sinal "+" para adicionar uma configuração de rede:
![Rede](../vpn_uspnet/arch01.jpg)

Clique em "Cliente VPN multiprotocolo (openconnect)":
![VPN](../vpn_uspnet/arch02.jpg)


Preencha o campo Nome da conexão com "VPN USPNet" e o campo Gateway com "vpn.semfio.usp.br".
Não é necessário alterar os outros campos. Clique em "Adicionar":
![USPNet](../vpn_uspnet/arch03.jpg)

## 3 - Fazer a conexão

Mude a chave de conexão para ON. Na janela que abrir clique sobre o ícone de rede.
Os dados para acesso são o seu Número USP e sua senha única do portal "uspdigital.usp.br".

Depois de preencher os dados, clique em Login, e a conexão deve ser estabelecida.

![Login](../vpn_uspnet/arch04.jpg)

# VPN no Ubuntu (pela interface gráfica)

## 1 - Instalar o OpenConnect

Comece abrindo o "terminal" do linux e execute as linhas de comandos no terminal:
```
$ sudo apt-get install network-manager-openconnect 
$ sudo apt-get install network-manager-openconnect-gnome 
```

## 2 - Configurar uma nova conexão VPN com o OpenConnect

Entre em "Configurações de Rede" no seu linux. No campo VPN, clique no sinal "+" para adicionar uma configuração de rede:

![Rede](../vpn_uspnet/ubuntu01.jpg)

No campo VPN, clique no sinal "+" para adicionar uma configuração de rede:

![VPN](../vpn_uspnet/ubuntu02.jpg)

Clique em "VPN Compatível com Cisco AnyConnect (openconnect)" e em seguida "Criar".

![USPNet](../vpn_uspnet/ubuntu03.jpg)

Preencha o campo Nome da conexão com "VPN USPNet" e o campo Gateway com "vpn.semfio.usp.br".
Não é necessário alterar os outros campos. Clique em "Salvar".

![Rede](../vpn_uspnet/ubuntu04.jpg)

## 3 - Fazer a conexão

Mude a chave de conexão para ON. Na janela que abrir clique sobre o ícone de rede.
Os dados para acesso são o seu Número USP e sua senha única do portal "uspdigital.usp.br".
Depois de preencher os dados, clique em "Login".

![Login](../vpn_uspnet/ubuntu05.jpg)

Depois disso, a conexão deve ser estabelecida.

![Conexao](../vpn_uspnet/ubuntu06.jpg)

# Fontes

https://atendimentosti.usp.br/otrs/public.pl?Action=PublicFAQZoom;ItemID=25