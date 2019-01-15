# delivery
API delivery

L’objectif de ce micro-service est de pouvoir tracer la livraison d’un colis que l’utilisateur aurait acheté sur un site de e-commerce.
L’API développé en PHP doit pouvoir ajouter un point de localisation du colis, la date et l’heure. Une liste de toutes les positions connues du produit doit s’afficher en indiquant son numéro unique. Le client développé en PHP doit pouvoir consommer les contrôleurs de l’API. 
Afin de mettre en œuvre ces deux parties, nous devons développer une application comprenant deux pages :

    • Une page d’accueil qui contient un formulaire demandant d’entrer le numéro de colis. En validant, la page affiche les dernières positions connues. Une carte montrant la dernière localisation s’affiche également en utilisant le service de cartographie de Google Maps.
    
    • Une page qui permet d’ajouter un nouveau point de localisation. 
    
Nous avons choisi de développer l’API avec le framework Symfony 4 et de l’ORM Doctrine ainsi que FOSRestBundle. Nous avons décidé d’utiliser le Framework Bootstrap et Symfony 4 pour l’application. Le client utilise du PHP et la librairie GuzzleHTTP. 

Pour l’architecture, nous avons quatre dossiers : 

    • delivery-api qui contient l’API, 
    • delivery-client qui contient le client, 
    • delivery-common qui contient les composants communs entre l’API et le client,
    • delivery-app qui contient l’application. 
    
Le dossier delivery-api contient un dossier « src » regroupant la gestion de l’API (Controller, Migrations).

Le dossier delivery-client contient :

    • un dossier vendor regroupant les librairies utilisées,
    • un dossier src contenant un contrôleur qui utilise l’API. 
    
Le dossier delivery-common contient :

    • un dossier vendor regroupant les librairies utilisées, 
    • un dossier src contenant un dossier Entity.
    
Le dossier delivery-app contient :

    • un dossier vendor regroupant les librairies utilisées, 
    • un dossier src contenant un dossier Controller, 
    • un dossier public contenant la feuille de style rangée dans le dossier css et les images rangées dans le dossier img,
    • un dossier template contenant les pages HTML au format TWIG. 
    
Instructions :    
      
    • Avoir un dossier delivery contenant les quatre livrables puis lancer la commande composer:install sur chaque dossier.
      
    • Définir vos identifiants de connexion en créant le fichier .env.local à la racine du dossier delivery-api sous ce format : DATABASE_URL=mysql://root:password@127.0.0.1:3306/delivery
      
    • Créer la base de données avec la commande php bin/console doctrine:database:create puis installer le contenu avec la commande php bin/console doctrine:migrations:migrate
      
    • Lancer la commande php bin/console server:run sur le dossier delivery-app puis sur delivery-api 
      
    • L'application devrait être accessible à l'adresse http://127.0.0.1:8000/ et l'API à cette adresse http://127.0.0.1:8001/
      
    • WampServer doit être opérationnel afin de faire fonctionner correctement le projet. 

Nota bene : Il est possible que la carte utilisant la technologie de Google Maps ne s’affiche pas correctement ou affiche un filigrane avec le message “for development purposes only”.

L’utilisation de l’API est devenue payante et aucune carte bancaire a été relié à la clé utilisée.
Par ailleurs, le nombre de chargement de la carte est limité à une par jour tant qu’une source de facturation n’est pas saisie.
