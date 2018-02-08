## Récupérer les données en base grâce aux Repositories
<br />
Les **Repositories** (ou **Spring Data Repositories**) ont le rôle d'aller effectuer une requête en base et de retourner les données récupérées. *Exemple : récupérer la liste des Recettes dans un annuaire de recettes de cuisine.*

Ce sont des interfaces qui étendent l'interface générique **JpaRepository<K, V>**.

### Query Methods

Les **Query Methods** sont des signatures de méthodes déclarées dans un **Repository** et dont la déclaration permet à JPA de construire une requête à destination de la base de données.

Pour savoir comment travailler avec les **Spring Data Repositories** et utiliser les **Query Methods**, se référer à la documentation suivante : [Working with Spring Data Repositories](https://docs.spring.io/spring-data/jpa/docs/1.5.0.RELEASE/reference/html/repositories.html).