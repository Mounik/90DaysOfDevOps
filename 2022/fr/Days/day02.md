---
title: '#90DaysOfDevOps - Responsabilités d\'un Ingénieur DevOps - Jour 2'
published: false
description: 90DaysOfDevOps - Responsabilités d\'un Ingénieur DevOps
tags: 'devops, 90daysofdevops, apprentissage'
cover_image: null
canonical_url: null
id: 1048699
date: '2022-04-17T21:15:34Z'
---

## Responsabilités d'un Ingénieur DevOps

Espérons que vous arrivez ici après avoir parcouru les ressources publié sur [Jour 1 de #90DaysOfDevOps](day01.md).

Cela a été brièvement abordé dans le premier post, mais maintenant nous devons approfondir ce concept et comprendre qu'il y a deux parties principales lors de la création d'une application. Nous avons la partie **Développement** où les développeurs de logiciels programment l'application et la testent. Ensuite, nous avons la partie **Opérations** où l'application est déployée et maintenue sur un serveur.

## DevOps est le lien entre les deux

Pour comprendre le DevOps ou les tâches qu'un ingénieur DevOps effectuerait, nous devons comprendre les outils ou le processus et avoir une vue d'ensemble de ceux-ci et de la manière dont ils s'assemblent.

Tout commence avec l'application ! Vous verrez tellement de choses tout au long de ce parcours que tout tourne autour de l'application lorsqu'il s'agit de DevOps.

Les développeurs créeront une application, cela peut être fait avec de nombreuses stacks technologiques différentes et laissons cela à l'imagination pour l'instant car nous aborderons cela plus tard. Cela peut également impliquer de nombreux langages de programmation différents, outils de construction, dépôts de code, etc.

En tant qu'ingénieur DevOps, vous ne programmerez pas l'application, mais avoir une bonne compréhension des concepts de travail d'un développeur et des systèmes, outils et processus qu'ils utilisent est la clé du succès.

À un niveau très élevé, vous devrez savoir comment l'application est configurée pour communiquer avec tous ses services ou services de données requis, puis ajouter une exigence sur la manière dont cela peut ou doit être testé.

L'application devra être déployée quelque part, gardons cela généralement simple ici et faisons en sorte que ce soit un serveur, peu importe où mais un serveur. On s'attend ensuite à ce qu'il soit accessible par le client ou l'utilisateur final en fonction de l'application qui a été créée.

Ce serveur doit fonctionner quelque part, sur site, dans un cloud public, sans serveur (d'accord, je suis allé trop loin, nous ne couvrirons pas le sans serveur mais c'est une option et de plus en plus d'entreprises se dirigent dans cette direction). Quelqu'un doit créer et configurer ces serveurs et les préparer pour l'exécution de l'application. Maintenant, cet élément pourrait vous revenir en tant qu'ingénieur DevOps pour déployer et configurer ces serveurs.

Ces serveurs exécutent un système d'exploitation et, en général, il s'agira de Linux, mais nous avons une section d'une semaine entière où nous couvrons certaines des connaissances de base que vous devriez acquérir ici.

Il est également probable que nous devions communiquer avec d'autres services de notre réseau ou environnement, nous devons donc également avoir ce niveau de connaissance autour de la mise en réseau et de la configuration de celle-ci, cela pourrait également dans une certaine mesure revenir aux tâches de l'ingénieur DevOps. Encore une fois, nous aborderons cela en détail dans une section dédiée parlant de toutes les choses DNS, DHCP, load balancer, etc.

## Homme à tout faire, maître de rien

Je dirai cependant à ce stade que vous n'avez pas besoin d'être un spécialiste du réseau ou de l'infrastructure, vous avez besoin de connaissances de base sur la façon de faire fonctionner les choses et de les faire communiquer entre elles, de la même manière qu'avoir une connaissance de base d'un langage de programmation mais vous n'avez pas besoin d'être un développeur. Cependant, vous pourriez venir dans ce domaine en tant que spécialiste et c'est une excellente base pour vous adapter à d'autres domaines.

Vous ne prendrez probablement pas non plus la gestion quotidienne de ces serveurs ou de l'application.

Nous avons parlé de serveurs, mais il est probable que votre application soit développée pour s'exécuter en tant que conteneurs, ce qui s'exécute toujours sur un serveur pour la plupart, mais vous aurez également besoin d'une compréhension non seulement de la virtualisation, de l'infrastructure cloud en tant que service (IaaS) mais aussi de la conteneurisation, le focus dans ces 90 jours sera plus orienté vers les conteneurs.

## Vue d'ensemble de haut niveau

D'un côté, nous avons nos développeurs qui créent de nouvelles fonctionnalités (ainsi que des correctifs de bugs) pour l'application.

De l'autre côté, nous avons une sorte d'environnement, d'infrastructure ou de serveurs qui sont configurés et gérés pour exécuter cette application et communiquer avec tous ses services requis.

La grande question est de savoir comment intégrer ces fonctionnalités et correctifs de bugs dans nos produits et les rendre disponibles à ces utilisateurs finaux ?

Comment publions-nous la nouvelle version de l'application ? C'est l'une des principales tâches d'un ingénieur DevOps, et l'important ici n'est pas seulement de comprendre comment faire cela une fois, mais nous devons le faire de manière continue et automatisée, efficace, qui doit également inclure des tests !

C'est là que nous allons terminer cette journée d'apprentissage, espérons que cela a été utile. Au cours des prochains jours, nous allons approfondir certains autres domaines du DevOps, puis nous aborderons les sections qui approfondissent les outils et les processus et les avantages de ceux-ci.

## Ressources

Je suis toujours ouvert à l'ajout de ressources supplémentaires à ces fichiers readme car ils sont là comme outil d'apprentissage.

Mon conseil est de regarder tout ce qui suit et, espérons-le, que vous ayez également appris quelque chose du texte et des explications ci-dessus.

- [Qu'est-ce que DevOps ? - TechWorld avec Nana](https://www.youtube.com/watch?v=0yWAtQ6wYNM)
- [Qu'est-ce que DevOps ? - GitHub YouTube](https://www.youtube.com/watch?v=kBV8gPVZNEE)
- [Qu'est-ce que DevOps ? - IBM YouTube](https://www.youtube.com/watch?v=UbtB4sMaaNM)
- [Qu'est-ce que DevOps ? - AWS](https://aws.amazon.com/devops/what-is-devops/)
- [Qu'est-ce que DevOps ? - Microsoft](https://docs.microsoft.com/en-us/devops/what-is-devops)

Si vous êtes arrivé jusqu'ici, alors vous saurez si c'est là que vous voulez être ou non. À bientôt sur [Jour 3](day03.md).