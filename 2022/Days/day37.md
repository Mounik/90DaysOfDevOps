## Vue d'Ensemble : Apprendre Git

Avant de nous plonger dans Git, nous devons comprendre ce qu'est le contrôle de version et pourquoi. Dans cette introduction à Git, nous allons examiner ce qu'est le contrôle de version et les bases de Git.

### Qu'est-ce que le Contrôle de Version ?

Git n'est pas le seul système de contrôle de version, donc ici, nous voulons couvrir les options disponibles et les méthodologies autour du contrôle de version.

L'un des avantages les plus évidents et un grand avantage du contrôle de version est la capacité à suivre l'historique d'un projet. Nous pouvons examiner ce dépôt en utilisant `git log` et voir que nous avons de nombreux commits et de nombreux commentaires et ce qui s'est passé jusqu'à présent dans le projet. Ne vous inquiétez pas, nous allons nous plonger dans les commandes plus tard. Maintenant, imaginez que ceci est un véritable projet logiciel rempli de code source et que plusieurs personnes commettent à notre logiciel à différents moments, différents auteurs, et ensuite les réviseurs sont tous enregistrés ici afin que nous sachions ce qui s'est passé, quand, par qui et qui a révisé.

![](Images/Day35_Git1.png)

Le contrôle de version avant qu'il soit cool aurait été quelque chose comme la création manuelle d'une copie de votre version avant de faire des modifications. Il se pourrait également que vous commentiez le vieux code inutile avec le "juste au cas où".

![](Images/Day35_Git2.png)

J'ai commencé à utiliser le contrôle de version non seulement sur le code source, mais pratiquement sur tout. Cela parle de projets comme celui-ci (90DaysOfDevOps). Pourquoi ne pas accepter les fonctionnalités qui permettent de revenir en arrière et de journaliser tout ce qui s'est passé ?

Cependant, un grand avertissement **Le contrôle de version n'est pas une sauvegarde !**

Un autre avantage du contrôle de version est la capacité à gérer plusieurs versions d'un projet. Prenons un exemple : nous avons une application gratuite disponible sur tous les systèmes d'exploitation et une application payante également disponible sur tous les systèmes d'exploitation. La majorité du code est partagée entre les deux applications. Nous pourrions copier et coller notre code à chaque commit pour chaque application, mais cela serait très désordonné, surtout lorsque vous mettez à l'échelle votre développement à plus d'une personne, et des erreurs seront commises.

L'application premium est l'endroit où nous allons avoir des fonctionnalités supplémentaires, appelons-les commits premium.

![](Images/Day35_Git3.png)

L'application gratuite est l'endroit où nous allons avoir des fonctionnalités supplémentaires, appelons-les commits premium.

![](Images/Day35_Git4.png)

Maintenant, cela semble facile, mais la fusion peut être compliquée parce que vous pourriez avoir une équipe travaillant sur l'édition gratuite et une autre équipe travaillant sur la version payante premium, et que se passe-t-il si les deux modifient le code qui affecte des aspects du code global ? Peut-être qu'une variable est mise à jour et casse quelque chose. Ensuite, vous avez un conflit qui casse l'une des fonctionnalités. Le contrôle de version ne peut pas résoudre les conflits qui dépendent de vous. Mais le contrôle de version permet de gérer cela facilement.

La raison principale, si vous n'avez pas encore compris le contrôle de version, en général, est la capacité à collaborer. La capacité à partager du code parmi les développeurs et, quand je dis code, comme je l'ai dit précédemment, de plus en plus nous voyons beaucoup plus de cas d'utilisation pour d'autres raisons d'utiliser le contrôle de source, peut-être est-ce une présentation conjointe sur laquelle vous travaillez avec un collègue ou un défi 90DaysOfDevOps où la communauté offre ses corrections et mises à jour tout au long du projet.

Sans contrôle de version, comment les équipes de développeurs de logiciels géraient-elles cela ? Je trouve cela assez difficile quand je travaille sur mes projets pour garder une trace des choses. Je m'attends à ce qu'ils divisent le code en chaque module fonctionnel. Peut-être une petite partie du puzzle, puis rassembler les pièces et ensuite résoudre les problèmes et les problèmes avant que quoi que ce soit ne soit publié.

Avec le contrôle de version, nous avons une seule source de vérité. Nous pourrions toujours tous travailler sur différents modules, mais cela nous permet de mieux collaborer.

![](Images/Day35_Git5.png)

Une autre chose à mentionner ici est que ce ne sont pas seulement les développeurs qui peuvent bénéficier du contrôle de version, ce sont tous les membres de l'équipe qui ont de la visibilité, mais aussi des outils ayant conscience ou tirant parti, les outils de gestion de projet peuvent être liés ici, suivant le travail. Nous pourrions également avoir une machine de construction, par exemple Jenkins, dont nous parlerons dans un autre module. Un outil qui construit et emballe le système, automatisant les tests de déploiement et les métriques.

### Qu'est-ce que Git ?

Git est un outil qui suit les modifications apportées au code source ou à n'importe quel fichier, ou nous pourrions également dire que Git est un système de contrôle de version distribué open-source.

