## Vue d'Ensemble : Mise en Scène et Changement

Nous avons déjà couvert certains des fondamentaux, mais mettre les choses en pratique nous aide à mieux comprendre comment et pourquoi nous le faisons de cette manière. Avant de nous plonger dans les services basés sur Git comme GitHub, Git a ses propres capacités que nous pouvons exploiter sur notre station de travail locale.

Nous allons prendre le dossier de projet que nous avons créé au début de la session Git et nous allons parcourir certaines des étapes simples que nous pouvons faire avec Git. Nous avons créé un dossier sur notre machine locale et nous l'avons initialisé avec la commande `git init`.

![](Images/Day38_Git1.png)

Nous pouvons également voir maintenant que nous avons initialisé le dossier, nous avons un dossier caché dans notre répertoire.

![](Images/Day38_Git2.png)

C'est ici que les détails du dépôt Git sont stockés ainsi que les informations concernant nos branches et nos commits.

### Mise en Scène des Fichiers

Nous commençons ensuite à travailler sur notre dossier vide et peut-être ajoutons du code source les premiers jours de travail. Nous créons notre fichier readme.md et nous pouvons voir ce fichier dans le répertoire, ensuite nous vérifions notre `git status` et il connaît le nouveau fichier readme.md mais nous n'avons pas encore commis le fichier.

![](Images/Day38_Git3.png)

Nous pouvons mettre en scène notre fichier readme.md avec la commande `git add README.md`, puis nous pouvons voir les changements à commettre que nous n'avions pas auparavant et un nouveau fichier vert.

![](Images/Day38_Git4.png)

Ensuite, nous voulons commit ceci, notre premier commit ou notre premier instantané de notre projet. Nous pouvons le faire en utilisant la commande `git commit -m "Message significatif"` afin de pouvoir facilement voir ce qui a changé pour chaque commit. Aussi, remarquez que la croix jaune des changements devient maintenant une coche verte. C'est quelque chose que j'ai dans mon terminal avec le thème que j'utilise, quelque chose que nous avons couvert dans la section Linux.

![](Images/Day38_Git5.png)

### Committre des Changements

Nous allons très probablement vouloir ajouter plus de fichiers ou même changer les fichiers que nous avons dans notre répertoire. Nous avons déjà fait notre premier commit ci-dessus. Mais maintenant, nous allons ajouter plus de détails et plus de fichiers.

Nous pourrions répéter notre processus précédent, créer ou éditer notre fichier > `git add .` pour ajouter tous les fichiers à la zone de mise en scène, puis `git commit -m "message significatif"` et cela fonctionnerait très bien. Mais pour pouvoir offrir un message significatif sur le commit de ce qui a changé, vous ne voudrez peut-être pas écrire quelque chose comme `git commit -m "Eh bien, j'ai changé du code parce que cela ne fonctionnait pas et quand je l'ai corrigé, j'ai également ajouté quelque chose de nouveau au readme.md pour m'assurer que tout le monde connaissait l'expérience utilisateur, puis j'ai fait un thé."` Je veux dire que cela fonctionnerait bien, bien que probablement rendre cela descriptif mais la manière préférée ici est d'ajouter ceci avec un éditeur de texte.

Si nous exécutons `git commit` après avoir exécuté `git add`, cela ouvrira notre éditeur de texte par défaut, qui dans mon cas ici est nano. Voici les étapes que j'ai suivies pour ajouter quelques changements au fichier, exécuter `git status` pour montrer ce qui est et ce qui n'est pas mis en scène. Ensuite, j'ai utilisé `git add` pour ajouter le fichier à la zone de mise en scène, puis exécuté `git commit` qui a ouvert nano.

![](Images/Day38_Git6.png)

Lorsque nano s'ouvre, vous pouvez ensuite ajouter votre message court et long de description, puis enregistrer le fichier.

![](Images/Day38_Git7.png)

### Meilleures Pratiques de Commit

Il y a un équilibre ici entre quand commettre et commettre souvent. Nous ne voulons pas attendre la fin du projet avant de commettre, chaque commit devrait être significatif et ils ne devraient pas non plus être couplés à des tâches non pertinentes les unes avec les autres. Si vous avez une correction de bug et une faute de frappe, assurez-vous qu'il s'agit de deux commits séparés en tant que meilleure pratique.

Rendez le message de commit significatif.

En termes de rédaction, l'équipe ou vous-même devriez vous en tenir au même mot pour chaque commit.

### Sauter la Zone de Mise en Scène

Devons-nous toujours mettre en scène nos changements avant de les commettre ?

