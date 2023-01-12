---
title: "Testar cartões de memória e pendrives"
date: 2023-01-10T17:49:41-03:00
thumbnail:
  src: "/post/testar_pendrives/pendrive.jpg"
categories:
  - "Manutenção"
tags:
  - "Cartão de Memória"
  - "Pendrive"
---

Resolver problemas relacionados a cartões de memória falsificados ou defeituosos no Linux.
<!--more-->
O kit de ferramentas **F3**, traz um conjunto de aplicativos para verificar, testar e consertar mídias flash falsificadas.

Desenvolvido pelo Michel Machado é uma alternativa a aplicativos proprietários como o **SOSFakeFlash** e o **H2testw****.

De acordo com o Michel, `F3` corresponde às palavras Fight Flash Fraud, (combate a fraude em mídias flash) ou Fight Fake Flash (combate a flash falso).

Vale lembrar que **NUNCA** deve-se usar mídias falsas ou defeituosas, mesmo que estejam funcionando “razoavelmente” para armazenar arquivos importantes.

Antes de prosseguir, certifique-se de ter backup de seus dados.

## O kit de ferramentas F3
O conjunto de aplicativos consiste:
- **f3probe** - maneira mais rápida para identificar drives falsos e determinar o tamanho real deles, em bytes.
- **f3fix** - cria condições para usar a capacidade real de uma mídia falsa, sem perder dados.
- **f3brew** - ajuda desenvolvedores a entender o funcionamento de drives falsos.

## 1 - Instalar o F3 

No Arch Linux:
```
$ paru -Syu f3
```

Debian e Ubuntu:
```
$ sudo apt update
$ sudo apt install f3
```

## 2 - Como usar o f3 (Fight Fake Flash)

1 - Inserir a mídia no seu leitor, certifique-se da sua localização com o comando lsblk:
```
$ lsblk
```

Destaque na última linha:
```
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda       8:0    0 931,5G  0 disk
├─sda1    8:1    0  21,4G  0 part /
├─sda2    8:2    0 881,1G  0 part /home
└─sda3    8:3    0  10,4G  0 part [SWAP]
mmcblk0 179:0    0   1,9G  0 disk
```

3 - Após a montagem da mídia, execute o `f3write` em relação a **pasta/diretório** em que a mídia se encontra montada:
```
$ f3write /media/justincase/music/
```
O processo pode demorar alguns minutos:
```
Free space: 2.68 GB
Creating file 1.h2w ... OK!
Creating file 2.h2w ... OK!        
Creating file 3.h2w ... OK!
Free space: 0.00 Byte
Average writing speed: 5.30 MB/s
```

O **f3write** procurou preencher o espaço livre com os arquivos **1.h2w**, **2.h2w**, **3.h2w** ... assim por diante, até preencher toda a memória, mas sem apagar os arquivos preexistentes.

4 - Em seguida, use o **f3read** para verificar a consistência dos arquivos **.h2w**:
```
$ f3read /media/justincase/music/
```

O resultado é separado em 4 colunas:
- 1 coluna - Exibe a quantidade de setores OK.
- 2 coluna - A quantidade de setores corrompidos.
- 3 coluna - Mostram os setores que sofreram alterações.
- 4 coluna - Mostram os setores que foram sobrescritos.
```
SECTORS      ok/corrupted/changed/overwritten
Validating file 1.h2w ... 2097152/        0/      0/      0
Validating file 2.h2w ... 2097152/        0/      0/      0
Validating file 3.h2w ... 1434984/        0/      0/      0
 
Data OK: 2.68 GB (5629288 sectors)
Data LOST: 0.00 Byte (0 sectors)
           Corrupted: 0.00 Byte (0 sectors)
    Slightly changed: 0.00 Byte (0 sectors)
         Overwritten: 0.00 Byte (0 sectors)
Average reading speed: 20.16 MB/s
```

A quantidade de dados que se encontra em setores confiáveis (ou Data OK).
Os números dos campos Data LOST e Corrupted, correspondem aos setores ruins e que não merecem confiança dentro da sua mídia.

Se você tivesse problemas, esta seção exibiria algo parecido com o seguinte:
```
Data LOST: 27.81 GB (58322336 sectors)
           Corrupted: 27.81 GB (58322336 sectors)
```

Algumas variações no espaço/capacidade total da mídia de armazenamento, em relação ao anunciado na embalagem, podem ser atribuídas a sistemas de arquivos que fazem reservas de segurança (ext2, ext3, ext4 etc.)

## Como testar o dispositivo de armazenamento com o f3probe
O **f3probe** não precisa que a sua mídia esteja montada e deve ser direcionado ao `endereço físico` e não à pasta de montagem.

