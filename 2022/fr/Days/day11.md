Avant de nous plonger dans les sujets d'aujourd'hui, je tiens à remercier chaleureusement [Techworld with Nana](https://www.youtube.com/watch?v=yyUHQIec83I) pour ce voyage concis et fantastique à travers les fondamentaux de Go.

Le [Jour 8](day08.md), nous avons configuré notre environnement, le [Jour 9](day09.md), nous avons parcouru le code Hello #90DaysOfDevOps, et le [Jour 10](day10.md), nous avons examiné notre espace de travail Go et sommes allés un peu plus loin dans la compilation et l'exécution du code.

Aujourd'hui, nous allons examiner les variables, les constantes et les types de données tout en écrivant un nouveau programme.

## Variables et Constantes en Go

Commençons par planifier notre application. Je pense qu'il serait judicieux de travailler sur un programme qui nous indique combien de jours nous avons passés dans notre défi #90DaysOfDevOps.

La première chose à considérer ici est que, puisque nous construisons notre application et que nous accueillons nos participants et que nous donnons un retour à l'utilisateur sur le nombre de jours qu'ils ont complétés, nous pourrions utiliser le terme #90DaysOfDevOps plusieurs fois dans le programme. C'est un excellent cas d'utilisation pour faire de #90DaysOfDevOps une variable dans notre programme.

- Les variables sont utilisées pour stocker des valeurs.
- Comme une petite boîte avec nos informations ou valeurs sauvegardées.
- Nous pouvons ensuite utiliser cette variable dans tout le programme, ce qui présente également l'avantage que si ce défi ou cette variable change, nous n'avons à changer cela qu'à un seul endroit. Cela signifie que nous pourrions traduire cela à d'autres défis que nous avons dans la communauté en changeant simplement cette valeur de variable.

Pour déclarer cela dans notre programme Go, nous définissons une valeur en utilisant un **mot-clé** pour les variables. Cela vivra dans notre bloc de code `func main` que vous verrez plus tard. Vous pouvez en savoir plus sur les [Mots-clés](https://go.dev/ref/spec#Keywords) ici.

N'oubliez pas de vous assurer que vos noms de variables sont descriptifs. Si vous déclarez une variable, vous devez l'utiliser, sinon vous obtiendrez une erreur. Cela permet d'éviter un code potentiellement mort, un code qui n'est jamais utilisé. Il en va de même pour les packages non utilisés.

```go
var challenge = "#90DaysOfDevOps"
```

Avec ce qui précède défini et utilisé comme nous le verrons dans le prochain extrait de code, vous pouvez voir à partir de la sortie ci-dessous que nous avons utilisé une variable.

```go
package main

import "fmt"

func main() {
    var challenge = "#90DaysOfDevOps"
    fmt.Println("Bienvenue à", challenge, "")
}
```

Vous pouvez trouver l'extrait de code ci-dessus dans [day11_example1.go](Go/day11_example1.go).

Vous verrez ensuite à partir de ce qui suit que nous avons construit notre code avec l'exemple ci-dessus et que nous avons obtenu la sortie montrée ci-dessous.

![](Images/Day11_Go1.png)

Nous savons également que notre défi dure 90 jours, au moins pour ce défi, mais ensuite, peut-être que ce sera 100, donc nous voulons définir une variable pour nous aider ici aussi. Cependant, pour notre programme, nous voulons définir cela comme une constante. Les constantes sont comme des variables, sauf que leur valeur ne peut pas être modifiée dans le code (nous pouvons toujours créer une nouvelle application plus tard avec ce code et changer cette constante, mais ce 90 ne changera pas pendant que nous exécutons notre application).

Ajoutons le `const` à notre code et ajoutons une autre ligne de code pour imprimer ceci.

```go
package main

import "fmt"

func main() {
    var challenge = "#90DaysOfDevOps"
    const daystotal = 90

    fmt.Println("Bienvenue à", challenge, "")
    fmt.Println("Ceci est un défi de", daystotal, "jours")
}
```

Vous pouvez trouver l'extrait de code ci-dessus dans [day11_example2.go](Go/day11_example2.go).

Si nous passons ensuite par ce processus `go build` et que nous exécutons, vous verrez ci-dessous le résultat.

![](Images/Day11_Go2.png)

Enfin, et ce ne sera pas la fin de notre programme, nous reviendrons sur cela le [Jour 12](day12.md) pour ajouter plus de fonctionnalités. Nous voulons maintenant ajouter une autre variable pour le nombre de jours que nous avons complétés dans le défi.

Ci-dessous, j'ai ajouté la variable `dayscomplete` avec le nombre de jours complétés.

```go
package main

import "fmt"

func main() {
    var challenge = "#90DaysOfDevOps"
    const daystotal = 90
    var dayscomplete = 11

    fmt.Println("Bienvenue à", challenge, "")
    fmt.Println("Ceci est un défi de", daystotal, "jours et vous avez complété", dayscomplete, "jours")
    fmt.Println("Bon travail")
}
```

Vous pouvez trouver l'extrait de code ci-dessus dans [day11_example3.go](Go/day11_example3.go).

Passons par ce processus `go build` à nouveau ou vous pourriez simplement utiliser `go run`.

![](Images/Day11_Go3.png)

Voici quelques autres exemples que j'ai utilisés pour rendre le code plus facile à lire et à éditer. Jusqu'à présent, nous avons utilisé `Println`, mais nous pouvons simplifier cela en utilisant `Printf` en utilisant `%v`, ce qui signifie que nous définissons nos variables dans l'ordre à la fin de la ligne de code. Nous utilisons également `\n` pour un saut de ligne.

J'utilise `%v` car cela utilise une valeur par défaut, mais il existe d'autres options que vous pouvez trouver ici dans la [documentation du package fmt](https://pkg.go.dev/fmt). Vous pouvez trouver l'exemple de code [day11_example4.go](Go/day11_example4.go).

Les variables peuvent également être définies dans un format plus simple dans votre code. Au lieu de définir qu'il s'agit d'un `var` et du `type`, vous pouvez coder ceci comme suit pour obtenir la même fonctionnalité mais avec un aspect plus propre et plus simple pour votre code. Cela ne fonctionnera que pour les variables et non pour les constantes.

```go
func main() {
    challenge := "#90DaysOfDevOps"
    const daystotal = 90
```

## Types de Données

Dans les exemples ci-dessus, nous n'avons pas défini le type de variables, car nous pouvons leur donner une valeur ici et Go est assez intelligent pour savoir quel est ce type ou au moins peut l'inférer en fonction de la valeur que vous avez stockée. Cependant, si nous voulons qu'un utilisateur entre cela, cela nécessitera un type spécique.

Nous avons utilisé des chaînes de caractères et des entiers dans notre code jusqu'à présent. Des entiers pour le nombre de jours et des chaînes de caractères pour le nom du défi.

Il est également important de noter que chaque type de données peut faire des choses différentes et se comporte différemment. Par exemple, les entiers peuvent se multiplier où les chaînes de caractères ne le peuvent pas.

Il existe quatre catégories :

- **Type de base** : Les nombres, les chaînes de caractères et les booléens entrent dans cette catégorie.
- **Type agrégé** : Les tableaux et les structures entrent dans cette catégorie.
- **Type de référence** : Les pointeurs, les tranches, les cartes, les fonctions et les canaux entrent dans cette catégorie.
- **Type d'interface**

Le type de données est un concept important en programmation. Le type de données spécifie la taille et le type des valeurs de variable.

Go est typé statiquement, ce qui signifie qu'une fois qu'un type de variable est défini, il ne peut stocker que des données de ce type.

Go a trois types de données de base :

- **bool** : représente une valeur booléenne et est soit vraie soit fausse
- **Numérique** : représente les types d'entiers, les valeurs à virgule flottante et les types complexes
- **string** : représente une valeur de chaîne de caractères

J'ai trouvé cette ressource super détaillée sur les types de données [Golang by example](https://golangbyexample.com/all-data-types-in-golang-with-examples/).

Je suggérerais également [Techworld with Nana](https://www.youtube.com/watch?v=yyUHQIec83I&t=2023s) à ce stade couvre en détail de nombreux aspects des types de données en Go.

Si nous devons définir un type dans notre variable, nous pouvons le faire comme suit :

```go
var TwitterHandle string
var DaysCompleted uint
```

Parce que Go implique des variables où une valeur est donnée, nous pouvons imprimer ces valeurs avec ce qui suit :

```go
fmt.Printf("challenge est %T, daystotal est %T, dayscomplete est %T\n", conference, daystotal, dayscomplete)
```

Il existe de nombreux types différents d'entiers et de types de flottants ; les liens ci-dessus couvriront cela en détail.

- **int** = nombres entiers
- **unint** = nombres entiers positifs
- **types à virgule flottante** = nombres qui contiennent une composante décimale

## Ressources

- [Enquête StackOverflow 2021 sur les développeurs](https://insights.stackoverflow.com/survey/2021)
- [Pourquoi nous choisissons Golang pour apprendre](https://www.youtube.com/watch?v=7pLqIIAqZD4&t)
- [Jake Wright - Apprenez Go en 12 minutes](https://www.youtube.com/watch?v=C8LgvuEBraI&t)
- [Techworld With Nana - Cours complet sur Golang - 3 heures 24 minutes](https://www.youtube.com/watch?v=yyUHQIec83I)
- [Techworld With Nana - Apprenez Go en construisant une application TodoList](https://www.youtube.com/watch?v=XCZWyN9ZbEQ)
- [**PAS GRATUIT** Nigel Poulton Pluralsight - Fondamentaux de Go - 3 heures 26 minutes](https://www.pluralsight.com/courses/go-fundamentals)
- [FreeCodeCamp - Apprenez la programmation Go - Tutoriel Golang pour débutants](https://www.youtube.com/watch?v=YS4e4q9oBaU&t)
- [Hitesh Choudhary - Liste de lecture complète](https://www.youtube.com/playlist?list=PLRAV69dS1uWSR89FRQGZ6q9BR2b44Tr9N)

Ensuite, nous allons commencer à ajouter une fonctionnalité d'entrée utilisateur à notre programme afin que l'on nous demande combien de jours ont été complétés.

À bientôt sur [Jour 12](day12.md).