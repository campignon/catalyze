[Retour à l'accueil](../index.md)

# Création du schéma avec le JHipster Domain Language (JDL)
<br />

### Création d'une entité

Une entité se créée de la façon suivante :

```
entity <entity name> {
  <fields>
}
```

Entre les accolades on définit les attributs de l'entité (qui correspondent aux colonnes/champs qui seront créées en base). 

**IMPORTANT :** on ne met pas les champs des clés étrangères ici. En effet les relations entre les différentes entités seront définies à part à un autre endroit du fichier.

Un attribut se définit de la manière suivante :

`<field name> <type> [<validation>*]`

Par exemple pour définir l'attribut *nom* qui est une chaîne de caractères et qui est obligatoire, on écrira :

`nom String required`

Si on avait en plus voulu dire que sa taille ne peut pas être supérieur à 50 caractères, on aurait écrit :

`nom String required maxlength(50)`

#### Liste des types pour les attributs

Voici la liste des types possibles pour les attributs d'une entité ainsi que les validations disponibles pour chacun d'entre eux :

| Types         | Validations                             |
| --------------| ----------------------------------------|
| String        | required, minlength, maxlength, pattern |
| Integer       | required, min, max                      |
| Long          | required, min, max                      |
| BigDecimal    | required, min, max                      |
| Float         | required, min, max                      |
| Double        | required, min, max                      |
| Enum          | required                                |
| Boolean       | required                                |
| LocalDate     | required                                |
| ZonedDateTime | required                                |
| Blob          | required, minbytes, maxbytes            |
| AnyBlob       | required, minbytes, maxbytes            |
| ImageBlob     | required, minbytes, maxbytes            |
| TextBlob      | required, minbytes, maxbytes            |
| Instant       | required                                |

### Exemple d'une entité concrète

Imaginons que l'on créé une application pour un grand distributeur. Celui-ci vend des produits : il faut donc une entité Product.

La définition de celle-ci pourrait donner quelque chose comme ceci :

```
entity Product {
	name String required minlength(3) maxlength(255)
	description TextBlob required maxbytes(2048)
	limitedEdition Boolean required
	price Float
	stock Integer
}
```

*Explication* 

Un produit possède :

- obligatoirement un nom qui ne peut pas faire moins de 3 caractères ni plus de 255 caractères ;
- une description, requise aussi, qui est un TextBlob (le type pour les chaînes de caractères de longueur élevée) et qui ne doit pas dépasser les 2048 octets ;
- un booléen **limitedEdition** qui indique si le produit est une édition limité ou non ;
- le prix du produit qui est un flottant (le prix est rarement un entier) ;
- un entier qui indique la quantité en stock du produit.

### Création des relations entre les entités

[Retour à l'accueil](../index.md)