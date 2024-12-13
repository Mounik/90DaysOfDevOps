### L'Espace de Travail Go

Le [Jour 8](day08.md), nous avons brièvement abordé l'espace de travail Go pour installer et démarrer Go afin de réaliser la démonstration de `Hello #90DaysOfDevOps`. Mais nous devons expliquer un peu plus l'espace de travail Go.

Rappelez-vous que nous avons choisi les paramètres par défaut et que nous avons ensuite créé notre dossier Go dans le GOPATH qui était déjà défini. En réalité, ce GOPATH peut être modifié pour être où vous le souhaitez.

Si vous exécutez

```
echo $GOPATH
```

La sortie devrait être similaire à la mienne (avec un nom d'utilisateur différent peut-être) qui est :

```
/home/michael/projects/go
```

Ensuite, nous avons créé 3 répertoires ici : **src**, **pkg** et **bin**.

![](Images/Day10_Go1.png)

**src** est l'endroit où tous vos programmes et projets Go sont stockés. Cela gère l'espace de noms et la gestion des packages pour tous vos dépôts Go. C'est ici que vous verrez, sur notre poste de travail, notre dossier Hello pour le projet Hello #90DaysOfDevOps.

![](Images/Day10_Go2.png)

**pkg** est l'endroit où vos fichiers d'archives de packages qui sont ou étaient installés dans des programmes sont stockés. Cela aide à accélérer le processus de compilation en fonction de si les packages utilisés ont été modifiés.

![](Images/Day10_Go3.png)

**bin** est l'endroit où tous vos binaires compilés sont stockés.

![](Images/Day10_Go4.png)

Notre Hello #90DaysOfDevOps n'est pas un programme complexe, donc voici un exemple d'un programme Go plus complexe tiré d'une autre excellente ressource qui vaut la peine d'être consultée : [GoChronicles](https://gochronicles.com/).

![](Images/Day10_Go5.png)

Cette page explique également en détail pourquoi et comment la disposition est ainsi. Elle va également un peu plus loin sur d'autres dossiers que nous n'avons pas mentionnés : [GoChronicles](https://gochronicles.com/project-structure/).

### Compilation et Exécution du Code

Le [Jour 9](day09.md), nous avons également abordé une brève introduction à la compilation du code, mais nous pouvons aller un peu plus loin ici.

Pour exécuter notre code, nous devons d'abord le **compiler**. Il existe trois façons de le faire dans Go.

- go build
- go install
- go run

Avant d'en arriver à l'étape de compilation ci-dessus, nous devons examiner ce que nous obtenons avec l'installation de Go.

Lorsque nous avons installé Go le Jour 8, nous avons installé quelque chose appelé Go tools, qui se compose de plusieurs programmes nous permettant de construire et de traiter nos fichiers source Go. L'un des outils est `Go`.

Il est utile de noter que vous pouvez installer des outils supplémentaires qui ne sont pas dans l'installation standard de Go.

Si vous ouvrez votre invite de commande et tapez `go`, vous devriez voir quelque chose comme l'image ci-dessous, puis vous verrez "Additional Help Topics" en dessous. Pour l'instant, nous n'avons pas à nous en préoccuper.

![](Images/Day10_Go6.png)

Vous vous souvenez peut-être aussi que nous avons déjà utilisé au moins deux de ces outils jusqu'à présent le Jour 8.

![](Images/Day10_Go7.png)

Ceux que nous voulons apprendre davantage sont build, install et run.

![](Images/Day10_Go8.png)

- `go run` - Cette commande compile et exécute le package principal composé des fichiers .go spécifiés sur la ligne de commande. La commande est compilée dans un dossier temporaire.
- `go build` - Pour compiler les packages et les dépendances, compilez le package dans le répertoire actuel. Si le projet Go contient un package `main`, il créera et placera l'exécutable dans le répertoire actuel, sinon il placera l'exécutable dans le dossier `pkg`, et celui-ci pourra être importé et utilisé par d'autres programmes Go. `go build` vous permet également de créer un fichier exécutable pour toute plateforme de système d'exploitation supportée par Go.
- `go install` - Identique à go build mais placera l'exécutable dans le dossier `bin`.

Nous avons parcouru go build et go run, mais n'hésitez pas à les parcourir à nouveau ici si vous le souhaitez. `go install`, comme indiqué ci-dessus, place l'exécutable dans notre dossier bin.

![](Images/Day10_Go9.png)

Espérons que si vous suivez, vous regardez l'une des listes de lecture ou vidéos ci-dessous. Je prends des éléments de chacune de ces ressources et les traduis dans mes notes pour comprendre les connaissances fondamentales du langage Golang. Les ressources ci-dessous vous donneront probablement une bien meilleure compréhension de nombreux domaines dont vous avez besoin globalement, mais j'essaie de documenter les 7 jours ou 7 heures de ce voyage avec des éléments intéressants que j'ai trouvés.

## Ressources

- [Enquête StackOverflow 2021 sur les développeurs](https://insights.stackoverflow.com/survey/2021)
- [Pourquoi nous choisissons Golang pour apprendre](https://www.youtube.com/watch?v=7pLqIIAqZD4&t)
- [Jake Wright - Apprenez Go en 12 minutes](https://www.youtube.com/watch?v=C8LgvuEBraI&t)
- [Techworld With Nana - Cours complet sur Golang - 3 heures 24 minutes](https://www.youtube.com/watch?v=yyUHQIec83I)
- [Techworld With Nana - Apprenez Go en construisant une application TodoList](https://www.youtube.com/watch?v=XCZWyN9ZbEQ)
- [**PAS GRATUIT** Nigel Poulton Pluralsight - Fondamentaux de Go - 3 heures 26 minutes](https://www.pluralsight.com/courses/go-fundamentals)
- [FreeCodeCamp - Apprenez la programmation Go - Tutoriel Golang pour débutants](https://www.youtube.com/watch?v=YS4e4q9oBaU&t)
- [Hitesh Choudhary - Liste de lecture complète](https://www.youtube.com/playlist?list=PLRAV69dS1uWSR89FRQGZ6q9BR2b44Tr9N)

À bientôt sur [Jour 11](day11.md).