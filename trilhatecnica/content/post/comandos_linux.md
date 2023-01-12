---
title: "Comandos mais usados no Linux"
date: 2023-01-10T17:43:15-03:00
draft: true
---

# Versão do Linux

`$ cat /etc/os-release`
`$ lsb_release -a`
`$ cat /etc/issue`
`$ uname-a`

# Ajuda ou Documentação

## Páginas man
`$ man mkdir` (Documentação geralmente instalada com o software que pode ser acessada com o comando man)

|Seção|Descrição|
|-----|---------|
|NAME | Nome do comando e breve descrição
|SYNOPSIS | Descrição da sintaxe do comando|
|DESCRIPTION | Descrição dos efeitos do comando|
|OPTIONS | Opções disponíveis|
|ARGUMENTS | Argumentos disponíveis|
|FILES | Arquivos auxiliares|
|EXAMPLES | Uma amostra da linha de comando|
|SEE ALSO | Referências cruzadas aos tópicos relacionados|
|DIAGNOSTICS | Mensagens de Advertência e Erro|
|COPYRIGHT | Autor(es) do comando|
|BUGS | Limitações conhecidas do comando|

As páginas man estão organizadas em oito categorias, numeradas de 1 a 8:
|Categoria|Descrição|
|---------|---------|
|1 | Comando do usuário|
|2 | Chamadas do sistema|
|3 | Funções da biblioteca C|
|4 | Drivers e arquivos de dispositivo|
|5 | Arquivos de configuração e formatos de arquivo|
|6 | Jogos|
|7 | Miscelânea|
|8 | Comandos do administrador do sistema|
|9 | Funções do kernel (não padrão)|

## Páginas info
`$ info mkdir` (Geralmente são mais detalhadas que as páginas man) 

## Diretório
O diretório `/usr/share/doc/` armazena a maior parte da documentação dos comandos que estão em uso.

# Gestão de Arquivos e Pastas

## Localizar arquivos (locate)
`# updatedb` (Atualiza o banco de dados com informações de arquivos)
`$ locate nome_do_arquivo`  (O locate consulta um banco de dados, você pode não encontrar um arquivo que foi criado recentemente.)
`$ locate *TERMO*` (O comando locate também suporta o uso de curingas e expressões regulares)

## Localizar arquivos (find)
O comando find pesquisa recursivamente em uma árvore de diretórios, incluindo os subdiretórios.
`$find . -name nome_do_arquivo.pdf` (Procura no diretório atual)
`$ find ~ -name nome_do_arquivo.pdf` (Procura no diretório home do usuário)
name - busca por nome
type - busca por tipo
size - busca pelo tamanho do arquivo
mtime - busca por data de modificação


## Pastas
`$ mkdir` (Cria um novo diretório)
`$ ls` ou `$ ls --color=auto` (Exibe o conteúdo de um diretório)
`$ cd` (Passa para um diretório diferente)
`rmdir` (Remove um diretório)
du diretório: mostra o tamanho de um diretório;


## Arquivos
`$ touch` (Cria um arquivo ou modifica a hora e data da última modificação de um arquivo existente)
file arquivo: mostra informações de um arquivo;
`$ cat` (Concatena ou visualiza arquivos de texto)
`$ cut` (Remove seções de um arquivo de texto)
`$ cp` (Copia um arquivo)
`$ mv` (Move um arquivo (também pode ser usado para renomear)
`$ wc` (Conta o número de palavras, linhas ou bytes de um arquivo)
`$ passwd` Muda a senha de um usuário)
`$ rm` (Remove um arquivo)
`$ more` (Visualiza arquivos de texto uma tela de cada vez)
`$ less` (Visualiza arquivos de texto, permite rolar uma linha ou página por vez, para cima ou para baixo)
`$ whereis` (Exibe o caminho até um programa especificado e arquivos de manual relacionados)
`$ head` (Exibe as primeiras linhas de um arquivo)
`$ tail` (Exibe as últimas linhas de um arquivo)
`$ sort` (Ordena um arquivo numérica ou alfabeticamente)
`$ tr` (Traduz ou remove caracteres de um arquivo)
`$ chmod` (Altera as permissões de um arquivo)
`$ grep` (Busca dentro de um arquivo)


