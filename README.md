````
   ___        _         _                                
  / _ \ _   _(_)_______(_)____                           
 | | | | | | | |_  /_  / |_  /                           
 | |_| | |_| | |/ / / /| |/ /                            
  \__\_\\__,_|_/___/___|_/___|    __  __ _          
 | __ )  __ _  ___| | __  / _ \  / _|/ _(_) ___ ___ 
 |  _ \ / _` |/ __| |/ / | | | || |_| |_| |/ __/ _ \
 | |_) | (_| | (__|   <  | |_| ||  _|  _| | (_|  __/
 |____/ \__,_|\___|_|\_\  \___/ |_| |_| |_|\___\___|
                                                         
````
# BTS-SIO-A-2022-Quizziz-BackOffice
Voici le modèle construit en cours pour réaliser la suite du projet QUIZZIZ

### SETUP PROJET
Installation du projet
````
$ composer install
````

Mettre un fichier .env
````
$ cp .env-exemple .env
````
Puis renseigner les variables d'environnement dans le fichier .env

Lien pour la base de donnée : [QUIZZIZ](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/98d1f42e-435a-4e0c-96b3-cebf3af6933a/bddqcm.sql?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220425%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220425T131517Z&X-Amz-Expires=86400&X-Amz-Signature=c504584fdf062ff4d022962e003f78179e886cd9342a1f5a569555c970458646&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22bddqcm.sql%22&x-id=GetObject)

Demarrer ton projet
````
$ composer start
````


### DEV PROJET
En cas de création ou de mise a jour des classes du projet, faire la commande de autoloader
````
$ composer dump-autoload 
````


### DEV STACK
| Version | Service                                                             | DESCRIPTION                      |
|:--------|:--------------------------------------------------------------------|:---------------------------------|
| ^5.4    | [vlucas/phpdotenv](https://packagist.org/packages/vlucas/phpdotenv) | Loads environment variables      |
| ^3.3    | [twig/twig](https://packagist.org/packages/twig/twig)               | Template Engine (VIEW couch)     |
| ^1.3    | [nikic/fast-route](https://packagist.org/packages/nikic/fast-route) | Router Engine (CONTROLLER couch) |
| ^8.0    | PHP Engine                                                          |                                  |  
| ^2.0    | Composer Dependency Manager                                         |                                  | 
|         | [Testing](https://codeception.com/)                                 |                                  |

### DOCUMENTATION
La base de donnée est dans le repertoire docs

#### USE CASE "/lister"

#### 1/ Demande HTTP via le browser
Le user envoie une requête "Demande" HTTP via un browser, voici l'adresse http://localhost/lister
#### 2/ Réception HTTP
La couche CONTROLLER (via FastRoute) réceptionne la requête HTTP -> /lister \
et l'envoie sur le bon controller -> Quizz\Controller\Questionnaire\ListController 
#### 3/ Couche MODEL
La couche MODEL se charge de gestion des données 
#### 4/ La database
La database est en relation avec la couche MODEL
#### 5/ Traitement de donnée
Une fois le traitement de données via la couche MODEL, les données sont envoyées dans un moteur de template (template angine) -> Twig
#### 6/ Couche VIEW
Dans la couche VIEW, les données sont placées dans les composants des templates HTML puis transmis au user via le protocole HTTP
#### 7/ Reponse HTTP via le browser
Le user réceptionne la requête "Reponse" pour que le browser puisse interpréter le code d'interface (HTML/CSS/JS) avec sa runtime local
