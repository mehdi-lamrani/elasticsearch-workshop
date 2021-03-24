# Elasticsearch PHP client

### Création de l'index tmdb

1. Récupérer le fhichiers de mapping de l'index ainsi que le dataset :
```
wget https://file.io/O51u3O29GiHu -O tmdb.json

wget https://file.io/UkUb2iyr3ToC -O tmdb-mapping.json
```

2. Créer l'index avec le mapping en utilisant l'API `_bulk`

<img src="https://i.ibb.co/mvf4N6j/Screenshot-from-2021-03-05-16-39-58.png" width="60%">

Réalisation d’une page en HTML et utiliser la librairie Elasticsearch/PHP pour :

* Afficher le contenu d’un index : celui de la base de données TMDB.

* Réaliser des recherches textuelles sur les titres et synopsys.

* Réaliser une agrégation pour retrouver les genres de films et replir la liste déroulate.

* Pouvoir faire une recherche multi-critères : Nom + genre.

Il existe d'autres librairies PHP pour intéragir avec Elasticsearch, comme décrit dans le lien ci dessous :<br>
https://jolicode.com/blog/quel-client-php-pour-elasticsearch

Utiliser la librairie PHP officiel Elasticsearch :<br/>
https://www.elastic.co/guide/en/elasticsearch/client/php-api/current/index.html

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

2. Créer des services REST en WebFlux Spring Reactive.

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
