<p align="center">
    <a href="https://devinthehood.com"><img src="https://github.com/jul6art/slim-skeleton/blob/master/assets/img/logo.png?raw=true" alt="logo dev in the hood"></a>
</p>

<p align="center">
    <a href="https://opensource.org/licenses/MIT" target="_blank"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License"></a>
    <a href="https://github.com/jul6art/server-config" target="_blank"><img src="https://img.shields.io/static/v1?label=stable&message=v1&color=success" alt="Version"></a>
</p>

Configuration de serveurs
=========================
Plusieurs PHP en parallèle
--------------------------

![logo PHP](http://php.net//images/logos/new-php-logo.svg "logo php")

Installation
------------

```console
sudo apt-get -y install apt-transport-https lsb-release ca-certificates &&
sudo curl -ssL -o /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/	apt.gpg &&
sudo sh -c 'echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" 	> /etc/apt/sources.list.d/php.list' &&
sudo apt-get update &&
sudo apt-get install php5.6-cli php7.0-cli php7.1-cli php7.2-cli php7.3-cli -y &&
sudo apt-get install php5.6-fpm php7.0-fpm php7.1-fpm php7.2-fpm php7.3-fpm -y
```
	
Modules PHP

```console
sudo apt-get install php5.6-intl php5.6-soap php5.6-gd php5.6-mbstring php5.6-mcrypt php5.6-curl php5.6-zip php5.6-opcache php5.6-mysql php5.6-pgsql php5.6-xml php5.6-apc -y &&
sudo apt-get install php7.0-intl php7.0-soap php7.0-gd php7.0-mbstring php7.0-mcrypt php7.0-curl php7.0-zip php7.0-opcache php7.0-mysql php7.0-pgsql php7.0-xml php7.0-apc -y &&
sudo apt-get install php7.1-intl php7.1-soap php7.1-gd php7.1-mbstring php7.1-mcrypt php7.1-curl php7.1-zip vphp7.1-opcache php7.1-mysql php7.1-pgsql php7.1-xml php7.1-apc -y &&
sudo apt-get install php7.2-intl php7.2-soap php7.2-gd php7.2-mbstring php7.2-curl php7.2-zip php7.2-opcache php7.2-mysql php7.2-pgsql php7.2-xml php7.2-apc -y &&
sudo apt-get install php7.3-intl php7.3-soap php7.3-gd php7.3-mbstring php7.3-curl php7.3-zip php7.3-opcache php7.3-mysql php7.3-pgsql php7.3-xml php7.3-apc -y
```
	
Configuration (php.ini)

```console
expose_php = Off     
```

> To not display PHP version in headers
    
Manipulation d'images

```console
sudo apt-get install jpegoptim optipng pngquant gifsicle -y

curl -sL https://deb.nodesource.com/setup_11.x | bash -

sudo apt-get install -y nodejs npm && sudo npm install -g svgo
```

Composer

```console
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"

php composer-setup.php

php -r "unlink('composer-setup.php');"

mv composer.phar /usr/local/bin/composer
```

Module apache proxy_fcgi

```console
a2enmod proxy_fcgi &&
service apache2 restart
```
    
> Si virtualmin est installé, les dernières étapes sont d'installer les modules phpX.X-cgi et redémarrer le fpm

>   sudo apt-get install php5.6-cgi php7.0-cgi php7.1-cgi php7.2-cgi php7.3-cgi -y
    
Configuration (sauf si virtualmin est installé)
-----------------------------------------------

> :warning: Répéter les opérations pour chaque version de PHP avec des ports différents
    
    nano /etc/php/5.6/fpm/pool.d/www.conf

changer

```console
listen = /run/php/php5.6-fpm.sock
```

par
	
```console
listen = 127.0.0.1:9056
```
	
Utilisation dans un fichier de conf apache (sauf si virtualmin est installé)
----------------------------------------------------------------------------

```console
<FilesMatch "\.php$">
        Require all granted
        SetHandler proxy:fcgi://127.0.0.1:9056
</FilesMatch>
```


License
-------

The Server Config is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

&copy; 2019 [dev in the hood](https://devinthehood.com)
