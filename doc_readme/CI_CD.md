## CI/CD - Intégration Continue et Déploiement Continu

### Outils utilisés

- GitHub Actions pour automatiser le pipeline

### Pipeline d’intégration continue (CI)

- Déclenchement automatique à chaque push sur `dev`, `staging`,`qa`,`main`
- Exécution des tests unitaires pour vérifier que rien ne casse
- Analyse du code (linting) pour respecter les standards

### Pipeline de déploiement continu (CD)

- Après succès du CI, build automatique de l’application
- Déploiement automatique sur l’environnement **qa** après fusion sur `dev`
- Déploiement en production après validation manuelle et fusion sur `main`
> En cas d'echec de build, la derniere version fonctionnelle sera conservée.

### Environnements de déploiement

> Voir : [la page des Urls](./Urls.md)

### Vérification post-déploiement

- Des tests automatiques sont lancés
- Un contrôle manuel via l’interface web est réalisé

### Bonnes pratiques

- Toujours vérifier que les tests passent avant de fusionner
- Documenter toute anomalie rencontrée dans un ticket GitHub
- Communiquer avec l’équipe en cas de problème
