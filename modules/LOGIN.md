<p align="center">
    <a href="https://devinthehood.com"><img src="https://github.com/jul6art/slim-skeleton/blob/master/assets/img/logo.png?raw=true" alt="logo dev in the hood"></a>
</p>

<p align="center">
    <a href="https://opensource.org/licenses/MIT" target="_blank"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License"></a>
    <a href="https://github.com/jul6art/server-config" target="_blank"><img src="https://img.shields.io/static/v1?label=stable&message=v1&color=success" alt="Version"></a>
</p>

Configuration de serveurs
=========================
Première connexion
------------------

Changer le mot de passe de l'utilisateur root
    
```console
passwd root   
```
    
Récupérer la clef ssh de notre machine

```console
cat ~/.ssh/id_rsa.pub
```
    
Ajouter la clef au serveur

```console
mkdir ~/.ssh && 
nano ~/.ssh/authorized_keys
```
    
Désactiver le timeout ssh

```console
nano /etc/ssh/sshd_config
```
    
Et ajouter les paramètres suivants

```console
TCPKeepAlive yes
ClientAliveInterval 60
ClientAliveCountMax 720
```
    
Redémarrer le service ssh

```console
service ssh restart
```
   

License
-------

The Server Config is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

&copy; 2019 [dev in the hood](https://devinthehood.com) 

















