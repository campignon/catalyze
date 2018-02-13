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

Voici la liste des types possibles pour les attributs d'une entité :

| Types         |
| --------------|
| String        |
| Integer       |
| Long          |
| BigDecimal    |
| Float         |
| Double        |
| Enum          |
| Boolean       |
| LocalDate     |
| ZonedDateTime |
| Blob          |
| AnyBlob       |
| ImageBlob     |
| TextBlob      |
| Instant       |