La réponse est oui, mais ne voyez pas cela comme un raccourci, vous devez être sûr à 100 % que vous n'avez pas besoin de cet instantané pour revenir en arrière, c'est une chose risquée à faire.

![](Images/Day38_Git8.png)

### Suppression de Fichiers

Et si nous supprimons des fichiers de notre projet, peut-être avons-nous un autre fichier dans notre répertoire que nous avons commis mais maintenant le projet n'en a plus besoin ou ne l'utilise plus, en tant que meilleure pratique, nous devrions le supprimer.

Juste parce que nous supprimons le fichier du répertoire, Git est toujours conscient de ce fichier et nous devons également le supprimer du dépôt. Vous pouvez voir le flux de travail pour cela ci-dessous.

![](Images/Day38_Git9.png)

Cela pourrait être un peu douloureux à gérer si vous avez un grand projet qui a beaucoup de fichiers et de dossiers en mouvement. Nous pouvons faire cela avec une seule commande avec `git rm oldcode.ps1`.

![](Images/Day38_Git10.png)

### Renommer ou Déplacer des Fichiers

Au sein de notre système d'exploitation, nous pouvons renommer et déplacer nos fichiers. Nous devrons sans aucun doute le faire de temps en temps avec nos projets. Similaire à la suppression de fichiers du système d'exploitation puis du dépôt Git, nous pouvons également effectuer ce renommage en utilisant une commande Git.

![](Images/Day38_Git11.png)

Cependant, comme pour la suppression de fichiers du système d'exploitation puis du dépôt Git, nous pouvons également effectuer ce renommage en utilisant une commande Git.

![](Images/Day38_Git12.png)

### Ignorer des Fichiers

Nous pourrions avoir besoin d'ignorer des fichiers ou des dossiers dans notre projet que nous pourrions utiliser localement ou qui seraient simplement un espace perdu si nous devions les partager avec l'ensemble du projet, un bon exemple de cela pourrait être les journaux. Je pense également utiliser ceci pour les secrets que vous ne souhaitez pas partager en public ou entre les équipes.

Nous pouvons ignorer des fichiers en ajoutant des dossiers ou des fichiers au fichier `.gitignore` dans notre répertoire de projet.

![](Images/Day38_Git13.png)

Vous pouvez ensuite ouvrir le fichier `.gitignore` et voir que nous avons le dossier logs/ présent. Mais nous pourrions également ajouter des fichiers et des dossiers supplémentaires ici à ignorer.

![](Images/Day38_Git14.png)

Nous pouvons ensuite voir `git status` puis voir ce qui s'est passé.

![](Images/Day38_Git15.png)

Il existe également des moyens de revenir en arrière et d'ignorer des fichiers et des dossiers, peut-être que vous vouliez partager le dossier logs mais que vous avez ensuite réalisé que vous ne le souhaitiez pas. Vous devrez utiliser `git rm --cached` pour supprimer les fichiers et les dossiers de la zone de mise en scène si vous avez un dossier précédemment suivi que vous souhaitez maintenant ignorer.

### Statut Court

Nous avons beaucoup utilisé `git status` pour comprendre ce que nous avons dans notre zone de mise en scène et ce que nous n'avons pas, c'est une commande très complète avec beaucoup de détails. La plupart du temps, vous voudrez simplement savoir ce qui a été modifié ou ce qui est nouveau ? Nous pouvons utiliser `git status -s` pour un statut court de ce détail. J'établirais généralement un alias sur mon système pour simplement utiliser `git status -s` par rapport à la commande plus détaillée.

![](Images/Day38_Git16.png)

Dans le post de demain, nous continuerons à examiner ces exemples courts de ces commandes Git courantes.

## Ressources

- [Qu'est-ce que le Contrôle de Version ?](https://www.youtube.com/watch?v=Yc8sCSeMhi4)
- [Types de Systèmes de Contrôle de Version](https://www.youtube.com/watch?v=kr62e_n6QuQ)
- [Tutoriel Git pour Débutants](https://www.youtube.com/watch?v=8JJ101D3knE&t=52s)
- [Tutoriel Git pour Professionnels](https://www.youtube.com/watch?v=Uszj_k0DGsg)
- [Git et GitHub pour Débutants - Cours Complet](https://www.youtube.com/watch?v=RGOj5yH7evk&t=8s)
- [Tutoriel Complet sur Git et GitHub](https://www.youtube.com/watch?v=apGV9Kg7ics)
- [Feuille de Triche Git](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

À demain pour le [Jour 39](day39.md)