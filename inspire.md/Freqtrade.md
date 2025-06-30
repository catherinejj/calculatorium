Analyse du Projet GitHub : Freqtrade

Gestion des Branches

Le projet utilise trois types de branches :
- develop : branche principale de développement, contient les nouvelles fonctionnalités.
- stable : contient la dernière version stable pour la production.
- feat/* : branches de fonctionnalités spécifiques, fusion dans develop une fois complètes.

Les Pull Requests doivent être soumises uniquement vers develop.

La documentation donne des directives claires.


Méthode de Gestion de Projet

- Présence du fichier CONTRIBUTING.md qui détaille comment contribuer :
  - Comment lancer les tests unitaires (pytest)
  - Comment vérifier que le code est bien formaté (ruff, mypy)
- Des hooks Git sont recommandés pour éviter les erreurs au moment du commit.
- Tous les changements doivent être relus, même par les membres expérimentés.
- La communauté est active et les rôles évoluent en fonction de l'implication dans le projet.
    - Il est possible de devenir "Committer", puis "Core Committer" avec plus d’accès, selon la qualité, la régularité et l'attitude dans le projet.

Gestion des versions et environnement

Le projet Freqtrade utilise un système de versionning clair (visible dans pyproject.toml, via les releases GitHub et les tags Git) pour suivre l’évolution des fonctionnalités et corriger les bugs de manière contrôlée. Chaque release est accompagnée d’un changelog détaillé. 

Il repose également sur Docker pour garantir un environnement cohérent entre les développeurs, que ce soit pour les tests, le développement ou le déploiement. Cela permet d’éviter les problèmes liés à la configuration locale et de maintenir une base de code stable.

Gestion des Issues

Les issues sont ouvertes à tous et la communauté peut y participer :
- Pour signaler des bugs
- Pour proposer de nouvelles fonctionnalités
- Pour poser des questions

Organisation des issues :
- Créer une PR vers develop, jamais vers stable !!
- Toute nouvelle fonctionnalité doit avoir :
  - des tests unitaires
  - un code conforme à PEP8
  - une documentation intégrée dans la PR
- Les PR peuvent être marquées comme [WIP] si elles ne sont pas terminées.
- Des labels (bug, question, etc.) permettent de mieux trier les sujets.

Une documentation claire est dispo, avec des liens vers des serveurs communautaires comme Discord, pour faciliter l’échange d’info et éviter les doublons.

Conclusion

Freqtrade est bien structuré et très collaboratif :
- Une gestion des branches propre
- Un système de contribution rigoureux
- Une vraie communauté autour du projet
- Une doc accessible pour tous les niveaux

Lien : https://github.com/freqtrade/freqtrade
