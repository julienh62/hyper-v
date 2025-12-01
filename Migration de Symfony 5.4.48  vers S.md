``Migration de Symfony 5.4.48  vers Symfony 6.0   puis  7.3``
``Faire la liste de tous les elements de l'environnement du serveur;``
``➡️ Système``

``Ubuntu 22.04.5 LTS``

``➡️ Symfony``

``Symfony 5.4.48 (LTS)``

``Mode prod``

``Utilise PHP 8.1 + OPcache``

``Chemins standards /var/www/symfony``

``➡️ PHP``

``PHP 8.4.15``

``PHP-FPM 8.1 actif (/var/run/php/php8.1-fpm.sock)``

``Extensions clés : intl, mbstring, pdo_mysql, curl, opcache…``

``➡️ Nginx``

``Version : 1.18``
 ``vhost :  symfony``

``Certbot (Let’s Encrypt) actif``

``Racine projet : /var/www/symfony/public``

``Redirection HTTP → HTTPS``

``index.php exposé via fastcgi_pass``

``➡️ Base de données``

``MariaDB 10.6.22``

``Socket : /run/mysqld/mysqld.sock``

``Service actif``

``➡️ Composer``

``Version : 2.2.6``

 
node -v
``v18.20.8``

yarn -v
``1.22.22``

``pour mettre Composer à jour``
composer self-update 

composer --version
``Composer version 2.9.2 2025-11-19 21:57:25``
``PHP version 8.4.15 (/usr/bin/php8.4)``


installer le pack pour debugger si nécessaire
`composer require symfony/debug-pack --dev



``la commande suivante v afficher les dépréciations``
php bin/console debug:deprecations
``Sensio\Bundle\FrameworkExtraBundle\EventListener\IsGrantedListener::__construct():`` ``Implicitly marking parameter $authChecker as nullable is deprecated, the explicit``

``Rechercher ensuite les termes depréciés``
grep -R "FrameworkExtraBundle" Controller/
grep -R "@ParamConverter" Controller/
grep -R "@Template" Controller/
si ne renvoie rien

``le bundle Sensio n’est plus nécessaire :``
composer remove sensio/framework-extra-bundle

``verifier à nouveau``
php bin/console debug:deprecations

``Prochaines étapes avant migration Symfony 6/7``
``Vérifier ton projet pour d’autres dépendances obsolètes :``
composer outdated

```Points critiques``
``Packages Doctrine majeurs à mettre à jour``
``doctrine/orm : 2.20.2 → 3.5.7``
``doctrine/doctrine-bundle : 2.13.2 → 3.0.0``
``doctrine/migrations-bundle : 3.4.1 → 3.7.0``

``Mettre à jour Symfony vers 6.4 :``
``remplacer dans composer.json tous les 5.4 par 6.4``
sed -i 's/"5\.4\.\*"/"^6.4"/g' composer.json

composer update "symfony/*" --with-all-dependencies

composer require symfony/asset:^6.4 symfony/config:^6.4 symfony/console:^6.4 symfony/dependency-injection:^6.4 symfony/dotenv:^6.4 symfony/form:^6.4 symfony/framework-bundle:^6.4 symfony/mailer:^6.4 symfony/security-bundle:^6.4 symfony/serializer:^6.4 symfony/string:^6.4 symfony/translation:^6.4 symfony/twig-bundle:^6.4 symfony/validator:^6.4 symfony/var-dumper:^6.4 symfony/yaml:^6.4 --with-all-dependencies




modification de cartservice

modification de config/services.yaml

scr/Controller/Admin/AdminUserController.php

scr/Controller/Admin/AdminCalendarAddUserController.php

src/EventDispatcher/PurchaseSuccessStock.php

Symfony 6.4 n’utilise plus les annotations Doctrine → il utilise les Attributs PHP

Désactiver les annotations Symfony et passer aux Attributs PHP
Dans config/packages/framework.yaml

Vérifie que tu désactives totalement les annotations :
annotations:
    enabled: true
  A PASSER SUR false
