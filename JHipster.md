# Java / Angular Applications avec JHipster

## API

### Repositories 
Les **Repositories** ont le rôle d'aller effectuer une requête en base et de retourner les données récupérées. *Exemple : récupérer la liste des Recettes dans un annuaire de recettes de cuisine.*

Ce sont des interfaces qui étendent l'interface générique **JpaRepository<K, V>**.

**Query Methods**
Les **Query Methods** sont des signatures de méthodes déclarées dans un **Repository** et dont la déclaration permet à JPA de construire une requête à destination de la base de données.

### Services
Les **Services** contiennent la logique métier de l'application : ils demandent des données à un Repository et effectuent des opérations sur ces données.

### Resource Controllers (*Resource.java)
Les **Resource Controllers** (fichiers se terminant par Resource.java) exposent et gèrent les points d'entrée de l'API pour une ressource particulière. *Exemple : la classe ProductResource expose les points d'entrée concernant les produits de l'application. La requête de récupération des utilisateurs sera quant à elle traitée dans la classe UserResource.*

## Angular
