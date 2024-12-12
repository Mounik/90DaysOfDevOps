## Vue d'ensemble : DevOps et Apprentissage d'un Langage de Programmation

Il est juste de dire que pour réussir à long terme en tant qu'ingénieur DevOps, vous devez connaître au moins un langage de programmation à un niveau fondamental. Je veux profiter de cette première session de cette section pour explorer pourquoi cette compétence est si cruciale à avoir, et espérons qu'à la fin de cette semaine ou de cette section, vous aurez une meilleure compréhension du pourquoi, du comment et de ce qu'il faut faire pour progresser dans votre parcours d'apprentissage.

Si je devais demander sur les réseaux sociaux si vous avez besoin de compétences en programmation pour des rôles liés à DevOps, la réponse serait probablement un oui ferme. Faites-moi savoir si vous pensez autrement. Mais alors, une question plus importante se pose : quel langage de programmation ? La réponse la plus courante que j'ai vue ici est Python, ou de plus en plus souvent, Golang ou Go devrait être le langage que vous apprenez.

Pour réussir en DevOps, vous devez avoir une bonne connaissance des compétences en programmation, c'est mon point de vue. Mais nous devons comprendre pourquoi nous en avons besoin pour choisir le bon chemin.

## Comprendre pourquoi vous devez apprendre un langage de programmation

La raison pour laquelle Python et Go sont si souvent recommandés pour les ingénieurs DevOps est que beaucoup des outils DevOps sont écrits en Python ou en Go, ce qui est logique si vous allez construire des outils DevOps. Cela est important car cela déterminera vraiment ce que vous devriez apprendre et ce qui serait probablement le plus bénéfique. Si vous allez construire des outils DevOps ou rejoindre une équipe qui le fait, il serait logique d'apprendre ce même langage. Si vous allez être fortement impliqué dans Kubernetes ou les conteneurs, il est plus que probable que vous voudrez choisir Go comme langage de programmation. Pour moi, l'entreprise pour laquelle je travaille (Kasten by Veeam) est dans l'écosystème Cloud-Native, axée sur la gestion des données pour Kubernetes, et tout est écrit en Go.

Mais ensuite, vous pourriez ne pas avoir de raison claire pour choisir. Vous pourriez être étudiant ou en transition de carrière sans décision réelle prise pour vous. Dans cette situation, je pense que vous devriez choisir celui qui semble résonner et correspondre aux applications avec lesquelles vous souhaitez travailler.

N'oubliez pas que je ne cherche pas à devenir développeur de logiciels ici. Je veux juste comprendre un peu plus le langage de programmation pour pouvoir lire et comprendre ce que font ces outils, et cela mène éventuellement à la manière dont nous pouvons aider à améliorer les choses.

Il est également important de savoir comment vous interagissez avec ces outils DevOps, qui pourraient être Kasten K10 ou Terraform et HCL. Ce sont ce que nous appellerons des fichiers de configuration, et c'est ainsi que vous interagissez avec ces outils DevOps pour faire avancer les choses. Communément, ceux-ci seront en YAML. (Nous pourrions utiliser le dernier jour de cette section pour plonger un peu dans YAML).

## Ai-je juste parlé de ne pas apprendre un langage de programmation ?

La plupart du temps, ou selon le rôle, vous aiderez les équipes d'ingénierie à intégrer DevOps dans leur flux de travail, beaucoup de tests autour de l'application et vous assurerez que le flux de travail construit s'aligne sur ces principes DevOps que nous avons mentionnés au cours des premiers jours. Mais en réalité, cela consistera souvent à dépanner un problème de performance de l'application ou quelque chose de ce genre. Cela nous ramène à mon point de départ et à mon raisonnement : le langage de programmation que je dois connaître est celui dans lequel le code est écrit. Si leur application est écrite en NodeJS, cela n'aidera pas beaucoup si vous avez un badge Go ou Python.

## Pourquoi Go ?

Pourquoi Golang est le prochain langage de programmation pour DevOps. Go est devenu un langage de programmation très populaire ces dernières années. Selon l'enquête StackOverflow de 2021, Go est arrivé en quatrième position des langages de programmation, de script et de balisage les plus recherchés, Python étant en tête, mais écoutez-moi. [Enquête StackOverflow 2021 sur les développeurs – Lien des plus recherchés](https://insights.stackoverflow.com/survey/2021#section-most-loved-dreaded-and-wanted-programming-scripting-and-markup-languages)

Comme je l'ai également mentionné, certains des outils et plateformes DevOps les plus connus sont écrits en Go, comme Kubernetes, Docker, Grafana et Prometheus.

