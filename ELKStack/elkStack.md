# Introduction
ELK est une solution open source constituée de trois logiciels : Elasticseach, Logstash, Kibana. Cette solution a été développée par Elastic (https://www.elastic.co/) et se nomme aujourd’hui Elastic Stack.

Le tout permet d’entrer des logs pour les parser et les filtrer (Logstash), de les stocker dans un moteur de recherche puissant qui peut gérer de grands volumes de données (Elasticsearch) et d’en faire des tableaux de bord qui comportent des graphiques, tableaux, camemberts et autres. Mais aussi de faire des recherches précises afin de trouver les informations voulues (Kibana). Cet outil est donc très pratique pour visualiser et rechercher des logs et nous évite de lire les fichiers en dur.
![ELK Stack](images/elkstack.jpg)


# Installation
Installer les éléments suivants comme indiqué sur la documentation officielle (en ajustant la version si nécessaire) :

### ELASTIC SEARCH

[Télécharger Elasticsearch](https://www.elastic.co/downloads/past-releases/elasticsearch-5-2-1)

[Documentation vers Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/5.2/_installation.html)

### FILEBEAT

[Télécharger Filabeat](https://www.elastic.co/downloads/past-releases/filebeat-5-2-1)

[Documentation vers Filebeat](https://www.elastic.co/guide/en/beats/filebeat/5.2/filebeat-installation.html)

### LOGSTASH

[Télécharger Logstach](https://www.elastic.co/downloads/past-releases/logstash-5-2-1)

[Documentation versLogstach](https://www.elastic.co/guide/en/logstash/5.2/installing-logstash.html)

### KIBANA

[Télécharger Kibana](https://www.elastic.co/downloads/past-releases/kibana-5-2-1
)

[Documentation vers Kibana](https://www.elastic.co/guide/en/kibana/5.2/install.html)
 
# Architecture 
![ELK Stack](images/archi.png)