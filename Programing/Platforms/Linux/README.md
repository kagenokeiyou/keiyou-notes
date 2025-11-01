# Linux

## 命令

### ls

`ls` (list directory contents) 用于显示指定工作目录下之内容

```bash
ls [OPTION] [FILE]
```

## 常用速查

### `~/.bashrc` 配置

```bash
# 非交互模式下不执行
[[ $- != *i* ]] && return

export PS1='\n\[\033[32m\]\u\[\033[0m\] \[\033[36m\]\w\[\033[0m\]\n\[\033[33m\]\$\[\033[0m\] '

export HISTCONTROL=ignoreboth
export HISTSIZE=5000
export HISTFILESIZE=10000

shopt -s histappend
shopt -s cmdhist
shopt -s checkwinsize

alias ..='cd ..'
alias ...='cd ../..'

alias ls='ls --color=auto -F'
alias la='ls --color=auto -AF'
alias ll='ls --color=auto -lhAF'

alias grep='grep --color=auto' 
alias fgrep='fgrep --color=auto'
alias egrep='egrep --color=auto'

alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

[[ -f /usr/share/bash-completion/bash_completion ]] && \
  . /usr/share/bash-completion/bash_completion
```

### `sudo` 免密码

```bash
sudo vim /etc/sudoers
```

```text
%sudo ALL=(ALL:ALL) NOPASSWD:ALL
```
