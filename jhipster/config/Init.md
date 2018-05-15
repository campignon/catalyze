[Retour à l'accueil](../README.md)

# Création et mise en place d'un nouveau projet

### Utilisation du générateur Yeoman generator-jhipster

1. Ouvrir un terminal ;

2. Créer un dossier avec le nom de l'application à créer (`mkdir myapp`) ;

3. Se placer à l'intérieur de ce dossier (`cd myapp`) ;

4. Lancer la commande `yo jhipster` (**Node.js**, **Yeoman**, **Yarn** et **JHipster** doivent être préalablement installés) ;

5. Répondre aux questions posées par le générateur Yeoman de JHipster ;

6. Attendre la fin de la génération des sources et l'installation des dépendances via Yarn.

**Le projet est maintenant créé !**

Pour tester que tout est OK :

1. Depuis le dossier racine de l'application (*myapp* dans l'exemple), taper la commande `mvnw test` pour lancer les tests unitaires Java ;

2. Taper la commande `yarn test` pour lancer les tests UI avec KarmaJS.


### Ajouter un repository Git distant

Le générateur Yeoman de JHipster initialise un repository Git dans le dossier de l'application et fait un premier commit avec toutes les sources générées. Il ne manque plus qu'à ajouter un repository distant avec lequel communiquer :

1. Ajouter un repository distant : `git remote add origin <REMOTE_URL>` ;

2. Pusher sur le repository distant : `git push origin master`.

[Retour à l'accueil](../README.md)


