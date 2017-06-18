# Run

## Informations

### Général

- Date du dernier audit de sécurité : DD/MM/YYYY
- Sensibilité des données : Cx
- Accessibilité : GAIA / SAFE / GAIA + SAFE
- Chef de projet : John Doe
- Product Owner : John Doe

## Maintenabilité

### Début du projet

- [ ] L'équipe a passé 30 minutes avec le RUN qui a expliqué la checklist
- [ ] Dans le cas d'une application utilisant mongodb, l'auto-reconnect est configuré — [Exemple de commit pour configurer l'auto-reconnect MongoDB](https://github.com/theodo/pepiniere-dashbook/pull/397/commits/3de3a444e3af1b2a4c7c8ba961d00b35c1130564)

### Tout au long du projet

- [ ] J'ai une documentation qui explique comment charger les fausses données (et j'ai aussi les fausses données dans le repository)
- [ ] J'ai une procédure d'installation du projet dans la documentation
- [ ] Je ne stocke pas de fichiers non temporaires sur le file system (pour le load-balancing)
- [ ] Les logs sont permutés régulièrement en homologation et production (viser une conservation de 3 mois, adapter selon la volumétrie)
- [ ] L'application n'écrit pas dans `/tmp` (au besoin, utiliser `$TNU_ROOT_DIRECTORY/tmp` qui est fait pour ça)
- [ ] L'application efface les fichiers temporaires qu'elle crée
- [ ] Dans le cas d'une application lançant des scripts régulièrement, j'ai un mécanisme d'alerte (mail) donnant des informations utiles au Run (exemple : mail avec des logs), en homologation et en production
- [ ] J'ai une "liste des interfaces" de l'application (Flux TOM, APIs que l'application sert ou consomme, fédérateur de messagerie ...)
- [ ] Tous les documents internes envoyés (Fédérateur de messagerie, Ouverture de route, Flux TOM, Inscription SAFE) sont dans Sharepoint
- [ ] Tous les points méritant une attention particulière sont évoqués dans la partie qui suit

### Après la première MEP

- [ ] Tous les composants de mon application sont équipés d'un health-check (node, DB, elasticsearch, ...) :
  - [ ] Le module [health-check](https://github.com/FastIT/health-check) est mis en place
  - [ ] Un job tourne en production pour lancer le health-check toutes les 15 minutes
- [ ] J'ai une procédure qui explique comment mettre en homologation / production
- [ ] La base de données est sauvegardée quotidiennement en production
- [ ] La base de données est purgée régulièrement en homologation et production (pas d'accumulation de données). Par exemple, dans le cas d'une piste d'audit, seuls les n derniers mois sont conservés.

### Fin de projet

- [ ] J'ai suivi la procédure d'installation depuis le début et je n'ai rencontré aucun problème
- [ ] J'ai lancé les tests ils passaient **localement** et **sur la CI**
- [ ] Le RUN a assisté à la cérémonie de clôture pour expliquer au PO le fonctionnement du RUN
- [ ] Tous les environnements sont iso (pas de commit surprise laissé pour la prochaine MEP)
- [ ] Le board trello est propre (pas de ticket laissé en suspens dans Doing, Blocked, ...)
- [ ] J'ai fixé les versions des sous-dépendances du projet :
  - [ ] j'ai fixé les versions des sous-dépendances npm à l'aide de la commande `npm shrinkwrap`
  - [ ] j'ai fixé les versions des sous-dépendances Bower en committant tous les modules

## Points importants