df: conferir o espaço em disco
sudo: permissões especiais
clear: limpar o buffer
cal: exibe um calendário;
date: mostra a data e a hora atual;
diff arquivo1 arquivo2: indica as diferenças entre dois arquivos
finger usuário: exibe informações sobre o usuário indicado;

free: mostra a quantidade de memória RAM disponível;

halt: desliga o computador;

history: mostra os últimos comandos inseridos;
id usuário: mostra qual o número de identificação do usuário especificado no sistema;

kill: encerra processados em andamento. Saiba mais no artigo Processos no Linux;

ls: lista os arquivos e diretórios da pasta atual;

lpr arquivo: imprime o arquivo especificado;

lpq: mostra o status da fila de impressão;

lprm: remove trabalhos da fila de impressão;

lynx: abre o navegador de internet de mesmo nome;

passwd: altera sua senha. Para um administrador mudar a senha de um usuário, basta digitar passwd seguido do nome deste;

ps: mostra os processos em execução. Saiba mais no artigo Processos no Linux;

pwd: mostra o diretório em que você está;

reboot: reinicia o sistema imediatamente (pouco recomendável, preferível shutdown -r now);

rm arquivo: apaga o arquivo especificado;

rmdir diretório: apaga o diretório especificado, desde que vazio;

shutdown: desliga ou reinicia o computador, veja:
shutdown -r now: reinicia o computador
shutdown -h now: desliga o computador

O parâmetro now pode ser mudado. Por exemplo: digite shutdown -r +10 e o sistema irá reiniciar daqui a 10 minutos;

