## Gestion de la couche métier avec les Services
<br />

Les **Services** contiennent la logique métier de l'application : ils demandent des données à un Repository et effectuent des opérations sur ces données.
Ils doivent posséder l'annotation *@Transactional* sur les méthodes *public* (c'est-à-dire les méthodes qui vont être appelées depuis les contrôleurs et dont les opérations doivent appartenir à la même transaction).