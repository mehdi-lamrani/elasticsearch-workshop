---
#### 02. Envoyer des requêtes avec cURL (Elastic Cloud)
---

- ElasticSearch permet d'accéder à des requêtes API de deux ordres : 
     - Les requêtes applicatives (relatives aux applications ES)
     - Les requetes administratives (relatives à la gestion des déploiements)
     
---
##### a. Envoyer des requêtes applicatives (Elastic Cloud Applications)
---

- Aller à https://cloud.elastic.co/home

![es-deployment-list](https://user-images.githubusercontent.com/28993140/182843852-17285c83-dff7-4225-bdee-c2f751592bbe.png)

- Noter le endpoint

![es-deploy-endpoint](https://user-images.githubusercontent.com/28993140/182845819-67c250e5-6c24-4288-a58a-cc34116bb691.png)

- Aller au Stack Management dans Kibana

![es-stack mgmt](https://user-images.githubusercontent.com/28993140/182843868-78987cb2-67c5-4058-a565-e6c70b79f865.png)

![es-api-keys](https://user-images.githubusercontent.com/28993140/182843864-9c0f955a-225b-4745-bb49-5219a41007b7.png)

![es-api-keys-2](https://user-images.githubusercontent.com/28993140/182843862-84a549d8-2694-4bfd-8353-4361edb23882.png)

![es-api-keys-3](https://user-images.githubusercontent.com/28993140/182843857-0c326710-44ab-46ce-ba72-3e6d593c5325.png)

![es-api-keys-4](https://user-images.githubusercontent.com/28993140/182843854-70128494-d72c-42df-87da-04e36cad8ea7.png)

- Depuis un terminal : 

```
curl -k -X GET -H "Authorization: ApiKey Rm54OGFJSUJFLXIteWhyTThXXXXXXXXXXXXXXXXXXTd1dFc2ZMVzRuamRfQQ==" https://my-deployment-b4ebde.es.us-east-1.aws.found.io:9243/_cat/indices?v 
```


![es-curl](https://user-images.githubusercontent.com/28993140/182844268-5964430b-1a18-4a25-aae4-ff8403e185fa.png)


---
##### b. Envoyer des requêtes d'administration (Elastic Service)
---
- Aller à https://cloud.elastic.co/home

![es-deployment-list](https://user-images.githubusercontent.com/28993140/182843852-17285c83-dff7-4225-bdee-c2f751592bbe.png)

Noter le endpoint

![es-deploy-endpoint](https://user-images.githubusercontent.com/28993140/182845819-67c250e5-6c24-4288-a58a-cc34116bb691.png)

![es-deploy-features](https://user-images.githubusercontent.com/28993140/182843847-98dd459a-95d4-444c-8486-bb6632720fda.png)

![es-deploy-api-keys](https://user-images.githubusercontent.com/28993140/182843845-94b3aa9f-8647-42c7-ad66-9912f6d24044.png)

![es-deploy-api-keys-2](https://user-images.githubusercontent.com/28993140/182843838-fd631648-d8b4-493b-b138-242c05430cd9.png)

![es-deploy-api-keys-3](https://user-images.githubusercontent.com/28993140/182843834-add51f37-addb-4e27-8680-664084991c3e.png)

![es-deploy-api-keys-4](https://user-images.githubusercontent.com/28993140/182843828-8d433a0d-0e09-4609-aef3-71d8dbc49b85.png)

- Depuis un terminal : 

```
curl -k -X GET -H "Authorization: ApiKey RjRCeWFJSUJ6WGkXXXXXXXXXXXXdVZBOTVTSUd6NmV4ci1BZWZLZw==" https://api.elastic-cloud.com/api/v1/deployments```
```


---
#### 02. Importer des données avec cURL (Linux)
---
        

<details>
<summary>TP</summary>
        
Le but ici est d'importer un fichier directement depuis la ligne de commande en utilisant l'utilitaire cURL
        
:warning: :warning: :warning: ATTENTION ! 
Cette partie de l'exercice nécessite d'avoir accès à un terminal linux
Si ce n'est pas le cas, passez votre chemin :)

Rappel :
* Le Content-Type doit être application/**x-ndjson**.
* Chaque ligne doit se terminer par un \n ou \r\n, dernière ligne incluse !
* Une action qui plante n'affectera pas les autres actions.
* L'API Bulk renvoie un rapport détaillé pour toutes les actions.
* L'API Bulk est plus efficace que l'envoi de plusieurs actions individuelles (réduction de traffic réseau).

##### :arrow_forward: Naviguer vers le dossier ou se trouve le fichier bulk

```
$ cd /path/to/data/file/directory
```

A noter que le nom de l'index n'est pas défini dans le fichier bulk, il faudra le spécifier dans le path de la requête HTTP.

##### :arrow_forward: Importer les données dans le cluster local

```
A compléter...
```

Il y a 1000 documents dans le fichier json. Vérifions que tout a été chargé dans l'index.

```
GET /products/_count
```

<img src="https://i.ibb.co/Jnv6G5q/027-Screenshot-2021-03-16-Elastic-Kibana.png" width="20%">

</details>

 
