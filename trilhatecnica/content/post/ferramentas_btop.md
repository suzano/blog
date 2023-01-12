---
title: "Ferramentas_btop"
date: 2023-01-10T18:00:22-03:00
draft: true
---

As ferramentas de linha de comando, geralmente são mais rápidas e mais eficientes em termos de recursos do que as alternativas de GUI.

# btop ++ (Monitor do Sistema)
Esta ferramenta de código aberto foi escrita em C ++ para maior velocidade e tornar a visualização das atividades do seu sistema na forma de um painel de recursos bem projetado.
Você obtém informações de memória, CPU e gráficos de arquivos de troca que são atualizados em tempo real; carga do processador e informações de tempo de atividade do sistema; uma lista classificável de dados do processo em tempo real sobre o uso da CPU, consumo de memória e prioridade do processo; além de uma tonelada de opções de configuração para permitir que você ajuste quais estatísticas aparecem e em que ordem.
Instação do btop++:
```
sudo snap install btop
```

# musikcube (reprodutor de música)
Tem uma IU que é inspirada em tocadores de música de desktop com recursos completos, mas, ao contrário deles, está livre de distrações desnecessárias. Posso percorrer toda a minha biblioteca; filtrar por artista, álbum, gênero ou lista de reprodução; e criei manualmente uma fila de reprodução que se adequasse inteiramente ao meu humor, sem precisar tirar uma única mão do teclado.
Instação do musikcube:
```
sudo snap install musikcube
```

## googler (Pesquisar na web)
uma captura de tela de um aplicativo googler para pesquisar no Google a partir da linha de comando
Prova ser útil em uma pitada 
Você sabia que é possível pesquisar na web a partir da linha de comando? Oh, você fez? Bem, você sabia que também é uma experiência muito boa?

Usando o googlerutilitário CLI, você pode pesquisar no Google a partir da linha de comando (e se você não é um fã de Sundar & co, há uma ferramenta igualmente capaz de pesquisar DuckDuckGo a partir da linha de comando ddgrtambém chamada ).

Por que pesquisar na web a partir da linha de comando pode ser útil? Talvez você esteja em um ttyporque seu sistema está instável e precisa encontrar uma solução. Você pode pegar seu telefone e pesquisar, ou você pode usar uma ferramenta de mecanismo de pesquisa de linha de comando como googler, exatamente onde você está.

Esqueça quaisquer preconceitos que você possa ter sobre formatação pobre ou resultados difíceis de ler porque, como as ferramentas de mecanismo de pesquisa de terminal vão, ambas as opções são bem projetadas e repletas de recursos. Eles permitem que você filtre por palavra-chave, limite o intervalo de pesquisa, pesquise apenas sites específicos, abra links em seu navegador GUI e muito mais.

De uma chance!

sudo apt install googler

## neofetch (informações do sistema)
Um único comando é suficiente para ver uma riqueza de informações sobre sua configuração do Linux, de qual distro você usa para qual versão do kernel você está usando, além de seu ambiente de área de trabalho, gerenciador de janelas, tema, conjunto de ícones e muito mais .
sudo apt install neofetch

## wttr (previsão do tempo)
Assim como os dias chuvosos no Reino Unido, os aplicativos de clima para desktop Linux são bastante comuns. Existem todos os tipos de widgets, miniaplicativos de painel, clientes GUI e complementos de barra de status capazes de retransmitir as condições meteorológicas atuais.

Mas você também pode verificar o clima na linha de comando. Algumas ferramentas são básicas, mas outras, como a que está abaixo, mostram uma previsão de vários dias para qualquer local que você especificar. Isso é útil quando você deseja saber mais do que o tempo que está fazendo agora (é assim que as janelas têm a forma certa?).

Meu favorito é wttr.in. Não é a ferramenta de clima CLI mais detalhada, mas tem uma boa aparência, não requer nenhuma configuração complexa (por exemplo, chaves de API) e é memorável - você nem precisa instalá-la se tiver por curlperto.

Para obter uma previsão, abra um terminal e execute o seguinte, substituindo 'Cidade' por um local:
curl wttr.in/City

## ncdu (analisador de disco)
Para uma maneira prática e rápida de descobrir quais arquivos e pastas estão ocupando mais espaço em disco em seu sistema, vá para Uso de disco do NCurses , ou ncducomo é mais conhecido. É uma versão supercarregada da du ferramenta regular  que usa uma interface de usuário totalmente interativa e baseada em curses.

Embora o ncdu faça a maior parte do que as ferramentas de armazenamento integradas da sua distro podem fazer, é mais rápido - muito mais rápido - e a forma como apresenta tamanho e estrutura é muito eficiente. Você pode navegar usando as teclas de seta, clicar enterpara entrar e sair das pastas e tocar dpara excluir - mas não se preocupe, isso vai verificar se você tem certeza!

sudo apt install ncdu

## nnn (gerenciador de arquivos)
uma captura de tela do gerenciador de arquivos nnn no ubuntu 21.10
Percorra seus arquivos e pastas 
Você provavelmente sabe como fechar em torno de seu sistema de arquivos a partir do CLI usando o cdcomando e ls, cp, mvetc para gerenciar arquivos. O nnngerenciador de arquivos também pode fazer tudo isso e muito mais - tudo em uma única interface.

O principal benefício de usar o nnn é que ele é super leve em recursos, rápido e facilita a navegação usando algumas teclas (em vez de digitar comandos).

sudo apt install nnn

mapscii (Mapas)
um gif do aplicativo de mapa de terminal mapscii
Mapscii oferece detalhes incríveis 
Vou terminar esta lista com uma ferramenta CLI que demonstra a engenhosidade absoluta que os utilitários baseados em terminal costumam exibir, e o JavaScript puro mapsciié apenas o bilhete.

É ser capaz de visualizar e navegar mapas em um terminal extremamente prático? Não. Mas usar mapsciié como usar o Google Earth pela primeira vez: você não pode deixar de querer mergulhar e explorar.

Você pode navegar pelos mapas no Mapscii usando as setas do teclado (ou usando o mouse para clicar e arrastar o mapa) e aumentar ou diminuir o zoom usando as teclas ae zou a roda de rolagem do mouse.

O que é impressionante é o quão detalhada é a maioria dos mapas. Você pode ampliar para ver edifícios, ruas e outras informações com detalhes incríveis. Embora eu não ache que você queira traçar uma rota em algum lugar desconhecido usando Mapscii, não há como negar que ele tem um charme único.

Você pode instalar o Mapscii a partir do Snap Store , mas pode experimentá-lo sem instalá-lo executando:

telnet mapscii.me
## Fonte
https://www.omgubuntu.co.uk/2021/11/best-command-line-tools-ubuntu-linux


