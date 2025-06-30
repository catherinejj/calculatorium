**1. URLs des environnements**
   |Environnement| URL |Description|
   |-------------|----|-------------|
   | Local| http://localhost:5173| Environnement de développement sur ta machine locale|
   | Staging| https://staging--calculatorium-ynov.netlify.app/ |Environnement de pré-production (actuellement offline)|
   | Dev| https://dev--calculatorium-ynov.netlify.app/ |Environnement Dev|
   | Qa| https://qa--calculatorium-ynov.netlify.app/ |Environnement de QA|
   |Production| https://calculatorium-ynov.netlify.app/ |Environnement en ligne accessible aux utilisateurs finaux|

**2. Workflow Git utilisé**

   Pour organiser le développement et éviter les erreurs, on utilise plusieurs branches :

> dev : Branche de développement. C’est là que tu fais tes modifications et tests locaux.

> qa : Branche de Quality Assurance. Permet à l’équipe de test de vérifier que toutes les fonctionnalités développées fonctionnent correctement.

> staging : Branche de pré-production. Permet de tester les versions quasi-finales.

> main: Branche de production stable, déployée en ligne pour les utilisateurs.

A noter que par convention, la documentation de Netlify nous offre des ulrs dédiées pour les brachnes qui ne sont pas en prod. 

Exemple de commandes typiques

```bash

# Se positionner sur la branche dev et créer une nouvelle branche pour ta tâche

git checkout dev
git pull origin dev
git checkout -b feature/ma-tache

# Faire les modifications, puis valider les changements

git add .
git commit -m "Ajout de la fonctionnalité X"

# Envoyer ta branche sur le serveur distant

git push origin feature/ma-tache

# Sur GitHub, créer une Pull Request vers dev pour validation et fusion

# Une fois validé, fusionner dev dans staging pour tests en pré-prod

git checkout staging
git pull origin staging
git merge dev
git push origin staging

# Enfin, après validation en staging, fusionner staging dans main pour mise en production

git checkout main
git pull origin main
git merge staging
git push origin main
```

**3. Situations où ça fonctionne en local mais pas en ligne**

3.1 Description du problème
Parfois, ton application marche parfaitement sur ta machine (local), mais quand tu la déploies en ligne (staging ou prod), elle ne fonctionne pas ou s’affiche mal (ex : page blanche, erreurs).

3.2 Causes fréquentes
Mauvaise gestion des chemins relatifs
Par exemple, des liens vers des images ou scripts qui fonctionnent localement mais cassent en ligne à cause des chemins.

Ressources non chargées
Images, fichiers CSS ou JS absents ou mal référencés dans la version en ligne.

Variables d’environnement manquantes ou mal configurées
Certaines clés ou URLs nécessaires ne sont pas définies sur le serveur.

Problèmes liés au CORS (Cross-Origin Resource Sharing)
Le serveur bloque certaines requêtes venant du client.

Différences de configuration entre local et serveur
Configuration serveur, versions de Node, bases de données, etc.

3.3 Solutions à mettre en place
Vérifier et corriger les chemins des ressources
Utiliser des chemins absolus ou variables d’environnement pour gérer les URL.

Ajouter toutes les variables d’environnement nécessaires sur le serveur
Par exemple, via .env ou paramètres du service d’hébergement.

Configurer correctement le CORS côté serveur
Permettre les bonnes origines et méthodes HTTP.

Effectuer un build complet avant déploiement
S’assurer que les fichiers générés correspondent à la dernière version.

Tester en staging avant production
Détecter les erreurs en amont.

**4. Remarques et bonnes pratiques**
   Toujours tester en local avant de déployer.

Documenter chaque problème rencontré et comment tu l’as résolu (utile pour toi et l’équipe).

Utiliser les branches Git pour séparer développement, tests, et production.

Communiquer clairement dans les tickets de suivi (issue tracker) pour garder tout le monde informé.

Penser à synchroniser régulièrement ta branche avec dev pour éviter les conflits.

> Garder le workflow clair et propre pour éviter les erreurs.
