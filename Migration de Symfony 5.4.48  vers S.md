Migration de Symfony 5.4.48  vers Symfony 6.0   puis  7.3
Faire la liste de tous les elements de l'environnement du serveur;
➡️ Système

Ubuntu 22.04.5 LTS

➡️ Symfony

Symfony 5.4.48 (LTS)

Mode prod

Utilise PHP 8.1 + OPcache

Chemins standards /var/www/symfony

➡️ PHP

PHP 8.4.15

PHP-FPM 8.1 actif (/var/run/php/php8.1-fpm.sock)

Extensions clés : intl, mbstring, pdo_mysql, curl, opcache…

➡️ Nginx

Version : 1.18
 vhost :  symfony

Certbot (Let’s Encrypt) actif

Racine projet : /var/www/symfony/public

Redirection HTTP → HTTPS

index.php exposé via fastcgi_pass

➡️ Base de données

MariaDB 10.6.22

Socket : /run/mysqld/mysqld.sock

Service actif

➡️ Composer

Version : 2.2.6


 
`node -v`
v18.20.8

`yarn -v`
1.22.22


Exécute `composer self-update` pour mettre Composer à jour.

`composer --version`
Composer version 2.9.2 2025-11-19 21:57:25
PHP version 8.4.15 (/usr/bin/php8.4)


installer le pack pour debugger si nécessaire
`composer require symfony/debug-pack --dev`




