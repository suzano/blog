---
title: "Comandos - Alias"
date: 2023-01-10T17:52:18-03:00
draft: true
---

# Arquivo .bashrc
De maneira bem resumida, o arquivo .bashrc (ou .bash_profile em algumas distros) é o arquivo que carrega as configurações do bash para o usuário logado.

## Criando um alias
Pois bem, encontramos o arquivo, agora em seu conteúdo, observe o seguinte trecho:
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Conforme dito nas instruções, Embora seja possível adicionar atalhos diretamente ao `.bashrc`, o recomendável é adicioná-los ao `.bash_aliases`.


# Arquivo .bash_aliases

```
# Ubuntu
alias ls='ls --color=auto'
alias update="sudo apt-get update"
alias web-version="php -v || "
alias rm='rm -i'
alias ll='ls -l'
alias cs='cd;ls'
alias ok="ping google.com"
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
alias bar='echo foo'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias foo='echo foo'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
alias foo='echo foo'
alias bar='echo foo'
alias baz='echo baz'
```

