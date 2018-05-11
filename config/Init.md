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


### Ajouter un gestionnaire de versions

1. Initialiser un nouveau repository Git dans le dossier de l'application avec la commande `git init` ;

2. Ajouter un repository distant : `git remote add origin <REMOTE_URL>` ;

3. Ajouter les fichiers tout juste générés à l'index : `git add .` ;

4. Faire un premier commit : `git commit -m "Initial commit"` puis pusher sur le repository distant : `git push origin master`.



[Retour à l'accueil](../README.md)


