## 📦 Installation et création de ta branche personnelle

### 1. Cloner le projet

Ouvre un terminal (ou invite de commandes) et tape la commande suivante pour copier le projet sur ton ordinateur :

```bash
git clone https://github.com/catherinejj/calculatorium.git
```

2. Accéder au dossier du projet
   Ensuite, entre dans le dossier du projet avec cette commande :

```bash
cd calculatorium
```

3. Installer les dépendances
   Pour que le projet fonctionne, il faut installer les bibliothèques utilisées. Tape cette commande :

```bash
npm install
```

4. Lancer le projet en mode développement
   Pour démarrer le serveur et voir le projet fonctionner, lance cette commande :

```bash
npm run dev
```

5. Ouvrir le projet dans ton navigateur
   Enfin, ouvre ton navigateur (Chrome, Firefox, etc.) et va à l’adresse suivante :

`http://localhost:5173`

Tu verras alors l’application tourner sur ton ordinateur.

## Travailler sur ta propre branche

Comme tu n’as pas les droits pour modifier directement les branches principales (dev, qa, main), voici comment faire pour travailler en toute sécurité :

1. Créer ta branche personnelle
   Avant de commencer à coder, crée une nouvelle branche à partir de dev :

```bash
git checkout dev
git pull origin dev
git checkout -b mon-nom-branche
```

> Remplace mon-nom-branche par un nom clair, par exemple dev-nomprenom ou feature/ma-fonctionnalite.

2. Faire tes modifications et valider
   Travaille dans ta branche, puis ajoute et valide tes changements :

```bash
git add .
git commit -m "Feat:Description claire de ce que tu as fait"
```

3. Envoyer ta branche sur GitHub
   Pousse ta branche pour la rendre accessible à l’équipe :

```bash
git push origin mon-nom-branche
```

4. Créer une Pull Request.
   
   Sur GitHub, crée une Pull Request de ta branche vers dev pour que l’équipe puisse relire et valider ton travail.

> Astuce : Mettre à jour ta branche régulièrement
> Pour éviter les conflits, synchronise ta branche avec dev souvent :

```bash
git checkout dev
git pull origin dev
git checkout mon-nom-branche
git merge dev
```
