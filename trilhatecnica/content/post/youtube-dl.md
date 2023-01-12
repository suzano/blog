---
title: "Youtube-dl"
date: 2023-01-10T17:51:00-03:00
thumbnail:
  src: "/post/youtube-dl/youtube.jpg"
categories:
  - "Download"
tags:
  - "Linux"
  - "Vídeos"
  - "Áudios"
---

O **youtube-dl** é um programa de linha de comando para baixar vídeos do YouTube.com e de alguns outros sites.

<!--more-->

Você pode facilmente baixar vídeos de mais de 270 sites e entre eles estão:
- YouTube, Metacafe, Dailymotion, Instagram, Vine, Vimeo, Tumblr, Trilulilu, Syfy, Slashdot, RottenTomatoes, NBC, NBA, NBCNews, MySpace, MTV, Metacritic, KickStarter, GameSpot, Flickr, Dropbox, Discovery, CollegeHumor, ComedyCentral, CNN, CBS, Bloomberg e 9gag.
- 4tube, AddAnime, AppleTrailers, ARD, Bandcamp, BlipTV, Brightcove, Chilloutzone, Cinemassacre, Clipsyndicate, DepositFiles e FranceInter.
- YouPorn, XTube, XNXX, Pornjam, Pornotube, XHamster, PornHub, PornHd, RedTube e Mofosex.

## 1 - Instalação do youtube-dl

No Arch Linux, você pode instalá-lo diretamente do terminal usando os comandos:
```
$ sudo pacman -Syu
$ sudo pacman -S youtube-dl
```

No Ubuntu:
```
$ sudo apt install youtube-dl
```

## 2 - Uso da ferramenta youtube-dl

De acordo com o tipo de mídia desejado:

![Tipos de mídia](../youtube-dl/youtube-dl_tipos_midia.jpg)

Para FULL HD 1080p:
```
$ youtube-dl -o arquivo.mp4 -f 37 "URL"
```

Para 720p:
```
$ youtube-dl -o arquivo.mp4 -f 22 "URL"
```

O comando básico às vezes é a melhor opção:
```
$ youtube-dl "URL"
```

Outras opções:
```
-b - Melhor qualidade.
-m - Versão móvel.
-d - Alta Definição.
-g - Não faça download, apenas mostre o url.
-c - Retomar o download de um vídeo que foi interrompido anteriormente.
-w - Não sobrescrever o arquivo existente.
```

## 3 - Download com conversão para MP3
No entanto, se você deseja converter os vídeos .webm para .mp3, você precisará do FFMpeg instalado em seu sistema.

Para baixar e converter qualquer outro formato de vídeo para um arquivo .mp3:
```
$ youtube-dl --extract-audio --audio-format mp3 "URL"
```

Para baixar uma lista de reprodução:
```
$ youtube-dl -itcv --yes-playlist https://www.youtube.com/playlist?list=
```

Agora, se quiser que essa lista se transforme em .mp3, faça assim:
```
$ youtube-dl -itcv --yes-playlist --extract-audio --audio-format mp3 https://www.youtube.com/playlist?list=
```

# Fontes
https://www.linuxexperten.com/content/youtube-dl-youtube-mp3-downloader



