
# Introduction
ELK est une solution open source constituée de trois logiciels : Elasticseach, Logstash, Kibana. Cette solution a été développée par Elastic (https://www.elastic.co/) et se nomme aujourd’hui Elastic Stack.

Le tout permet d’entrer des logs pour les parser et les filtrer (Logstash), de les stocker dans un moteur de recherche puissant qui peut gérer de grands volumes de données (Elasticsearch) et d’en faire des tableaux de bord qui comportent des graphiques, tableaux, camemberts et autres. Mais aussi de faire des recherches précises afin de trouver les informations voulues (Kibana). Cet outil est donc très pratique pour visualiser et rechercher des logs et nous évite de lire les fichiers en dur.

![ELK Stack](https://github.com/anassibnoualii/articles/blob/master/ELKStack/images/elkStack.png)


# Installation
Installer les éléments suivants comme indiqué sur la documentation officielle (en ajustant la version si nécessaire) :

### ELASTICSEARCH
<img src="images/elasticsearch.png" width="100" height="100">

1. [Télécharger le fichier zip d'Elasticsearch 6.5.3 de la page de téléchargement.](https://www.elastic.co/downloads/elasticsearch)
2. Extraire le fichier zip dans l'emplacement 
``` C:\Program Files ``` 
(de préference :D )
3. Ouvrez une invite de commande en tant qu'administrateur et accédez au répertoire contenant les fichiers extraits, par exemple:
``` cd C:\Program Files\elasticsearch-6.5.3 ```

4. Lancer Elasticsearch du même dossier ``` bin\elasticsearch.bat ```
5. Pour s'assuer de lancement d'elasticsearch on lance l'url suivant  ``` http://127.0.0.1:9200 ``` on doit avoir un résultat qui resemple à l'object suivant
``` JSON
{
  "name" : "QtI5dUu",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "DMXhqzzjTGqEtDlkaMOzlA",
  "version" : {
    "number" : "6.5.3",
    "build_flavor" : "default",
    "build_type" : "tar",
    "build_hash" : "00d8bc1",
    "build_date" : "2018-06-06T16:48:02.249996Z",
    "build_snapshot" : false,
    "lucene_version" : "7.3.1",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}
```

6. pour plus d'info voici une [Documentation vers Elasticsearch](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-elastic-stack.html#install-elasticsearch)

### FILEBEAT

1. [Télécharger le fichier zip de Filebeat 6.5.3 de la page de téléchargement.](https://www.elastic.co/downloads/beats/filebeat)
2. Extraire le fichier zip dans l'emplacement 
``` C:\Program Files ``` 
(de préference :D )
3. Ouvrez une invite de commande en tant qu'administrateur et accédez au répertoire contenant les fichiers extraits, par exemple:
``` cd C:\Program Files\Filebea ```

4. Lancer Filebeat du même dossier ``` .\install-service-filebeat.ps1 ```
5. configuration (TODO)

6. pour plus d'info voici une [Documentation vers Filebeat](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-elastic-stack.html#install-beats)


### LOGSTASH
<img src="images/logstash.png" width="100" height="100">

1. [Télécharger le fichier zip de Logstash 6.5.3 de la page de téléchargement.](https://www.elastic.co/downloads/logstash)
2. Extraire le fichier zip dans l'emplacement 
``` C:\Program Files ``` 
(de préference :D )
3. ajout de configuration ( TODO)


4. pour plus d'info voici une [Documentation versLogstach](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-elastic-stack.html#install-logstash)

### KIBANA
<img src="images/kibana.png" width="100" height="100">

1. [Télécharger le fichier zip de Kibana 6.5.3 de la page de téléchargement.](https://www.elastic.co/downloads/kibana)
2. Extraire le fichier zip dans l'emplacement 
``` C:\Program Files ``` 
(de préference :D )
3. Ouvrez une invite de commande en tant qu'administrateur et accédez au répertoire contenant les fichiers extraits, par exemple:
``` cd C:\Program Files\kibana-6.5.3-windows ```
4. Lancer Filebeat du même dossier ``` bin\kibana.bat ```
5. Pour s'assuer de lancement de kibana on lance l'url suivant  ``` http://127.0.0.1:5601 ``` on doit voir son interface

6. pour plus d'info voici une [Documentation vers Kibana](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-elastic-stack.html#install-kibana) .
 
# Architecture 
![ELK Stack](images/archi.png)