# Elasticsearch PHP client

### Création de l'index tmdb

1. Récupérer le fichiers de mapping de l'index ainsi que le dataset :
<img src="https://i.ibb.co/q79Bdbr/Screenshot-from-2021-03-26-09-34-19.png" width="60%">

2. Créer l'index avec le mapping en utilisant l'API `_bulk`

### Application Web tmdb

<img src="https://i.ibb.co/mvf4N6j/Screenshot-from-2021-03-05-16-39-58.png" width="60%">

Réalisation d’une page en HTML et utiliser la librairie Elasticsearch/PHP pour :

* Afficher le contenu d’un index : celui de la base de données TMDB.

* Réaliser des recherches textuelles sur les titres et synopsys.

* Réaliser une agrégation pour retrouver les genres de films et replir la liste déroulate.

* Pouvoir faire une recherche multi-critères : Nom + genre.

Fonctionnalités optionnelles :

* Modifier la recherche pour la rendre en temps réel "search as you type".

* Gérer la pagination.<br/>
https://www.elastic.co/guide/en/elasticsearch/reference/current/paginate-search-results.html

* Trier les films par notes, obtenir les N films les mieux notés pour tel genre.

Il existe un certain nombres de librairies PHP pour intéragir avec Elasticsearch, comme décrit dans le lien ci dessous :<br>
https://jolicode.com/blog/quel-client-php-pour-elasticsearch

Utiliser la librairie PHP officiel Elasticsearch :<br/>
https://www.elastic.co/guide/en/elasticsearch/client/php-api/current/index.html

1. Installer PHP
```
$ sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2
```

2. Installer Composer<br/>
Composer est un logiciel gestionnaire de dépendances libre écrit en PHP. Il permet à ses utilisateurs de déclarer et d'installer les bibliothèques dont le projet principal a besoin.

```
$ php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

$ HASH="$(wget -q -O - https://composer.github.io/installer.sig)"
$ php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"

$ sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

$ composer
```
3. Installer Apache 2 :
```
sudo yum install -y httpd
```

4. Création du projet et ajout de la dépendance Elasticsearch :
```
$ mkdir movies-es-php
$ cd movies-es-php
$ composer require elasticsearch/elasticsearch

$ ls -l
```
* Le dossier vendor est le répertoire où sont stockées les dépendances du projet.
* Le fichier composer.lock contient la liste des packages installés avec les numéros de version.
* Le fichier composer.json decrit le projet PHP et toutes les dépendances PHP.

```
::::::::::::::
composer.json
::::::::::::::
{
    "require": {
        "elasticsearch/elasticsearch": "^7.12"
    }
}
```

5. Créer la page index.php et développer l'application.

6. Déploiement sous apache2 :
```
$ sudo cp -r ~/movies-es-php /var/www/html/

$ sudo vi /etc/httpd/conf.d/movies-es-php.conf
<VirtualHost *:80>
   ServerName movies-es-php
   DocumentRoot "/var/www/html/movies-es-php"
</VirtualHost>
```

7. Lancer le serveur et tester sur IP_ADDRESS:80
```
$ sudo systemctl restart httpd
```