Il existe de nombreuses façons d'utiliser Git sur nos systèmes, le plus couramment ou du moins pour moi, je l'ai vu sur la ligne de commande, mais nous avons également des interfaces utilisateur graphiques et des outils comme Visual Studio Code qui ont des opérations sensibles à Git dont nous pouvons tirer parti.

Maintenant, nous allons parcourir un aperçu de haut niveau avant même d'installer Git sur notre machine locale.

Prenons le dossier que nous avons créé précédemment.

![](Images/Day35_Git2.png)

Pour utiliser ce dossier avec le contrôle de version, nous devons d'abord initialiser ce répertoire en utilisant la commande `git init`. Pour l'instant, pensez simplement que cette commande place notre répertoire en tant que dépôt dans une base de données quelque part sur notre ordinateur.

![](Images/Day35_Git6.png)

Maintenant, nous pouvons créer quelques fichiers et dossiers et notre code source peut commencer ou peut-être qu'il existe déjà et que nous avons quelque chose ici. Nous pouvons utiliser la commande `git add .` qui place tous les fichiers et dossiers de notre répertoire dans un instantané, mais nous n'avons pas encore commis quoi que ce soit à cette base de données. Nous disons simplement que tous les fichiers avec le `.` sont prêts à être ajoutés.

![](Images/Day35_Git7.png)

Ensuite, nous voulons continuer et commettre nos fichiers, nous faisons cela avec la commande `git commit -m "Mon premier commit"`. Nous pouvons donner une raison pour notre commit et cela est suggéré afin que nous sachions ce qui s'est passé pour chaque commit.

![](Images/Day35_Git8.png)

Nous pouvons maintenant voir ce qui s'est passé dans l'historique du projet. En utilisant la commande `git log`.

![](Images/Day35_Git9.png)

Si nous créons un fichier supplémentaire appelé `samplecode.ps1`, l'état serait différent. Nous pouvons également vérifier l'état de notre dépôt en utilisant `git status`, cela montre que nous n'avons rien à commettre et que nous pouvons ajouter un nouveau fichier appelé samplecode.ps1. Si nous exécutons ensuite la même commande `git status`, vous verrez que nous avons le fichier à commettre.

![](Images/Day35_Git10.png)

Ajoutons notre nouveau fichier en utilisant la commande `git add samplecode.ps1`, puis nous pouvons réexécuter `git status` et voir que notre fichier est prêt à être commis.

![](Images/Day35_Git11.png)

Ensuite, émettez la commande `git commit -m "Mon deuxième commit"`.

![](Images/Day35_Git12.png)

Un autre `git status` montre maintenant que tout est à nouveau propre.

![](Images/Day35_Git13.png)

Nous pouvons ensuite utiliser la commande `git log` qui montre les derniers changements et le premier commit.

![](Images/Day35_Git14.png)

Si nous voulions voir les changements entre nos commits, c'est-à-dire quels fichiers ont été ajoutés ou modifiés, nous pouvons utiliser la commande `git diff b8f8 709a`.

![](Images/Day35_Git15.png)

Ce qui affiche ensuite ce qui a changé dans notre cas, nous avons ajouté un nouveau fichier.

![](Images/Day35_Git16.png)

Nous allons approfondir cela plus tard, mais nous pouvons sauter dans le temps ! En utilisant notre numéro de commit, nous pouvons utiliser la commande `git checkout 709a` pour revenir en arrière dans le temps sans perdre notre nouveau fichier.

![](Images/Day35_Git17.png)

Mais ensuite, de manière égale, nous voudrons avancer également et nous pouvons le faire de la même manière avec le numéro de commit ou vous pouvez voir ici que nous utilisons la commande `git switch -` pour annuler notre opération.

![](Images/Day35_Git18.png)

Le TLDR;

- Suivi de l'historique d'un projet
- Gestion de plusieurs versions d'un projet
- Partage de code parmi les développeurs et une portée plus large d'équipes et d'outils
- Coordination du travail d'équipe
- Oh et il y a un peu de voyage dans le temps !

J'espère qu'avec les commandes utilisées, les capacités et la vue d'ensemble derrière le contrôle de version, vous pouvez voir sans vraiment connaître les commandes utilisées.

Ensuite, nous allons installer Git sur votre machine locale et approfondir certains autres cas d'utilisation et commandes que nous pouvons réaliser dans Git.

## Ressources

- [Qu'est-ce que le contrôle de version ?](https://www.youtube.com/watch?v=Yc8sCSeMhi4)
- [Types de systèmes de contrôle de version](https://www.youtube.com/watch?v=kr62e_n6QuQ)
- [Tutoriel Git pour débutants](https://www.youtube.com/watch?v=8JJ101D3knE&t=52s)
- [Tutoriel Git pour professionnels](https://www.youtube.com/watch?v=Uszj_k0DGsg)
- [Git et GitHub pour débutants - Cours complet](https://www.youtube.com/watch?v=RGOj5yH7evk&t=8s)
- [Tutoriel complet sur Git et GitHub](https://www.youtube.com/watch?v=apGV9Kg7ics)
- [Feuille de triche Git](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

À demain pour le [Jour 38](day38.md)