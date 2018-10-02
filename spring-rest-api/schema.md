## Création d'une entité

Une entité est un simple POJO avec l'annotation JPA `@Entity`.

Exemple avec une entité **Book** représentant un livre :

```java
package com.example.mypackage;

@Entity
public class Book { }
```

## Contraintes sur les attributs

Pour ajouter des contraintes sur les attributs d'une entité, on utilise conjointement l'annotation JPA `@Column` pour définir des contraintes de base de données et les annotations de la JSR 303 pour définir des contraintes sur le bean à l'intérieur de l'application.

### Valeur non-nullable

Pour interdire à un attribut de posséder une valeur nulle, on utilise les annotations : `@NotNull` et `@Column(nullable = false)`.



