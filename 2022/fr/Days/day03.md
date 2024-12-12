---
title: '#90DaysOfDevOps - Axé sur l\'Application - Jour 3'
published: false
description: 90DaysOfDevOps - Axé sur l'Application
tags: 'devops, 90daysofdevops, apprentissage'
cover_image: null
canonical_url: null
id: 1048825
---

## Cycle de Vie DevOps - Axé sur l'Application

Au cours des prochaines semaines, nous allons certainement rencontrer ces titres (Développement Continu, Tests, Déploiement, Surveillance) encore et encore. Si vous vous dirigez vers le rôle d'ingénieur DevOps, la répétabilité sera quelque chose à laquelle vous vous habituerez, mais l'amélioration constante à chaque fois est ce qui rend les choses intéressantes.

Dans cette heure, nous allons examiner la vue d'ensemble de l'application du début à la fin, puis de nouveau comme une boucle constante.

### Développement

Prenons un tout nouvel exemple d'une Application. Pour commencer, nous n'avons rien créé, peut-être qu'en tant que développeur, vous devez discuter avec votre client ou utilisateur final des exigences et élaborer un plan ou des exigences pour votre Application. Nous devons ensuite créer notre toute nouvelle application à partir de ces exigences.

En ce qui concerne les outils à ce stade, il n'y a pas de réelle exigence ici autre que de choisir votre IDE et le langage de programmation que vous souhaitez utiliser pour écrire votre application.

En tant qu'ingénieur DevOps, rappelez-vous que vous n'êtes probablement pas celui qui crée ce plan ou qui code l'application pour l'utilisateur final, ce sera un développeur qualifié.

Mais il ne serait pas inutile pour vous de pouvoir lire une partie du code afin de prendre les meilleures décisions d'infrastructure pour votre application.

Nous avons précédemment mentionné que cette application peut être écrite dans n'importe quel langage. Il est important que cela soit maintenu en utilisant un système de contrôle de version, c'est quelque chose que nous aborderons également en détail plus tard et, en particulier, nous plongerons dans **Git**.

Il est également probable que ce ne soit pas un seul développeur qui travaille sur ce projet, bien que cela puisse être le cas. Les meilleures pratiques nécessiteraient un dépôt de code pour stocker et collaborer sur le code, celui-ci pourrait être privé ou public et pourrait être hébergé ou déployé de manière privée. En général, vous entendrez parler de **GitHub ou GitLab** utilisés comme dépôt de code. Encore une fois, nous aborderons cela dans le cadre de notre section sur **Git** plus tard.

### Tests

À ce stade, nous avons nos exigences et notre application en cours de développement. Mais nous devons nous assurer que nous testons notre code dans tous les différents environnements disponibles pour nous ou spécifiquement peut-être pour le langage de programmation choisi.

Cette phase permet à la QA de tester les bugs, de plus en plus fréquemment, nous voyons des conteneurs utilisés pour simuler l'environnement de test, ce qui peut globalement améliorer les coûts de l'infrastructure physique ou cloud.

Cette phase sera probablement également automatisée dans le cadre de la prochaine zone qui est l'Intégration Continue.

La capacité à automatiser ces tests par rapport à 10, 100 ou même 1000 ingénieurs QA devant le faire manuellement parle d'elle-même, ces ingénieurs peuvent se concentrer sur autre chose dans la pile pour s'assurer que vous avancez plus rapidement et développez plus de fonctionnalités par rapport aux tests de bugs et de logiciels qui tendent à être le blocage de la plupart des versions logicielles traditionnelles qui utilisent une méthodologie en cascade.

### Intégration

Très important, l'Intégration est au milieu du cycle de vie DevOps. C'est la pratique dans laquelle les développeurs doivent commettre des changements dans le code source plus fréquemment. Cela pourrait être sur une base quotidienne ou hebdomadaire.

Avec chaque commit, votre application peut passer par les phases de test automatisées et cela permet une détection précoce des problèmes ou des bugs avant la phase suivante.

Maintenant, vous pourriez dire à ce stade "mais nous ne créons pas d'applications, nous les achetons chez un fournisseur de logiciels". Ne vous inquiétez pas, de nombreuses entreprises font cela et continueront à le faire et ce sera le fournisseur de logiciels qui se concentrera sur les 3 phases ci-dessus, mais vous voudrez peut-être toujours adopter la phase finale car cela permettra des déploiements plus rapides et plus efficaces de vos déploiements prêts à l'emploi.

Je suggérerais également que simplement avoir cette connaissance ci-dessus est très important car vous pourriez acheter un logiciel prêt à l'emploi aujourd'hui, mais qu'en est-il de demain ou plus tard... le prochain emploi peut-être ?

### Déploiement

D'accord, nous avons notre application construite et testée selon les exigences de notre utilisateur final et nous devons maintenant procéder et déployer cette application en production pour que nos utilisateurs finaux puissent la consommer.

