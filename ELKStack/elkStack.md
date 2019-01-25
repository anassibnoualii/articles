
# Introduction
ELK est une solution open source constituée de trois logiciels : Elasticseach, Logstash, Kibana. 

Cette solution a été développée par Elastic (https://www.elastic.co/) et se nomme aujourd’hui Elastic Stack.

Le tout permet d’entrer des logs pour les parser et les filtrer (Logstash), de les stocker dans un moteur de recherche puissant qui peut gérer de grands volumes de données (Elasticsearch) et d’en faire des tableaux de bord qui comportent des graphiques, tableaux, camemberts et autres. Mais aussi de faire des recherches précises afin de trouver les informations voulues (Kibana). Cet outil est donc très pratique pour visualiser et rechercher des logs et nous évite de lire les fichiers en dur.

![ELK Stack](elk/elkStack.png)


# Installation
Installer les éléments suivants comme indiqué sur la documentation officielle (en ajustant la version si nécessaire) :

## 1. ELASTICSEARCH
<img src="elk/elasticsearch.png" width="100" height="100">

1. [Télécharger le fichier zip d'Elasticsearch 6.5.3 de la page de téléchargement.](https://www.elastic.co/downloads/elasticsearch)
2. Extraire le fichier zip dans un emplacement, par exemple.
``` C:\Program Files ``` 

3. Ouvrir une invite de commande en tant qu'administrateur et accédez au répertoire contenant les fichiers extraits, par exemple:
``` cd C:\Program Files\elasticsearch-6.5.3\bin ```

4. Lancer Elasticsearch du même dossier avec la commande  ``` elasticsearch.bat ```
5. Pour s'assuer du lancement d'elasticsearch on occède à l'url suivant  ``` http://127.0.0.1:9200 ``` on doit avoir un résultat qui resemble à l'object suivant
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

6. pour plus d'info voici [le lien vers la  documentation  d'Elasticsearch](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-elastic-stack.html#install-elasticsearch)

## 2. FILEBEAT

1. [Télécharger le fichier zip de Filebeat 6.5.3 de la page de téléchargement.](https://www.elastic.co/downloads/beats/filebeat)
2. Extraire le fichier zip dans un emplacement par exemple :
``` C:\Program Files ``` 
3. Ouvrir une invite de commande en tant qu'administrateur et accédez au répertoire contenant les fichiers extraits, par exemple:
``` cd C:\Program Files\Filebeat ```

4. configuration:

    Filebeat est un stash léger qui permet de collecter les données et les envoyer vers logstash.
    Il a également un fichier de configuration qui fonctionne à peu près comme celui de logstash 
- Dans le fichier filebeat.yml:
    -	Définir   le chemin des logs
    ```
    paths:
        - C:\elkstack\logs.log
    ```
    -	Indiquer  l’emplacement du logstash
    ```
    output.logstash:
      hosts: ["localhost:5044"]
    ```
5. Lancer Filebeat du même dossier avec la commande suivante : ``` filebeat -e -c filebeat.yml ```.

6. pour plus d'info voici [le lien vers la documentation de Filebeat](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-elastic-stack.html#install-beats)


## 3. LOGSTASH
<img src="elk/logstash.png" width="100" height="100">

1. [Télécharger le fichier zip de Logstash 6.5.3 de la page de téléchargement.](https://www.elastic.co/downloads/logstash)
2. Extraire le fichier zip dans un emplacement par exemple :  
``` C:\Program Files ``` 

3. Ajouter la configuration:

      Le fichier de configuration de logstash est un pipeline il se compose d’un input, filter et output
      Dans le input on spécifie la source et le type de donnée qu’on va passer à logstash 
      Dans notre cas on va travailler avec filebeat donc la config est la suivante :
```
input {  
  beats {
    port => 5044
  }
}
La partie filter permet de parser les logs et les structurer sous forme de json
filter {  
}
La partie output permet de destiner les sortie où on veut envoyer les données traitées .
On peut spécifier plusieurs sorties : 
output {
  elasticsearch {
    hosts => ["localhost:9200"]
  }
  stdout { codec => rubydebug }
}
```

4. Lancer depuis le dossier ``` C:\Program Files\logstash\bin ```  la commande ``` logstash -f ../config/config.conf ```

5. Pour plus d'info voici  [le lien vers la documentation de Logstach](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-elastic-stack.html#install-logstash)

## 4. KIBANA
<img src="elk/kibana.png" width="100" height="100">

1. [Télécharger le fichier zip de Kibana 6.5.3 de la page de téléchargement.](https://www.elastic.co/downloads/kibana)
2. Extraire le fichier zip dans un emplacement, par exemple  
``` C:\Program Files ``` 
3. Ouvrir une invite de commande en tant qu'administrateur et accédez au répertoire contenant les fichiers extraits, par exemple:
``` cd C:\Program Files\kibana-6.5.3-windows ```
4. Lancer Filebeat du même dossier ``` bin\kibana.bat ```
5. Pour s'assuer de lancement de kibana on lance l'url suivant  ``` http://127.0.0.1:5601 ``` on doit voir son interface.

6. Pour plus d'info voici [le lien vers la documentation de Kibana](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-elastic-stack.html#install-kibana) .
 
# Architecture 
![ELK Stack](elk/archi.png)
