Organisation Git de Flutter

1. Les branches
   Le dépôt Flutter utilise une organisation de branches bien structurée :

`main` : correspond à la version de production du projet, stable et publiée.

`flutter-X.XX-candidate.Y` : ce sont des branches candidates à une future version stable. Elles sont destinées à être fusionnées dans main après validation.

`cleanup-todo` : utilisée pour faire du ménage dans les commentaires TODO laissés dans le code.

`stable` : contient une version stable du framework, différente de main selon le cycle de publication.

`fix/numéro-d’issue` : branches spécifiques aux correctifs liés à une issue identifiée (ex. : fix/12345).

D'autres branches suivent des noms explicites qui précisent clairement leur but ou leur fonctionnalité.

2. Les tags

Les tags Git sont utilisés pour marquer des points importants de l’historique du projet, notamment :

    - Les versions stables (3.22.1, 2.10.0, etc.).

    - Les release candidates (3.22.0-0.1.pre, etc.).

Ces tags sont associés à des archives (.zip ou .tar.gz) qui permettent de télécharger directement une version du SDK Flutter sans passer par Git. Cela facilite l'installation manuelle ou l'utilisation en CI/CD.

3. Les projets (Projects)

   La section Projects du dépôt GitHub est utilisée pour suivre l’avancement des développements. Les tâches sont organisées en tableaux (kanban) et classées par thèmes ou fonctionnalités, facilitant la gestion des priorités et du suivi.

4. Les issues

   Les issues (ou tickets) sont gérées avec des labels permettant de les catégoriser par thème, priorité, ou composant concerné.
   Lors de la création d’une issue, un formulaire guidé est proposé pour aider les contributeurs à fournir les bonnes informations et à orienter correctement leur demande.

5. Les droits et la contribution

   Le fichier CODEOWNERS définit les personnes responsables de certaines parties du code. Elles ont le droit d’approuver ou de valider les modifications dans les fichiers qu’elles supervisent.

Le fichier CONTRIBUTING.md explique comment contribuer au projet, les bonnes pratiques à suivre, et donne des liens vers la documentation officielle de Flutter.

## Conclution :

En conclusion, dans flutter less etapes pour soriti une nouvelles version c'est : clean_todo, puis les tests, puis stable et enfin la version final avec le tag correspondant a ce qui sort ( selon majeur pour mineur) en realese. Lorsque le version est bien validé en passe en Tag normal.
