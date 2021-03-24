# Elasticsearch PHP client

<img src="https://i.ibb.co/mvf4N6j/Screenshot-from-2021-03-05-16-39-58.png" width="60%">

Réalisation d’une page en HTML et utiliser la librairie Elasticsearch/PHP pour :

* Afficher le contenu d’un index : celui de la base de données TMDB.

* Réaliser des recherches textuelles sur les titres et synopsys.

* Réaliser une agrégation pour retrouver les genres de films et replir la liste déroulate.

* Pouvoir faire une recherche multi-critères : Nom + genre.

Utiliser le libraire PHP officiel Elasticsearch :<br/>
https://www.elastic.co/guide/en/elasticsearch/client/php-api/current/index.html

Il existe d'autres librairies, comme décrit dans le lien ci dessous :<br>
https://jolicode.com/blog/quel-client-php-pour-elasticsearch

# Elasticsearch Java client

Déployer des services Rest grâce à Spring Boot et Webflux Reactive pour réaliser les mêmes opérations avec l’API Java d’Elasticsearch en intéraction avec le même index TMDB.

#####Project Reactor :
Reactor est l’implémentation des flux réactifs par Spring. Project Reactor est d’ailleurs intégré dans Spring 5, avec les WebFlux.
Project Reactor est directement embarqué avec Spring 5, et la bibliothèque est écrite en Java 8. Tandis que RxJava se doit de rester compatible avec Android et est écrit en Java 6.

### Créer une application SpringBoot

Pour initialiser le projet Maven, rendez-vous sur https://start.spring.io.

### Ouvrir le projet dans votre IDE préféré

Créer un projet Maven.

Créer des services REST en WebFlux Spring Reactive.

Suivre le tutoriel ci dessous :
https://spring.io/guides/gs/reactive-rest-service/

La partie "Create a WebClient" n'est pas nécessaire, les appels se feront en cURL ou sur un client REST comme Postman.

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
