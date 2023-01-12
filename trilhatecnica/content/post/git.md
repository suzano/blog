---
title: "Git"
date: 2023-01-06T22:47:21-03:00
thumbnail:
  src: "assets/images/github/github.jpg"
categories:
  - "Desenvolvimento"
tags:
  - "HTML"
  - "CSS"
  - "Markdown"
draft: true
---

# Instalação do Git

Caso você já tenha o Git instalado, você pode verificar com o seguinte comando:
```
$ git --version
```

Se o git tiver instalado, o comando te dirá a versão do Git. Se não tiver, o recomendado é instalar pelo gerenciador de pacotes do seu sistema.

No Arch Linux:
```
$ paru -Sy git
```

Configuração
A configuração obrigatória do Git é simples: basta dar nome e email.

Para definir seu nome como "Suzano Bitencourt", basta executar:
```
$ git config --global user.name 'Suzano Bitencourt'
```

Para definir seu email como "suzanobitencourt@gmail.com", basta executar:
```
$ git config --global user.email 'suzanobitencourt@gmail.com'
```

Para verificar o nome e e-mail definidos:
```
$ git config user.name
$ git config user.email
```