Quelles sont certaines des caractéristiques de Go qui le rendent si bon pour DevOps ?

## Construction et Déploiement de Programmes Go

Un avantage d'utiliser un langage comme Python, qui est interprété dans un rôle DevOps, est que vous n'avez pas besoin de compiler un programme Python avant de l'exécuter. Surtout pour des tâches d'automatisation plus petites, vous ne voulez pas être ralenti par un processus de construction qui nécessite une compilation. Bien que Go soit un langage de programmation compilé, **Go compile directement en code machine**. Go est également connu pour ses temps de compilation rapides.

## Go vs Python pour DevOps

Les programmes Go sont liés statiquement, ce qui signifie que lorsque vous compilez un programme Go, tout est inclus dans un seul exécutable binaire, et aucune dépendance externe ne sera requise, ce qui devrait être installé sur la machine distante. Cela facilite le déploiement des programmes Go, contrairement aux programmes Python qui utilisent des bibliothèques externes. Vous devez vous assurer que toutes ces bibliothèques sont installées sur la machine distante sur laquelle vous souhaitez exécuter le programme.

Go est un langage indépendant de la plateforme, ce qui signifie que vous pouvez produire des exécutables binaires pour *tous les systèmes d'exploitation, Linux, Windows, macOS, etc., et c'est très facile à faire. Avec Python, il n'est pas aussi facile de créer ces exécutables binaires pour des systèmes d'exploitation particuliers.

Go est un langage très performant, avec une compilation rapide et un temps d'exécution rapide avec une utilisation moindre des ressources comme le CPU et la mémoire, surtout par rapport à Python. De nombreuses optimisations ont été mises en œuvre dans le langage Go qui le rendent si performant. (Ressources ci-dessous)

Contrairement à Python, qui nécessite souvent l'utilisation de bibliothèques tierces pour implémenter un programme Python particulier, Go inclut une bibliothèque standard qui contient la majorité des fonctionnalités dont vous auriez besoin pour DevOps intégrées directement. Cela inclut des fonctionnalités de traitement de fichiers, des services web HTTP, du traitement JSON, un support natif pour la concurrence et le parallélisme ainsi que des tests intégrés.

Cela ne signifie en aucun cas que Python est mauvais. Je donne simplement mes raisons de choisir Go, mais ce n'est pas seulement Go vs Python. C'est généralement parce que cela a du sens puisque l'entreprise pour laquelle je travaille développe des logiciels en Go.

Je dirais que une fois que vous avez appris votre premier langage de programmation, il devient plus facile d'en apprendre d'autres. Vous n'aurez probablement jamais un seul emploi dans une entreprise où vous n'aurez pas à gérer, architecturer, orchestrer, déboguer des applications JavaScript et NodeJS.

## Ressources

- [Enquête StackOverflow 2021 sur les développeurs](https://insights.stackoverflow.com/survey/2021)
- [Pourquoi nous choisissons Golang pour apprendre](https://www.youtube.com/watch?v=7pLqIIAqZD4&t=9s)
- [Jake Wright - Apprenez Go en 12 minutes](https://www.youtube.com/watch?v=C8LgvuEBraI&t=312s)
- [Techworld With Nana - Cours complet sur Golang - 3 heures 24 minutes](https://www.youtube.com/watch?v=yyUHQIec83I)
- [Techworld With Nana - Learn Go by Building a TodoList App](https://www.youtube.com/watch?v=XCZWyN9ZbEQ)
- [**PAS GRATUIT** Nigel Poulton Pluralsight - Fondamentaux de Go - 3 heures 26 minutes](https://www.pluralsight.com/courses/go-fundamentals)
- [FreeCodeCamp - Apprenez la programmation Go - Tutoriel Golang pour débutants](https://www.youtube.com/watch?v=YS4e4q9oBaU&t=1025s)
- [Hitesh Choudhary - Liste de lecture complète](https://www.youtube.com/playlist?list=PLRAV69dS1uWSR89FRQGZ6q9BR2b44Tr9N)

Maintenant, pour les 6 prochains jours de ce sujet, j'ai l'intention de parcourir certaines des ressources listées ci-dessus et de documenter mes notes pour chaque jour. Vous remarquerez qu'elles durent généralement environ 3 heures pour un cours complet. Je voulais partager ma liste complète afin que, si vous avez le temps, vous puissiez avancer et travailler sur chacune d'elles si le temps le permet. Je vais m'en tenir à mon heure d'apprentissage chaque jour.

À bientôt sur [Jour 8](day08.md).