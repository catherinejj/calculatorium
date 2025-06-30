# Protocole de Sécurité de Calculatorium

Ce document décrit les étapes à suivre en cas d'incident de sécurité pour Calculatorium.

---

## 1. Que faire en cas d'incident de sécurité ?

Si une attaque est suspectée ou confirmée, agissez rapidement :

### 1.1. Alerter et Isoler

1.  **Alerter l'équipe :**
    * Contactez immédiatement [catherinejj](https://github.com/catherinejj).
2.  **Isoler le système :**
    * Mettez l'application ou le service affecté hors ligne ou en mode maintenance.
    * Si possible, rendez vous dans `netlify --> projet configuration --> disable project`

### 1.2. Diagnostiquer et Contenir

1.  **Recueillir des preuves :** Sauvegardez les logs et prenez des captures d'écran avant toute intervention.
2.  **Identifier la source :** Cherchez la cause de l'intrusion (via les logs, les fichiers modifiés).
3.  **Contenir l'attaque :** Bloquez les IPs malveillantes, retirez le contenu malicieux.

### 1.3. Éradiquer et Récupérer

1.  **Nettoyer :** Supprimez tout code malveillant ou porte dérobée.
2.  **Restaurer :** Déployez la dernière **sauvegarde saine** du code et des données.
3.  **Sécuriser :** Changez tous les mots de passe et clés compromis. Appliquez les mises à jour de sécurité critiques.

### 1.4. Remettre en service en toute sécurité

1.  **Vérifier :** Testez l'application pour s'assurer qu'elle est stable et sécurisée.
2.  **Surveiller :** Mettez en place une surveillance accrue après la remise en ligne. Avec un outil tel que `Sentry`.
3.  **Remettre en ligne :** Rétablissez l'accès aux utilisateurs.

---

## 2. Bonnes Pratiques de Sécurité (pour les contributeurs)

Pour maintenir la sécurité du projet :

* **Validation des entrées :** Toujours valider et nettoyer les données utilisateur pour prévenir les injections (SQL, XSS).
* **Secrets sécurisés :** Ne **jamais** commiter de mots de passe, clés API ou identifiants directement dans le code. Utilisez des **variables d'environnement**.
* **Fichiers `.env` :** Assurez-vous que `.env` est dans le `.gitignore` et fournissez un `.env.example`.
* **Permissions de fichiers :** Définissez des permissions strictes pour les fichiers sensibles.
* **Mises à jour :** Gardez les dépendances et frameworks à jour.
* **Revue de code :** Chaque modification majeure doit être revue par un pair, avec un œil sur la sécurité.
