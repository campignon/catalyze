### Services

Les **Services** contiennent la logique métier de l'application : ils demandent des données à un Repository et effectuent des opérations sur ces données.
Ils doivent posséder l'annotation *@Transactional* sur les méthodes *public* 