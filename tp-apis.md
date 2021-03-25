# Elasticsearch PHP client

### Création de l'index tmdb

1. Récupérer le fhichiers de mapping de l'index ainsi que le dataset :
```
wget https://file.io/O51u3O29GiHu -O tmdb.json

wget https://file.io/UkUb2iyr3ToC -O tmdb-mapping.json
```

2. Créer l'index avec le mapping en utilisant l'API `_bulk`

### Application Web tmdb

<img src="https://i.ibb.co/mvf4N6j/Screenshot-from-2021-03-05-16-39-58.png" width="60%">

Réalisation d’une page en HTML et utiliser la librairie Elasticsearch/PHP pour :

* Afficher le contenu d’un index : celui de la base de données TMDB.

* Réaliser des recherches textuelles sur les titres et synopsys.

* Réaliser une agrégation pour retrouver les genres de films et replir la liste déroulate.

* Pouvoir faire une recherche multi-critères : Nom + genre.

Il existe un certain nombres librairies PHP pour intéragir avec Elasticsearch, comme décrit dans le lien ci dessous :<br>
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

# Elasticsearch Java client

Déployer des services Rest grâce à Spring Boot et Webflux Reactive pour réaliser les mêmes opérations avec l’API Java d’Elasticsearch en intéraction avec le même index TMDB.

##### Project Reactor :
Reactor est l’implémentation des flux réactifs par Spring. Project Reactor est d’ailleurs intégré dans Spring 5, avec les WebFlux.
Project Reactor est directement embarqué avec Spring 5, et la bibliothèque est écrite en Java 8. Tandis que RxJava se doit de rester compatible avec Android et est écrit en Java 6.

### Créer une application SpringBoot

Pour initialiser le projet Maven, rendez-vous sur https://start.spring.io.

1. Choisir la version 11 de Java.
2. Choisir la version 2.4.4 de Spring Boot.
3. Ajouter l& d&pendecne "Spring Reactive Web".

### Ouvrir le projet dans votre IDE préféré

1. Importer le projet en tant que projet Maven.

2. Ajouter la dépendance Maven Elasticsearch :
```
		<dependency>
			<groupId>org.elasticsearch.client</groupId>
			<artifactId>elasticsearch-rest-high-level-client</artifactId>
			<version>7.11.1</version><!--$NO-MVN-MAN-VER$ -->
		</dependency>
```

3. Créer des services REST en WebFlux Spring Reactive.

Suivre le tutoriel ci dessous :
https://spring.io/guides/gs/reactive-rest-service/

La partie "Create a WebClient" dans le tutoriel n'est pas nécessaire, les appels se feront en cURL ou sur un client REST comme Postman.

### Les services REST à créer

* Récupérer les films de l'index, le paramètre size permet de limiter le nombre de films:
```
http://localhost:8080/movies?size=100
```

* Retrouver un film à partir de son identifiant.
```
http://localhost:8080/movies/33627
```

* Réaliser des recherches textuelles sur les titres et synopsys.
```
http://localhost:8080/movies/search/shark
```

* Pouvoir faire une recherche multi-critères.
```
http://localhost:8080/movies/search/Enjoy antisocial?genre=Fantasy
```

* Calculer le moyenne des notes pour un genre de films :
```
http://localhost:8080/movies/ratings/average?genre=Animation
```

* Récupérer le classement des dix films les mieux notés, genre de films est facultatif :
```
http://localhost:8080/movies/ratings/topten?genre=Animation
```

* La répartition des films par notes.
```
http://localhost:8080/movies/ratings/histogram
```

* Réaliser une agrégation pour retrouver les genres de films.
```
http://localhost:8080/genres
```
