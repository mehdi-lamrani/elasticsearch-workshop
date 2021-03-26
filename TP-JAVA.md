# Elasticsearch Java client

Déployer des services Rest grâce à Spring Boot et Webflux Reactive pour réaliser les mêmes opérations avec l’API Java d’Elasticsearch en intéraction avec le même index TMDB.

### Création de l'index tmdb

1. Récupérer le fichiers de mapping de l'index ainsi que le dataset :
<img src="https://i.ibb.co/q79Bdbr/Screenshot-from-2021-03-26-09-34-19.png" width="60%">

https://i.ibb.co/q79Bdbr/Screenshot-from-2021-03-26-09-34-19.png

2. Créer l'index avec le mapping en utilisant l'API `_bulk`

### Créer une application SpringBoot

##### Project Reactor :
Reactor est l’implémentation des flux réactifs par Spring. Project Reactor est d’ailleurs intégré dans Spring 5, avec les WebFlux.<br/>
Project Reactor est directement embarqué avec Spring 5, et la bibliothèque est écrite en Java 8. Tandis que RxJava se doit de rester compatible avec Android et est écrit en Java 6.

Pour initialiser le projet Maven, rendez-vous sur https://start.spring.io.

1. Choisir la version 11 de Java.
2. Choisir la version 2.4.4 de Spring Boot.
3. Ajouter la d&pendecne "Spring Reactive Web".

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