su: passa para o usuário administrador, isto é, root (perceba que o símbolo $ mudará para #);

tar -xzvf arquivo.tar.gz: extrai um arquivo compactado em tar.gz. Saiba mais no artigo Compactação e descompactação de arquivos com Tar e gzip;

telnet: ativa o serviço de Telnet em uma máquina. Para acessar esse computador a partir de outros por Telnet, basta digitar telnet nomedamáquina ou telnet IP. Por exemplo: telnet 192.168.0.10. Após abrir o Telnet, digite help para conhecer suas funções;

top: exibe a lista dos processos, conforme os recursos de memória consumidos;

useradd usuário: cria uma nova conta usuário, por exemplo, useradd marvin cria o usuário marvin;

userdel usuário: apaga a conta do usuário especificado;

uptime: mostra a quantas horas seu computador está ligado;

vi: inicia o editor de textos vi. Saiba mais aqui;

whereis nome: procura pelo binário do arquivo indicado, útil para conhecer seu diretório ou se ele existe no sistema;

w: mostra os usuários logados atualmente no computador (útil para servidores);

who: mostra quem está usando o sistema.

1. exit
O exit permite terminar a sessão existente no terminal. Sempre execute-o após terminar atividades que demandam privilégios administrativos.

2. logout
O logout desloga o usuário da sua sessão atual. Porém, fique atento: o logoff será apenas na C shell e na bash shell que estiverem ativas.

3. passwd
Como o passwd é possível trocar a senha do usuário logado rapidamente.

4. rlogin
Utilize o rlogin sempre que você precisar logar em outro sistema Unix/Linux.

5. ssh
O ssh é o comando adotado para abrir uma sessão segura. Ele é fundamental para executar atividades em servidores remotos. Porém, é importante verificar se o sistema utilizado é compatível com o protocolo ssh.

6. slogin
A partir do slogin o usuário pode realizar um login com controles avançados de segurança em um sistema Linux/Unix.

7. yppasswd
O yppasswd permite mudar a senha do usuário nas páginas amarelas do sistema.

whatis
O comando “whatis” descreve o que outros comandos do Linux fazem, no exemplo abaixo, ele diz o que faz o comando “ls”:
whereis
O “whereis” é utilizado para localizar a página de ajuda, código-fonte ou arquivos binários de um determinado programa.

env
O comando “env” mostra todas as variáveis de ambiente que estão sendo utilizadas no sistema.

uptime
O comando uptime informa há quanto tempo o sistema está funcional, quando foi ligado e o seu uptime.

who
O comando “who” é utilizado para exibir quem está logado no sistema.

w – whoami
Isso mesmo, simplesmente, a letra “w”. O comando é utilizado para nos mostrar quem está no sistema, ou que comando cada job está a executar.

ps – process status
O comando “ps” é utilizado para mostrar os processos que estão ativos no momento.

# Controle de processos
jobs
O comando “jobs” exibe todos os jobs que estão em execução, quando corremos uma aplicação em background, poderemos ver esse job com este comando.

kill
O comando “kill” é utilizado para encerrar um programa que não esteja respondendo bem. Ele vai mandar um certo sinal ao aplicativo com mau funcionamento e instruir que ele seja encerrado logo na sequência.

bg – background
O comando “bg” coloca um processo suspenso em background.

fg – foreground
O comando “fg” faz o contrário do comando “bg”, trazendo de volta um processo ao foreground.





# Comunicação
1. mail
Esse comando simples abre espaço para uma interface para enviar e receber e-mails.

2. mesg
Com o mesg você pode habilitar ou negar o envio e o recebimento de mensagens pelo terminal. Elas são enviadas via rede para outro computador com o terminal ativo.

3. pine
Utilize o pine para enviar e receber e-mails.

4. talk
Com o talk é possível falar com outros usuários da sua rede.

5. write
Já o write facilita o envio de mensagens curtas de texto para outros usuários ativos.

ping
O comando “ping”, é utilizado para “pingar” um determinado host, ou seja, enviar pacotes ICMP para um determinado host e medir tempos de resposta, entre outras coisas.

ifconfig
O comando “ifconfig” possui a função de visualizar os ips da nossa máquina, entre outras funções relacionadas com ips.

ssh
O comando “ssh”, nos permite logar em um servidor remoto através do protocolo ssh.

wget
O “wget” efetua o download completo de páginas web, com todos os arquivos, de forma fácil e não interativa, sem exigir, por isso, presença do utilizador.

# Exibição e impressão de arquivos

head
O comando “head” mostra as primeiras linhas de um arquivo.

tail
O comando “tail” funciona de forma inversa ao comando head, exibe as últimas linhas de um arquivo ou mesmo do output de outro comando, quando usado como filtro.

more
O comando “more”, mostra o conteúdo de um arquivo, mas apenas uma tela de cada vez, ou mesmo output de outros comandos, como, por exemplo, ls | more.

less
O comando “less” funciona de maneira semelhante ao comando “more”, a diferença é que o “less” é utilizado para leitura de arquivos que ocupam mais de uma tela.

lpr
O comando “lpr” é utilizado para imprimir arquivos.

# Controle de acesso
passwd
O comando “passwd” serve para mudar a senha do usuário com o qual você estiver logado no momento.

exit
O comando “exit” termina a sessão, ou seja, a shell.

logout
O comando logout é utilizado para deslogar o usuário da sessão.

# Organizar
alias
O comando alias permite que você defina alias temporários em sua sessão shell. Ao criar um alias, você instrui seu shell a substituir uma palavra por uma série de comandos.
unalias
Como o nome sugere, o comando unalias visa remover um alias dos pseudônimos já definidos.
htop é um visualizador de processos interativo que permite a você gerenciar os recursos da sua máquina diretamente do terminal.
shutdown now
shutdown 20:40
shutdown -c
unzip
O comando unzip permite que você extraia o conteúdo de um arquivo .zip do terminal.
apt, yum, pacman
Não importa qual distribuição Linux você esteja usando, é provável que você use gerenciadores de pacotes para instalar, atualizar e remover o software que você usa todos os dias.
O comando echo exibe o texto definido no terminal – é tão simples quanto isso:

echo "Cool message"
Com ps, você pode dar uma olhada nos processos que sua sessão de shell atual está rodando.

which
O comando which produz o caminho completo dos comandos shell.
shred
Se você já quis que um arquivo fosse quase impossível de recuperar, shred pode ajudá-lo com esta tarefa. Este comando substitui o conteúdo de um arquivo repetidamente e, como resultado, o arquivo dado torna-se extremamente difícil de ser recuperado.

neofetch
Neofetch é uma ferramenta CLI (command-line interface) que exibe informações sobre seu sistema