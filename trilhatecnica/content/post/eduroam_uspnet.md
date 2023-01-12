---
title: "Eduroam"
date: 2023-01-10T17:47:41-03:00
thumbnail:
  src: "/post/eduroam_uspnet/eduroam.jpg"
categories:
  - "Redes"
tags:
  - "Linux"
  - "USP"
---

O **Eduroam** (education roaming) é um serviço de acesso sem fio seguro, desenvolvido para a comunidade internacional de educação e pesquisa.
<!--more-->
A iniciativa permite que os estudantes, os pesquisadores e as equipes das instituições participantes obtenham conectividade à Internet, através de conexão sem fio (wi-fi), dentro de seus campi e em qualquer localidade que ofereça essa facilidade como provedora de serviço.

# Como usar

A rede sem fio eduroam esta disponível para computadores e dispositivos portáteis compatíveis com o padrão IEEE 802.11.

Resumidamente, as configurações de seu dispositivo móvel para acesso ao eduroam são as seguintes:

## Configurações de rede sem fio (Wireless network settings):
- Escolher o SSID ou “Nome da Rede” eduroam (tudo em minúsculo).
- Tipo de Autenticação é o WPA2 Enterprise.
- Modo de Criptografia a ser usado é o AES.

## Configurações de Autenticação de Usuário:
- O protocolo de autenticação é o EAP, escolher o tipo PEAP ou TTLS. Em sistema Android o TTLS funciona melhor.
- Método de Autenticação é MS-CHAPv2.

## Credenciais do usuário:
- Usuário: o número USP com o sufixo @usp.br (exemplo: 123456@usp.br).
- Senha de acesso: corresponde à senha única de acesso ao USPdigital.
- É possível recuperar a senha em  https://id.usp.br/senha-unica

# Fonte:
https://eduroam.usp.br/como-usar/

