## Plan > Code > Build > Testing > Release > Deploy > Operate > Monitor >

Aujourd'hui, nous allons nous concentrer sur les étapes individuelles du début à la fin et sur le cycle continu d'une application dans le monde DevOps.

![DevOps](Images/Day5_DevOps8.png)

### Plan

Tout commence avec le processus de planification, où l'équipe de développement se réunit pour déterminer quels types de fonctionnalités et de corrections de bugs seront déployés dans leur prochain sprint. En tant qu'ingénieur DevOps, c'est une opportunité pour vous de vous impliquer et de comprendre ce qui va arriver, de vous impliquer et d'influencer leurs décisions ou leur parcours, et de les aider à travailler avec l'infrastructure que vous avez construite ou de les orienter vers quelque chose qui fonctionnera mieux pour eux s'ils ne sont pas sur ce chemin. Un point clé à souligner ici est que les développeurs ou l'équipe d'ingénierie logicielle sont vos clients en tant qu'ingénieur DevOps. C'est donc votre opportunité de travailler avec votre client avant qu'ils ne prennent un mauvais chemin.

### Code

Une fois la session de planification terminée, ils vont commencer à écrire le code. Vous pouvez ou non être impliqué dans cette étape. L'un des endroits où vous pourriez être impliqué est lorsqu'ils écrivent du code. Vous pouvez les aider à mieux comprendre l'infrastructure. S'ils savent quels services sont disponibles et comment communiquer au mieux avec ces services, ils le feront. Ensuite, une fois qu'ils ont terminé, ils fusionneront ce code dans le dépôt.

### Build

C'est ici que nous lancerons le premier de nos processus d'automatisation, car nous allons prendre leur code et le construire. Selon le langage qu'ils utilisent, cela peut impliquer de le transpiler, de le compiler ou de créer une image Docker à partir de ce code. Quoi qu'il en soit, nous allons passer par ce processus en utilisant notre pipeline CI/CD.

### Testing

Une fois que nous avons construit le code, nous allons exécuter des tests dessus. L'équipe de développement écrit généralement les tests. Vous pouvez avoir une certaine influence sur les tests qui sont écrits, mais nous devons exécuter ces tests. Le test est un moyen pour nous d'essayer de minimiser l'introduction de problèmes en production. Cela ne garantit pas l'absence de problèmes, mais nous voulons nous rapprocher le plus possible d'une garantie que nous n'introduisons pas de nouveaux bugs et que nous ne cassons pas ce qui fonctionnait auparavant.

### Release

Une fois ces tests réussis, nous allons procéder au processus de release. Selon le type d'application sur lequel vous travaillez, cela peut ne pas être une étape. Le code peut simplement vivre dans le dépôt GitHub ou le dépôt git ou là où il se trouve, mais cela peut être le processus de prendre votre code compilé ou l'image Docker que vous avez construite et de la placer dans un registre ou un dépôt où elle est accessible par vos serveurs de production pour le processus de déploiement.

### Deploy

C'est la prochaine chose que nous faisons, car le déploiement est comme le but ultime de tout cela. Les déploiements sont le moment où nous mettons le code en production, et ce n'est qu'à ce moment-là que votre entreprise réalise la valeur de tout le temps, des efforts et du travail acharné que vous et l'équipe d'ingénierie logicielle avez mis dans ce produit jusqu'à présent.

### Operate

Une fois déployé, nous allons l'exploiter. L'exploitation peut impliquer quelque chose comme recevoir des appels de vos clients qui sont tous contrariés que le site ou leur application soit lent. Vous devez donc comprendre pourquoi et éventuellement mettre en place une mise à l'échelle automatique pour augmenter le nombre de serveurs disponibles pendant les périodes de pointe et diminuer le nombre de serveurs pendant les périodes creuses. Quoi qu'il en soit, ce sont toutes des métriques de type opérationnel. Une autre chose opérationnelle que vous faites est d'inclure une boucle de rétroaction de la production à votre équipe d'opérations, vous informant des événements clés qui se sont produits en production, comme un déploiement. En remontant d'un pas sur le déploiement, cela peut ou non être automatisé en fonction de votre environnement. L'objectif est toujours de l'automatiser lorsque cela est possible. Il existe certains environnements où vous devez peut-être faire quelques étapes avant d'être prêt à le faire, mais idéalement, vous voulez déployer automatiquement dans le cadre de votre processus d'automatisation. Si vous faites cela, il pourrait être judicieux d'inclure dans vos étapes opérationnelles une sorte de notification pour que votre équipe d'opérations sache qu'un déploiement a eu lieu.

### Monitor

Toutes les parties ci-dessus mènent à l'étape finale, car vous devez avoir une surveillance, en particulier autour des problèmes opérationnels, de la mise à l'échelle automatique et du dépannage. Vous ne savez pas qu'il y a un problème si vous n'avez pas de surveillance en place pour vous dire qu'il y a un problème. Certaines des choses que vous pourriez surveiller sont l'utilisation de la mémoire, l'utilisation du CPU, l'espace disque, le temps de réponse des points de terminaison API, la rapidité avec laquelle ce point de terminaison répond, et une grande partie de cela ce sont aussi les journaux. Les journaux permettent aux développeurs de voir ce qui se passe sans avoir à accéder aux systèmes de production.

### Rinse & Repeat

Une fois que c'est en place, vous revenez directement au début à l'étape de planification et vous recommencez tout le processus.

### Continuous

De nombreux outils nous aident à réaliser le processus continu ci-dessus, tout ce code et l'objectif ultime d'être complètement automatisé, l'infrastructure cloud ou tout environnement est souvent décrit comme Intégration Continue/Livraison Continue/Déploiement Continu ou "CI/CD" en abrégé. Nous passerons une semaine entière sur CI/CD plus tard dans les 90 jours avec quelques exemples et des tutoriels pour saisir les fondamentaux.

### Continuous Delivery

Continuous Delivery = Plan > Code > Build > Test

### Continuous Integration

C'est effectivement le résultat des phases de Continuous Delivery ci-dessus plus le résultat de la phase de Release. C'est le cas pour les échecs et les succès, mais cela est réintégré dans la livraison continue ou déplacé vers le déploiement continu.

Continuous Integration = Plan > Code > Build > Test > Release

### Continuous Deployment

Si vous avez une release réussie de votre intégration continue, passez au Continuous Deployment, qui inclut les phases suivantes :

CI Release est un succès = Continuous Deployment = Deploy > Operate > Monitor

Vous pouvez voir ces trois notions continues ci-dessus comme la simple collection de phases du cycle de vie DevOps.

Cette dernière partie était un peu un rappel pour moi du Jour 3, mais je pense que cela rend les choses plus claires pour moi.

### Resources

- [DevOps for Developers – Software or DevOps Engineer?](https://www.youtube.com/watch?v=a0-uE3rOyeU)
- [Techworld with Nana -DevOps Roadmap 2022 - How to become a DevOps Engineer? What is DevOps?](https://www.youtube.com/watch?v=9pZ2xmsSDdo&t=125s)
- [How to become a DevOps Engineer in 2021 - DevOps Roadmap](https://www.youtube.com/watch?v=5pxbp6FyTfk)

Si vous êtes arrivé jusqu'ici, vous saurez si c'est là que vous voulez être ou non.

À bientôt sur [Jour 6](day06.md).