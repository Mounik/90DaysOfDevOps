## Vue d'ensemble : DevOps et Réseau

Comme pour toutes les sections, j'utilise des matériaux de formation opensource et gratuits et une grande partie du contenu peut être attribuée à d'autres. Dans le cas de la section sur le réseau, une grande majorité du contenu présenté provient de la série gratuite [Fundamentals of Networking](https://www.youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi) de [Practical Networking](https://www.practicalnetworking.net/). Il est mentionné dans les ressources ainsi qu'un lien, mais il est approprié de souligner cela car, du point de vue de la communauté, j'ai utilisé ce cours pour mieux comprendre certaines zones spécifiques des technologies. Ce dépôt est un dépôt pour ma prise de notes et permettre à la communauté de bénéficier, espérons-le, de cela et des ressources listées.

Bienvenue au Jour 21 ! Nous allons nous plonger dans le réseau au cours des 7 prochains jours. Le réseau et DevOps sont les thèmes principaux, mais nous devrons également aborder certains des fondamentaux du réseau.

En fin de compte, comme nous l'avons dit précédemment, le DevOps concerne un changement de culture et de processus au sein de votre organisation. Comme nous en avons discuté, cela peut inclure des machines virtuelles, des conteneurs ou Kubernetes, mais cela peut aussi inclure le réseau. Si nous appliquons ces principes DevOps à notre infrastructure, cela doit inclure le réseau, plus précisément, du point de vue de DevOps, vous devez également connaître le réseau, c'est-à-dire les différentes topologies et outils et stacks réseau dont nous disposons.

Je soutiendrais que nous devrions configurer nos dispositifs réseau en utilisant l'infrastructure en tant que code et automatiser tout comme nous le ferions pour nos machines virtuelles, mais pour cela, nous devons avoir une bonne compréhension de ce que nous automatisons.

### Qu'est-ce que NetDevOps | Network DevOps ?

Vous avez peut-être également entendu parler des termes Network DevOps ou NetDevOps. Peut-être êtes-vous déjà ingénieur réseau et avez une bonne compréhension des composants réseau au sein de l'infrastructure. Vous comprenez les éléments utilisés autour du réseau tels que DHCP, DNS, NAT, etc. Vous aurez également une bonne compréhension des options de réseau définies par matériel ou logiciel, des commutateurs, des routeurs, etc.

Mais si vous n'êtes pas ingénieur réseau, nous devons probablement acquérir des connaissances de base dans certains de ces domaines afin de comprendre l'objectif final de Network DevOps.

Mais en ce qui concerne ces termes, nous pouvons considérer NetDevOps ou Network DevOps comme l'application des principes et pratiques DevOps au réseau, en appliquant des outils de contrôle de version et d'automatisation à la création, aux tests, à la surveillance et aux déploiements du réseau.

Si nous pensons que Network DevOps nécessite une automatisation, nous avons mentionné précédemment que DevOps brise les silos entre les équipes. Si les équipes réseau ne changent pas pour adopter un modèle et un processus similaires, elles deviennent le goulot d'étranglement ou même la cause de l'échec global.

L'utilisation des principes d'automatisation autour de l'approvisionnement, de la configuration, des tests, du contrôle de version et du déploiement est un bon début. L'automatisation va globalement permettre une rapidité de déploiement, une stabilité de l'infrastructure réseau et une amélioration constante, ainsi que le partage du processus à travers plusieurs environnements une fois qu'ils ont été testés. Par exemple, une politique de réseau entièrement testée dans un environnement peut être rapidement utilisée dans un autre emplacement en raison de la nature de celle-ci étant en code par rapport à un processus rédigé manuellement comme cela aurait pu être le cas auparavant.
Un très bon point de vue et une présentation de cette réflexion peuvent être trouvés ici : [Network DevOps](https://www.thousandeyes.com/learning/techtorials/network-devops).

## Réseau : Les Bases

Oublions d'abord l'aspect DevOps et examinons brièvement certains des fondamentaux du réseautage.

### Dispositifs Réseau

Si vous préférez ce contenu sous forme de vidéo, consultez ces vidéos de Practical Networking :

* [Network Devices - Hosts, IP Addresses, Networks - Networking Fundamentals - Lesson 1a](https://www.youtube.com/watch?v=bj-Yfakjllc&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=1)
* [Network Devices - Hub, Bridge, Switch, Router - Networking Fundamentals - Lesson 1b](https://www.youtube.com/watch?v=H7-NR3Q3BeI&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=2)

**Hôte** : tout dispositif qui envoie ou reçoit du trafic.

![](Images/Day21_Networking1.png)

**Adresse IP** : l'identité de chaque hôte.

![](Images/Day21_Networking2.png)

**Réseau** : ce qui transporte le trafic entre les hôtes. Sans réseaux, il y aurait beaucoup de mouvements manuels de données !

Un groupe logique d'hôtes nécessitant une connectivité similaire.

![](Images/Day21_Networking3.png)

**Commutateurs** : facilitent la communication **au sein** d'un réseau. Un commutateur transmet des paquets de données entre les hôtes. Un commutateur envoie des paquets directement aux hôtes.

- Réseau : un groupement d'hôtes nécessitant une connectivité similaire.
- Les hôtes sur un réseau partagent le même espace d'adresses IP.

![](Images/Day21_Networking4.png)

**Routeur** : facilite la communication entre les réseaux. Comme nous l'avons dit précédemment, un commutateur gère la communication au sein d'un réseau, un routeur nous permet de joindre ces réseaux ensemble ou au moins de leur donner accès les uns aux autres si cela est autorisé.

Un routeur peut fournir un point de contrôle du trafic (sécurité, filtrage, redirection). De plus en plus de commutateurs fournissent également certaines de ces fonctions maintenant.

Les routeurs apprennent à quels réseaux ils sont connectés. Ceux-ci sont connus sous le nom de routes, une table de routage est l'ensemble des réseaux qu'un routeur connaît.

Un routeur a une adresse IP dans les réseaux auxquels il est connecté. Cette adresse IP sera également le moyen pour chaque hôte de sortir de son réseau local, également connu sous le nom de passerelle.

Les routeurs créent également la hiérarchie dans les réseaux dont j'ai parlé précédemment.

![](Images/Day21_Networking5.png)

## Commutateurs vs Routeurs

**Routage** : le processus de déplacement des données entre les réseaux.

- Un routeur est un dispositif dont le but principal est le routage.

**Commutation** : le processus de déplacement des données au sein des réseaux.

- Un commutateur est un dispositif dont le but principal est la commutation.

Ceci est vraiment une vue d'ensemble fondamentale des dispositifs car nous savons qu'il existe de nombreux dispositifs réseau différents tels que :

- Points d'accès
- Pare-feu
- Équilibreurs de charge
- Commutateurs de couche 3
- IDS / IPS
- Proxys
- Commutateurs virtuels
- Routeurs virtuels

Bien que tous ces dispositifs vont effectuer le routage et/ou la commutation.

Au cours des prochains jours, nous allons en apprendre davantage sur cette liste.

- Modèle OSI
- Protocoles réseau
- DNS (Domain Name System)
- NAT
- DHCP
- Sous-réseaux

## Ressources

* [Fundamentals of Networking](https://www.youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi)
* [Computer Networking full course](https://www.youtube.com/watch?v=IPvYjXCsTg8)

À demain pour le [Jour 22](day22.md)