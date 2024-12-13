## Expliquons le code Hello World

### Comment fonctionne Go

Le [Jour 8](day08.md), nous avons parcouru l'installation de Go sur votre poste de travail et créé notre première application Go.

Dans cette section, nous allons examiner plus en profondeur le code et comprendre quelques éléments supplémentaires sur le langage Go.

### Qu'est-ce que la compilation ?

Avant de nous plonger dans les [6 lignes du code Hello World](Go/hello.go), nous devons comprendre un peu ce qu'est la compilation.

Les langages de programmation que nous utilisons couramment, comme Python, Java, Go et C++, sont des langages de haut niveau. Cela signifie qu'ils sont lisibles par l'homme, mais lorsqu'une machine essaie d'exécuter un programme, il doit être sous une forme que la machine peut comprendre. Nous devons traduire notre code lisible par l'homme en code machine, ce qui s'appelle la compilation.

![](Images/Day9_Go1.png)

Comme vous pouvez le voir ci-dessus, le [Jour 8](day08.md), nous avons créé un simple Hello World main.go et utilisé la commande `go build main.go` pour compiler notre exécutable.

### Qu'est-ce qu'un package ?

Un package est une collection de fichiers source dans le même répertoire qui sont compilés ensemble. Nous pouvons simplifier cela davantage : un package est un ensemble de fichiers .go dans le même répertoire. Vous vous souvenez de notre dossier Hello du Jour 8 ? Si et quand vous vous lancez dans des programmes Go plus complexes, vous pourriez trouver que vous avez dossier1, dossier2 et dossier3 contenant différents fichiers .go qui composent votre programme avec plusieurs packages.

Nous utilisons des packages pour pouvoir réutiliser le code des autres. Nous n'avons pas besoin d'écrire tout à partir de zéro. Peut-être que nous voulons une calculatrice dans notre programme ; vous pourriez probablement trouver un package Go existant qui contient les fonctions mathématiques que vous pourriez importer dans votre code, vous faisant gagner beaucoup de temps et d'efforts à long terme.

Go vous encourage à organiser votre code en packages pour qu'il soit facile de réutiliser et de maintenir le code source.

### Hello #90DaysOfDevOps Ligne par Ligne

Maintenant, jetons un coup d'œil à notre fichier main.go Hello #90DaysOfDevOps et parcourons les lignes.

![](Images/Day9_Go2.png)

Dans la première ligne, vous avez `package main`, ce qui signifie que ce fichier appartient à un package appelé main. Tous les fichiers .go doivent appartenir à un package ; ils doivent également avoir `package something` dans la ligne d'ouverture.

Un package peut être nommé comme vous le souhaitez. Nous devons appeler cela `main` car c'est le point de départ du programme qui sera dans ce package, c'est une règle. (Je dois comprendre davantage cette règle ?)

![](Images/Day9_Go3.png)

Chaque fois que nous voulons compiler et exécuter notre code, nous devons indiquer à la machine où l'exécution doit commencer. Nous faisons cela en écrivant une fonction appelée main. La machine recherchera une fonction appelée main pour trouver le point d'entrée du programme.

Une fonction est un bloc de code qui peut effectuer une tâche spécifique et peut être utilisé dans tout le programme.

Vous pouvez déclarer une fonction avec n'importe quel nom en utilisant `func`, mais dans ce cas, nous devons la nommer `main` car c'est là que le code commence.

![](Images/Day9_Go4.png)

Ensuite, nous allons examiner la ligne 3 de notre code, l'importation. Cela signifie que vous voulez intégrer un autre package à votre programme principal. fmt est un package standard fourni par Go utilisé ici ; ce package contient la fonction `Println()` et parce que nous l'avons importé, nous pouvons l'utiliser à la ligne 6. Il existe plusieurs packages standard que vous pouvez inclure dans votre programme et utiliser ou réutiliser dans votre code, vous évitant ainsi la peine d'avoir à écrire à partir de zéro. [Bibliothèque standard Go](https://pkg.go.dev/std)

![](Images/Day9_Go5.png)

Le `Println()` que nous avons ici est un moyen d'écrire la sortie standard dans le terminal où l'exécutable a été exécuté avec succès. N'hésitez pas à changer le message entre les ().

![](Images/Day9_Go6.png)

### TLDR

- **Ligne 1** = Ce fichier sera dans le package appelé `main` et doit être appelé `main` car il inclut le point d'entrée du programme.
- **Ligne 3** = Pour utiliser `Println()`, nous devons importer le package fmt pour l'utiliser à la ligne 6.
- **Ligne 5** = Le véritable point de départ, c'est la fonction `main`.
- **Ligne 6** = Cela nous permettra d'imprimer "Hello #90DaysOfDevOps" sur notre système.

## Ressources

- [Enquête StackOverflow 2021 sur les développeurs](https://insights.stackoverflow.com/survey/2021)
- [Pourquoi nous choisissons Golang pour apprendre](https://www.youtube.com/watch?v=7pLqIIAqZD4&t=9s)
- [Jake Wright - Apprenez Go en 12 minutes](https://www.youtube.com/watch?v=C8LgvuEBraI&t=312s)
- [Techworld With Nana - Cours complet sur Golang - 3 heures 24 minutes](https://www.youtube.com/watch?v=yyUHQIec83I)
- [Techworld With Nana - Apprenez Go en construisant une application TodoList](https://www.youtube.com/watch?v=XCZWyN9ZbEQ)
- [**PAS GRATUIT** Nigel Poulton Pluralsight - Fondamentaux de Go - 3 heures 26 minutes](https://www.pluralsight.com/courses/go-fundamentals)
- [FreeCodeCamp - Apprenez la programmation Go - Tutoriel Golang pour débutants](https://www.youtube.com/watch?v=YS4e4q9oBaU&t=1025s)
- [Hitesh Choudhary - Liste de lecture complète](https://www.youtube.com/playlist?list=PLRAV69dS1uWSR89FRQGZ6q9BR2b44Tr9N)

À bientôt sur [Jour 10](day10.md).