1 - Novamente, use o `lsblk` para descobrir onde se encontra o dispositivo em que você quer executar o `f3probe`.
```
$ sudo f3probe /dev/mmcblk0
```

O resultado, abaixo, indica que o device está danificado e que tem 0.00 bytes *utilizáveis*.
```
F3 probe 6.0
Copyright (C) 2010 Digirati Internet LTDA.
This is free software; see the source for copying conditions.
 
WARNING: Probing normally takes from a few seconds to 15 minutes, but
         it can take longer. Please be patient.
 
Probe finished, recovering blocks... Done
 
Bad news: The device `/dev/mmcblk0' is damaged
 
Device geometry:
             *Usable* size: 0.00 Byte (0 blocks)
            Announced size: 1.88 GB (3952640 blocks)
                    Module: 2.00 GB (2^31 Bytes)
    Approximate cache size: 0.00 Byte (0 blocks), need-reset=no
       Physical block size: 512.00 Byte (2^9 Bytes)
 
Probe time: 7.33s

```
Ao tentar usar uma identificação como `/dev/sdb1` ou `/dev/sdc3`, para o `f3probe`, ele irá avisar que você precisa indicar o endereço raíz `/dev/sdb` ou `/dev/sdc`.
Para acessar este tipo de endereço, é necessário ter privilégios administrativos.
Use a opção `–destructive` se você não se importa em perder dados no dispositivo testado.
Acrescente a opção `–min-memory`, para economizar memória do sistema — em compensação o processo ficará mais lento.
A opção `–time-ops`, testa leitura, escrita e aplica resets.
A mensagem abaixo, se você a obtiver é indício de falsificação:
```
Bad news: The device `/dev/sdb’ is a counterfeit of type limbo.
```
A opção `–destructive` faz o utilitário desprezar o conteúdo do drive, para aumentar a velocidade do teste. Sem ela, o `F3` fará backup dos dados, antes de os destruir e os copia de volta, quando terminar o teste.
O problema é que você ainda pode perder tudo, caso o `F3` deixe de funcionar no meio do procedimento. Portanto, faça seu próprio backup, antes de usar o `F3`.

## Como resolver o problema do cartão de memória falso

Obviamente, você não deve aceitar ficar com um produto falso.
O melhor caminho é deixar claro para o vendedor que você sabe que ele te vendeu um produto ilegítimo e procurar receber o seu dinheiro de volta.
Ao agir assim, você ajuda outras pessoas a não serem enganadas.
Se não houver meios de reaver o seu prejuízo, esta seção irá te ajudar a tentar reduzir os danos.
Uma mídia de armazenamento falsa, usualmente, tenta fazer passar que tem um capacidade muito superior à real.
Por exemplo, anuncia que é um cartão de 32 GB e tem, no máximo, 8 GB utilizáveis.
Se você prestar atenção, o resultado do `f3probe` contém uma sugestão de uso do `f3fix` que pode ajudar a corrigir o problema no caso de mídia falsa.
O aviso costuma ser parecido com este:
```
f3fix --last-sec=16477878 /dev/sdb
```
Certifique-se de ter privilégios de superusuário para rodar o comando contido no aviso que você obteve, aí.

O `f3fix` funciona criando uma partição no seu cartão de memória, que incluirá apenas a sua parte utilizável. Isto evita que dados sejam gravados na “área ruim” (ou inexistente).
Ainda assim, não é recomendável confiar os arquivos mais importantes da sua vida a um dispositivo nestas condições.
Esta solução te dará algum fôlego para guardar dinheiro para comprar um novo cartão de memória SD.

Se, ao final da execução, o `f3fix` avisar que tem que forçar o kernel a recarregar a tabela de partições 
```
reload the new partition table
```
desconecte e reconecte o dispositivo. Assim que a nova partição estiver disponível, faça a sua formatação.
O exemplo, abaixo, formata a mídia em /dev/sdb1 com o sistema de arquivos VFAT:
```
$ sudo mkfs.vfat /dev/sdb1
```
A partir deste ponto, o cartão deve estar a funcionar bem.
Monte-o novamente e faça o teste f3write/f3read, novamente
Se você ainda obtiver mensagens informando erros e setores corrompidos, repita o procedimento f3write/f3read, mais uma vez.
É comum alguns cartões se recuperarem de falhas em um segundo ciclo de escrita.
Contudo, se os setores corrompidos persistirem, o conselho é desistir da mídia — pois ela não é apenas falsa, mas de baixíssima qualidade.
Boa sorte!

# Fontes:
https://elias.praciano.com/2016/08/baixe-e-instale-o-f3-para-testar-cartoes-de-memoria-e-pendrives-no-linux/