C'est l'étape où le code est déployé sur les serveurs de production, maintenant c'est là que les choses deviennent extrêmement intéressantes et c'est là que nos 86 prochains jours plongent plus profondément dans ces domaines. Parce que différentes applications nécessitent éventuellement différents matériels ou configurations. C'est là que **la Gestion de la Configuration des Applications** et **l'Infrastructure en tant que Code** pourraient jouer un rôle clé dans votre cycle de vie DevOps. Il se peut que votre application soit **conteneurisée** mais également disponible pour s'exécuter sur une machine virtuelle. Cela nous amène ensuite à des plateformes comme **Kubernetes** qui orchestreraient ces conteneurs et s'assureraient que vous avez l'état souhaité disponible pour vos utilisateurs finaux.

De ces sujets en gras, nous allons entrer dans plus de détails au cours des prochaines semaines pour obtenir une meilleure connaissance de base de ce qu'ils sont et quand les utiliser.

### Surveillance

Les choses avancent rapidement ici et nous avons notre Application que nous mettons à jour en continu avec de nouvelles fonctionnalités et fonctionnalités et nous avons nos tests qui s'assurent qu'aucun gremlin n'est trouvé. Nous avons l'application en cours d'exécution dans notre environnement qui peut continuellement maintenir la configuration et les performances requises.

Mais maintenant, nous devons nous assurer que nos utilisateurs finaux obtiennent l'expérience qu'ils souhaitent. Ici, nous devons nous assurer que les Performances de notre Application sont continuellement surveillées, cette phase permettra à vos développeurs de prendre de meilleures décisions concernant les améliorations de l'application dans les futures versions pour mieux servir les utilisateurs finaux.

Cette section est également celle où nous allons capturer cette roue de retour sur les fonctionnalités qui ont été mises en œuvre et comment les utilisateurs finaux souhaitent les améliorer.

La fiabilité est également un facteur clé ici, à la fin de la journée, nous voulons que notre Application soit disponible à tout moment où elle est nécessaire. Cela conduit ensuite à d'autres domaines de **l'observabilité, la sécurité et la gestion des données** qui devraient être continuellement surveillés et les retours peuvent toujours être utilisés pour mieux améliorer, mettre à jour et publier l'application en continu.

Un membre de la communauté, [@\_ediri](https://twitter.com/_ediri), a également mentionné que dans le cadre de ce processus continu, les équipes FinOps devraient également être impliquées. Les applications et les données s'exécutent et sont stockées quelque part, vous devriez les surveiller en continu pour vous assurer que si les choses changent d'un point de vue des ressources, vos coûts ne causent pas une douleur financière majeure sur vos factures cloud.

Je pense que c'est aussi un bon moment pour évoquer l' "ingénieur DevOps" mentionné ci-dessus, bien qu'il y ait de nombreux postes d'ingénieur DevOps dans la nature que les gens occupent, ce n'est pas la manière idéale de positionner le processus de DevOps. Ce que je veux dire, c'est qu'en parlant à d'autres membres de la communauté, le titre d'ingénieur DevOps ne devrait pas être l'objectif de quiconque car, en réalité, toute position devrait adopter les processus et la culture DevOps expliqués ici. DevOps devrait être utilisé dans de nombreuses positions différentes telles que l'ingénieur/architecte cloud-native, l'administrateur de virtualisation, l'architecte/ingénieur cloud et l'administrateur d'infrastructure. Ce ne sont que quelques exemples, mais la raison d'utiliser l'ingénieur DevOps ci-dessus était vraiment de souligner l'étendue du processus utilisé par l'une des positions ci-dessus et plus encore.

## Ressources

Je suis toujours ouvert à l'ajout de ressources supplémentaires à ces fichiers readme car ils sont là comme outil d'apprentissage.

Mon conseil est de regarder tout ce qui suit et, espérons-le, vous avez également appris quelque chose du texte et des explications ci-dessus.

- [Développement Continu](https://www.youtube.com/watch?v=UnjwVYAN7Ns) Je dirai également que cela est axé sur la fabrication mais la culture lean peut être étroitement suivie avec DevOps.
- [Tests Continus - IBM YouTube](https://www.youtube.com/watch?v=RYQbmjLgubM)
- [Intégration Continue - IBM YouTube](https://www.youtube.com/watch?v=1er2cjUq1UI)
- [Surveillance Continue](https://www.youtube.com/watch?v=Zu53QQuYqJ0)
- [FinOps Foundation - Qu'est-ce que FinOps](https://www.finops.org/introduction/what-is-finops/)
- [**PAS GRATUIT** The Phoenix Project: A Novel About IT, DevOps, and Helping Your Business Win](https://www.amazon.com/Phoenix-Project-DevOps-Helping-Business/dp/1942788290/)

Si vous êtes arrivé jusqu'ici, alors vous saurez si c'est là que vous voulez être ou non. À bientôt sur [Jour 4](day04.md).