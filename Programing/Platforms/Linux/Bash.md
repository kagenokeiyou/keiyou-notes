# Bash

## 重新加载配置

```bash
source ~/.bashrc
```

## 自用配置

```bash
export PS1="\n\033[33m\u\033[0m \033[36m\w\033[0m\n\033[32m\$\033[0m "

alias ..='cd ..'
alias ...='cd ../..'

alias ls='ls --color=auto'
alias la='ls --color=auto -A'
alias ll='ls --color=auto -lAh'

alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

alias grep='grep --color=auto' 
alias fgrep='fgrep --color=auto'
alias egrep='egrep --color=auto'
```
