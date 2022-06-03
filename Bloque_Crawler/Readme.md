# BLOQUAGE_CRAWLERS


## 1.Recherchez dans le fichier journal Apache une liste d'agents utilisateurs.

$ cat /var/log/apache2/access.log 

## 2.Entrez dans le dossier apache2 avec le commande :

$ cd /var/log/apache2

## 3.Modifié à l'aide un éditeur (ex:vim ou nano) :

$ vim +x blockage.sh

Ou

$ nano blockage.sh

## 4. Entre le script:

$ !/bin/sh

L'utilisation principale de "awk" est de décomposer chaque ligne d'un fichier en "champs" ou "colonnes" à l'aide d'un séparateur prédéfini. Étant donné que chaque ligne du fichier journal est basée sur le format standard, nous pouvons faire beaucoup de choses assez facilement.

### 5.L'étape suivante consiste à identifier les pages/fichiers qui génèrent les différents codes. La commande suivante résumera les requêtes 404 ("Not Found") :

$ list all 404 requests
awk '($9 ~ /404/)' combined_log

$ summarise 404 requests

awk '($9 ~ /404/)' combined_log | awk '{print $9,$7}' | sort 

### 6.Modifiez les valeurs USER-AGENT pour refléter vos besoins. 

$ RewriteCond %{HTTP_USER_AGENT} (gumgum-bot|postmanruntime|ag_dm_spider|scrapy|chimebot) [NC]

### Redémarrez le service Apache 

$ service apache2 restart


#### 

Félicitations! Vous avez appris à configurer le serveur Apache pour refuser l’accès aux utilisateurs et Crawlers.👏👏

 



