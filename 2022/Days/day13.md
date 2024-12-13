## Tweetez votre progression avec notre nouvelle application

Le dernier jour de notre exploration de ce langage de programmation, nous n'avons fait qu'effleurer la surface, mais c'est à ce stade que je pense que nous devons nous intéresser, nous enthousiasmer et vouloir nous plonger davantage.

Au cours des derniers jours, nous avons pris une petite idée pour une application et nous y avons ajouté des fonctionnalités. Dans cette session, je veux tirer parti de ces packages que nous avons mentionnés et créer la fonctionnalité pour notre application afin qu'elle ne donne pas seulement la mise à jour de votre progression à l'écran, mais qu'elle envoie également un tweet avec les détails du défi et votre statut.

## Ajouter la capacité de tweeter votre progression

La première chose que nous devons faire est de configurer notre accès API développeur avec Twitter pour que cela fonctionne.

Rendez-vous sur la [Plateforme Développeur Twitter](https://developer.twitter.com) et connectez-vous avec votre identifiant et vos informations Twitter. Une fois connecté, vous devriez voir quelque chose comme ci-dessous, sans l'application que j'ai déjà créée.

![](Images/Day13_Go1.png)

À partir d'ici, vous pourriez également demander un accès élevé, cela peut prendre un certain temps, mais cela a été très rapide pour moi.

Ensuite, nous devons sélectionner Projets et Applications et créer notre Application. Les limites dépendent de l'accès au compte que vous avez, avec l'essentiel vous n'avez qu'une application et un projet et avec l'élevé vous pouvez avoir 3 applications.

![](Images/Day13_Go2.png)

Donnez un nom à votre application

![](Images/Day13_Go3.png)

Vous recevrez ensuite ces jetons API, vous devez les sauvegarder quelque part en sécurité. (J'ai depuis supprimé cette application) Nous en aurons besoin plus tard avec notre application Go.

![](Images/Day13_Go4.png)

Maintenant que nous avons créé notre application, (j'ai dû changer le nom de mon application car celui de la capture d'écran ci-dessus était déjà pris, ces noms doivent être uniques)

![](Images/Day13_Go5.png)

Les clés que nous avons rassemblées précédemment sont connues sous le nom de nos clés de consommateur et nous aurons également besoin de notre jeton d'accès et de nos secrets. Nous pouvons rassembler ces informations en utilisant l'onglet "Clés et Jetons".

![](Images/Day13_Go6.png)

D'accord, nous avons terminé dans le portail développeur Twitter pour l'instant. Assurez-vous de garder vos clés en sécurité car nous en aurons besoin plus tard.

## Bot Twitter Go

Rappelez-vous le code que nous commençons dans notre application ainsi que [day13_example1](Go/day13_example1.go), mais d'abord, nous devons vérifier que nous avons le bon code pour faire tweeter quelque chose.

Nous devons maintenant réfléchir au code pour obtenir notre sortie ou message sur Twitter sous la forme d'un tweet. Nous allons utiliser [go-twitter](https://github.com/dghubble/go-twitter). Il s'agit d'une bibliothèque client Go pour l'API Twitter.

Pour tester cela avant de l'intégrer dans notre application principale, j'ai créé un nouveau répertoire dans notre dossier `src` appelé go-twitter-bot, émis la commande `go mod init github.com/michaelcade/go-Twitter-bot` sur le dossier qui a ensuite créé un fichier `go.mod`, puis nous pouvons commencer à écrire notre nouveau main.go et tester cela.

Nous avons maintenant besoin de ces clés, jetons et secrets que nous avons rassemblés à partir du portail développeur Twitter. Nous allons les définir dans nos variables d'environnement. Cela dépendra du système d'exploitation que vous utilisez :

J'ai eu quelques questions concernant les variables d'environnement, voici un article de blog qui entre plus en détail pour que vous puissiez comprendre ce qui se passe. [Comment Définir les Variables d'Environnement](https://www.twilio.com/blog/2017/01/how-to-set-environment-variables.html)

Windows

```
set CONSUMER_KEY
set CONSUMER_SECRET
set ACCESS_TOKEN
set ACCESS_TOKEN_SECRET
```

Linux / macOS

```
export CONSUMER_KEY
export CONSUMER_SECRET
export ACCESS_TOKEN
export ACCESS_TOKEN_SECRET
```

À ce stade, vous pouvez consulter [day13_example2](Go/day13_example2.go) pour le code, mais vous verrez ici que nous utilisons une structure pour définir nos clés, secrets et jetons.

Nous avons ensuite une fonction `func` pour analyser ces identifiants et établir cette connexion à l'API Twitter.

Ensuite, en fonction du succès, nous enverrons un tweet.

```go
package main

import (
    // autres imports
    "fmt"
    "log"
    "os"

    "github.com/dghubble/go-twitter/twitter"
    "github.com/dghubble/oauth1"
)

// Credentials stocke tous nos jetons/clés de consommateur et d'accès
// et les clés secrètes nécessaires pour l'authentification contre
// l'API REST de Twitter.
type Credentials struct {
    ConsumerKey       string
    ConsumerSecret    string
    AccessToken       string
    AccessTokenSecret string
}

// getClient est une fonction d'aide qui retournera un client Twitter
// que nous pouvons ensuite utiliser pour envoyer des tweets ou pour diffuser de nouveaux tweets
// cela prendra un pointeur vers une structure Credential qui contiendra
// tout ce qui est nécessaire pour s'authentifier et retourner un pointeur vers un client Twitter
// ou une erreur
func getClient(creds *Credentials) (*twitter.Client, error) {
    // Passez votre clé de consommateur (clé API) et votre secret de consommateur (secret API)
    config := oauth1.NewConfig(creds.ConsumerKey, creds.ConsumerSecret)
    // Passez votre jeton d'accès et votre secret de jeton d'accès
    token := oauth1.NewToken(creds.AccessToken, creds.AccessTokenSecret)

    httpClient := config.Client(oauth1.NoContext, token)
    client := twitter.NewClient(httpClient)

    // Vérifier les identifiants
    verifyParams := &twitter.AccountVerifyParams{
        SkipStatus:   twitter.Bool(true),
        IncludeEmail: twitter.Bool(true),
    }

    // nous pouvons récupérer l'utilisateur et vérifier si les identifiants
    // que nous avons utilisés nous permettent de nous connecter avec succès !
    user, _, err := client.Accounts.VerifyCredentials(verifyParams)
    if err != nil {
        return nil, err
    }

    log.Printf("Compte de l'utilisateur :\n%+v\n", user)
    return client, nil
}
func main() {
    fmt.Println("Go-Twitter Bot v0.01")
    creds := Credentials{
        AccessToken:       os.Getenv("ACCESS_TOKEN"),
        AccessTokenSecret: os.Getenv("ACCESS_TOKEN_SECRET"),
        ConsumerKey:       os.Getenv("CONSUMER_KEY"),
        ConsumerSecret:    os.Getenv("CONSUMER_SECRET"),
    }

    client, err := getClient(&creds)
    if err != nil {
        log.Println("Erreur lors de l'obtention du client Twitter")
        log.Println(err)
    }

    tweet, resp, err := client.Statuses.Update("Un tweet de test depuis le futur, testant un programme #90DaysOfDevOps qui tweete, tweet tweet", nil)
    if err != nil {
        log.Println(err)
    }
    log.Printf("%+v\n", resp)
    log.Printf("%+v\n", tweet)
}
```

Ce qui précède vous donnera soit une erreur en fonction de ce qui se passe, soit cela réussira et vous aurez un tweet envoyé avec le message décrit dans le code.

## Associer les deux - Go-Twitter-Bot + Notre Application

Maintenant, nous devons fusionner ces deux éléments dans notre `main.go`. Je suis sûr que quelqu'un là-bas crie qu'il y a une meilleure façon de faire cela et veuillez commenter ceci car vous pouvez avoir plus d'un fichier `.go` dans un projet, cela pourrait avoir du sens, mais cela fonctionne.

Vous pouvez voir la base de code fusionnée [day13_example3](Go/day13_example3.go), mais je vais également la montrer ci-dessous.

```go
package main

import (
    // autres imports
    "fmt"
    "log"
    "os"

    "github.com/dghubble/go-twitter/twitter"
    "github.com/dghubble/oauth1"
)

// Credentials stocke tous nos jetons/clés de consommateur et d'accès
// et les clés secrètes nécessaires pour l'authentification contre
// l'API REST de Twitter.
type Credentials struct {
    ConsumerKey       string
    ConsumerSecret    string
    AccessToken       string
    AccessTokenSecret string
}

// getClient est une fonction d'aide qui retournera un client Twitter
// que nous pouvons ensuite utiliser pour envoyer des tweets ou pour diffuser de nouveaux tweets
// cela prendra un pointeur vers une structure Credential qui contiendra
// tout ce qui est nécessaire pour s'authentifier et retourner un pointeur vers un client Twitter
// ou une erreur
func getClient(creds *Credentials) (*twitter.Client, error) {
    // Passez votre clé de consommateur (clé API) et votre secret de consommateur (secret API)
    config := oauth1.NewConfig(creds.ConsumerKey, creds.ConsumerSecret)
    // Passez votre jeton d'accès et votre secret de jeton d'accès
    token := oauth1.NewToken(creds.AccessToken, creds.AccessTokenSecret)

    httpClient := config.Client(oauth1.NoContext, token)
    client := twitter.NewClient(httpClient)

    // Vérifier les identifiants
    verifyParams := &twitter.AccountVerifyParams{
        SkipStatus:   twitter.Bool(true),
        IncludeEmail: twitter.Bool(true),
    }

    // nous pouvons récupérer l'utilisateur et vérifier si les identifiants
    // que nous avons utilisés nous permettent de nous connecter avec succès !
    user, _, err := client.Accounts.VerifyCredentials(verifyParams)
    if err != nil {
        return nil, err
    }

    log.Printf("Compte de l'utilisateur :\n%+v\n", user)
    return client, nil
}
func main() {
    creds := Credentials{
        AccessToken:       os.Getenv("ACCESS_TOKEN"),
        AccessTokenSecret: os.Getenv("ACCESS_TOKEN_SECRET"),
        ConsumerKey:       os.Getenv("CONSUMER_KEY"),
        ConsumerSecret:    os.Getenv("CONSUMER_SECRET"),
    }
    {
        const DaysTotal int = 90
        var remainingDays uint = 90
        challenge := "#90DaysOfDevOps"

        fmt.Printf("Bienvenue dans le défi %v.\nCe défi est composé de %v jours\n", challenge, DaysTotal)

        var TwitterName string
        var DaysCompleted uint

        // demander l'entrée de l'utilisateur
        fmt.Println("Entrez votre identifiant Twitter : ")
        fmt.Scanln(&TwitterName)

        fmt.Println("Combien de jours avez-vous complétés ? : ")
        fmt.Scanln(&DaysCompleted)

        // calculer les jours restants
        remainingDays = remainingDays - DaysCompleted

        //fmt.Printf("Merci %v de participer et d'avoir complété %v jours.\n", TwitterName, DaysCompleted)
        //fmt.Printf("Il vous reste %v jours pour le défi %v\n", remainingDays, challenge)
        // fmt.Println("Bonne chance")

        client, err := getClient(&creds)
        if err != nil {
            log.Println("Erreur lors de l'obtention du client Twitter, ceci est attendu si vous n'avez pas fourni vos jetons API Twitter")
            log.Println(err)
        }

        message := fmt.Sprintf("Salut, je suis %v, j'ai fait le %v pendant %v jours et il me reste %v jours", TwitterName, challenge, DaysCompleted, remainingDays)
        tweet, resp, err := client.Statuses.Update(message, nil)
        if err != nil {
            log.Println(err)
        }
        log.Printf("%+v\n", resp)
        log.Printf("%+v\n", tweet)
    }

}
```

Le résultat de ceci devrait être un tweet, mais si vous n'avez pas fourni vos variables d'environnement, vous devriez obtenir une erreur comme celle ci-dessous.

![](Images/Day13_Go7.png)

Une fois que vous avez corrigé cela ou si vous choisissez de ne pas vous authentifier avec Twitter, vous pouvez utiliser le code avec lequel nous avons terminé hier. La sortie du terminal en cas de succès ressemblera à ceci :

![](Images/Day13_Go8.png)

Le tweet résultant devrait ressembler à ceci :

![](Images/Day13_Go9.png)

## Comment compiler pour plusieurs systèmes d'exploitation

Ensuite, je veux aborder la question : "Comment compiler pour plusieurs systèmes d'exploitation ?" L'avantage de Go est qu'il peut facilement compiler pour de nombreux systèmes d'exploitation différents. Vous pouvez obtenir une liste complète en exécutant la commande suivante :

```
go tool dist list
```

L'utilisation de nos commandes `go build` jusqu'à présent est géniale et elle utilisera les variables d'environnement `GOOS` et `GOARCH` pour déterminer la machine hôte et ce pour quoi la compilation doit être construite. Mais nous pouvons également créer d'autres binaires en utilisant le code ci-dessous comme exemple.

```
GOARCH=amd64 GOOS=darwin go build -o ${BINARY_NAME}_0.1_darwin main.go
GOARCH=amd64 GOOS=linux go build -o ${BINARY_NAME}_0.1_linux main.go
GOARCH=amd64 GOOS=windows go build -o ${BINARY_NAME}_0.1_windows main.go
GOARCH=arm64 GOOS=linux go build -o ${BINARY_NAME}_0.1_linux_arm64 main.go
GOARCH=arm64 GOOS=darwin go build -o ${BINARY_NAME}_0.1_darwin_arm64 main.go
```

Cela vous donnera ensuite des binaires dans votre répertoire pour toutes les plateformes ci-dessus. Vous pouvez ensuite prendre cela et créer un makefile pour construire ces binaires chaque fois que vous ajoutez de nouvelles fonctionnalités et fonctionnalités à votre code. J'ai inclus le [makefile](Go/makefile).

C'est ce que j'ai utilisé pour créer les versions que vous pouvez maintenant voir sur le [dépôt](https://github.com/MichaelCade/90DaysOfDevOps/releases).

## Ressources

- [Enquête StackOverflow 2021 sur les développeurs](https://insights.stackoverflow.com/survey/2021)
- [Pourquoi nous choisissons Golang pour apprendre](https://www.youtube.com/watch?v=7pLqIIAqZD4&t=9s)
- [Jake Wright - Apprenez Go en 12 minutes](https://www.youtube.com/watch?v=C8LgvuEBraI&t=312s)
- [Techworld avec Nana - Cours complet sur Golang - 3 heures 24 minutes](https://www.youtube.com/watch?v=yyUHQIec83I)
- [**PAS GRATUIT** Nigel Poulton Pluralsight - Fondamentaux de Go - 3 heures 26 minutes](https://www.pluralsight.com/courses/go-fundamentals)
- [FreeCodeCamp - Apprenez la programmation Go - Tutoriel Golang pour débutants](https://www.youtube.com/watch?v=YS4e4q9oBaU&t=1025s)
- [Hitesh Choudhary - Liste de lecture complète](https://www.youtube.com/playlist?list=PLRAV69dS1uWSR89FRQGZ6q9BR2b44Tr9N)
- [Un dépôt génial plein de choses DevOps et d'exercices](https://github.com/bregman-arie/devops-exercises)
- [GoByExample - Apprentissage basé sur des exemples](https://gobyexample.com/)
- [go.dev/tour/list](https://go.dev/tour/list)
- [go.dev/learn](https://go.dev/learn/)

Cela conclut le langage de programmation pour 7 jours ! Il y a tellement plus à couvrir et j'espère que vous avez pu continuer à travers le contenu ci-dessus et être en mesure de comprendre certains des autres aspects du langage de programmation Go.

Ensuite, nous orientons notre attention vers Linux et certains des fondamentaux que nous devrions tous connaître.

À bientôt sur [Jour 14](day14.md).