<p align="center">
    <a href="https://devinthehood.com"><img src="https://github.com/jul6art/slim-skeleton/blob/master/assets/img/logo.png?raw=true" alt="logo dev in the hood"></a>
</p>

<p align="center">
    <a href="https://opensource.org/licenses/MIT" target="_blank"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License"></a>
    <a href="https://github.com/jul6art/server-config" target="_blank"><img src="https://img.shields.io/static/v1?label=stable&message=v1&color=success" alt="Version"></a>
</p>

Configuration de serveurs
=========================
Paquets de base
---------------

Aliases

```console
nano .bashrc
```
    
Modifier comme ceci

```console
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
fi

# ls Aliases
alias ll='ls -alL'
alias la='ls -A'
alias l='ls -CF'

PS1="\u [\w] > "
```

Mise à jour du system
  
```console
source .bashrc && 
apt-get update -y &&
apt-get install build-essential -y
```  
    
Installation des paquets de base

```console
apt-get install sudo git
```
   

License
-------

The Server Config is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

&copy; 2019 [dev in the hood](https://devinthehood.com) 

















