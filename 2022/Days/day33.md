## Modèles de Réseau de Microsoft Azure + Gestion d'Azure

Comme si aujourd'hui marquait l'anniversaire de Microsoft Azure et son 12ème anniversaire ! (1er février 2022) Quoi qu'il en soit, nous allons couvrir les modèles de réseautage au sein de Microsoft Azure et certaines des options de gestion pour Azure. Jusqu'à présent, nous n'avons utilisé que le portail Azure, mais nous avons mentionné d'autres domaines qui peuvent être utilisés pour piloter et créer nos ressources au sein de la plateforme.

## Modèles de Réseau Azure

### Réseaux Virtuels

- Un réseau virtuel est une construction créée dans Azure.
- Un réseau virtuel a une ou plusieurs plages d'adresses IP qui lui sont attribuées.
- Les réseaux virtuels vivent au sein d'un abonnement au sein d'une région.
- Les sous-réseaux virtuels sont créés dans le réseau virtuel pour diviser la plage d'adresses du réseau.
- Les machines virtuelles sont placées dans des sous-réseaux virtuels.
- Toutes les machines virtuelles au sein d'un réseau virtuel peuvent communiquer.
- 65,536 adresses IP privées par réseau virtuel.
- Vous ne payez que pour le trafic sortant d'une région. (Données quittant la région)
- Prise en charge d'IPv4 et d'IPv6.
  - IPv6 pour les interfaces publiques et au sein des réseaux virtuels.

Nous pouvons lier les réseaux virtuels Azure aux VPC d'AWS. Cependant, il y a quelques différences à noter :

- Dans AWS, un VPC par défaut est créé, ce qui n'est pas le cas dans Microsoft Azure ; vous devez créer votre premier réseau virtuel selon vos besoins.
- Toutes les machines virtuelles par défaut dans Azure ont un accès NAT à Internet. Pas de passerelles NAT comme dans AWS.
- Dans Microsoft Azure, il n'y a pas de concept de sous-réseaux privés ou publics.
- Les adresses IP publiques sont une ressource qui peut être attribuée aux vNIC ou aux équilibreurs de charge.
- Le réseau virtuel et les sous-réseaux ont leurs propres listes de contrôle d'accès (ACL) permettant une délégation au niveau du sous-réseau.
- Sous-réseaux entre les zones de disponibilité, tandis que dans AWS, vous avez des sous-réseaux par zone de disponibilité.

Nous avons également le peering de réseaux virtuels. Cela permet aux réseaux virtuels de se connecter entre les locataires et les régions en utilisant le backbone Azure. Non transitif, mais peut être activé via le pare-feu Azure dans le réseau virtuel hub. L'utilisation d'un transit de passerelle permet aux réseaux virtuels peerés de bénéficier de la connectivité du réseau connecté, et un exemple pourrait être ExpressRoute vers des environnements sur site.

### Contrôle d'Accès

- Azure utilise des groupes de sécurité réseau, qui sont étatiques.
- Permet de créer des règles puis de les attribuer à un groupe de sécurité réseau.
- Les groupes de sécurité réseau sont appliqués aux sous-réseaux ou aux machines virtuelles.
- Lorsqu'ils sont appliqués à un sous-réseau, ils sont toujours appliqués au niveau de la carte réseau de la machine virtuelle, ce n'est pas un appareil "edge".

![](Images/Day33_Cloud1.png)

- Les règles sont combinées dans un groupe de sécurité réseau.
- En fonction de la priorité, des configurations flexibles sont possibles.
- Un numéro de priorité plus bas signifie une priorité plus élevée.
- La plupart de la logique est basée sur les adresses IP, mais certains tags et labels peuvent également être utilisés.

| Description      | Priority | Source Address     | Source Port | Destination Address | Destination Port | Action |
| ---------------- | -------- | ------------------ | ----------- | ------------------- | ---------------- | ------ |
| Inbound 443      | 1005     | *                  | *           | *                   | 443              | Allow  |
| ILB              | 1010     | Azure Load Balancer | *           | *                   | 10000            | Allow  |
| Deny All Inbound | 4000     | *                  | *           | *                   | *                | Deny   |

Nous avons également des groupes de sécurité d'applications (ASG).

- Alors que les NSG se concentrent sur les plages d'adresses IP, ce qui peut être difficile à maintenir pour les environnements en croissance.
- Les ASG permettent de définir des noms réels (monikers) pour différents rôles d'application (serveurs web, serveurs de base de données, WebApp1, etc.).
- La carte réseau de la machine virtuelle devient membre d'un ou plusieurs ASG.

Les ASG peuvent ensuite être utilisés dans des règles qui font partie des groupes de sécurité réseau pour contrôler le flux de communication et peuvent toujours utiliser les fonctionnalités NSG comme les tags de service.

| Action | Name               | Source     | Destination | Port         |
| ------ | ------------------ | ---------- | ----------- | ------------ |
| Allow  | AllowInternetToWeb  | Internet   | WebServers  | 443(HTTPS)   |
| Allow  | AllowWebToApp      | WebServers | AppServers  | 443(HTTPS)   |
| Allow  | AllowAppToDB       | AppServers | DbServers   | 1433 (MSSQL) |
| Deny   | DenyAllInbound     | Any        | Any         | Any          |

### Équilibrage de Charge

Microsoft Azure dispose de deux solutions d'équilibrage de charge distinctes. (la première partie, il y a des tiers disponibles sur la place de marché Azure.) Les deux peuvent fonctionner avec des points de terminaison orientés vers l'extérieur ou l'intérieur.

- Équilibreur de charge (couche 4) prenant en charge la distribution basée sur le hachage et la redirection de port.
- Passerelle d'application (couche 7) prenant en charge des fonctionnalités telles que le déchargement SSL, l'affinité de session basée sur les cookies et le routage de contenu basé sur l'URL.

Avec la passerelle d'application, vous pouvez également utiliser le composant pare-feu d'application web.

## Outils de Gestion Azure

Nous avons passé la plupart de notre temps théorique à parcourir le portail Azure. Je suggérerais que lorsqu'il s'agit de suivre une culture et un processus DevOps, beaucoup de ces tâches, en particulier autour de l'approvisionnement, seront effectuées via une API ou un outil en ligne de commande. Je voulais aborder certains de ces autres outils de gestion dont nous disposons, car nous devons les connaître lorsque nous automatisons l'approvisionnement de nos environnements Azure.

### Portail Azure

Le portail Microsoft Azure est une console basée sur le web qui offre une alternative aux outils en ligne de commande. Vous pouvez gérer vos abonnements au sein du portail Azure. Construire, gérer et surveiller tout, d'une simple application web à des déploiements cloud complexes. Une autre chose que vous trouverez dans le portail sont ces fil d'Ariane, JSON comme mentionné précédemment est le sous-jacent de toutes les ressources Azure. Il se peut que vous commenciez dans le portail pour comprendre les fonctionnalités, les services et les fonctionnalités, mais que vous compreniez ensuite le JSON sous-jacent pour l'incorporer dans vos flux de travail automatisés.

![](Images/Day33_Cloud2.png)

Il y a aussi le portail Azure Preview, qui peut être utilisé pour voir et tester de nouveaux services et améliorations à venir.

![](Images/Day33_Cloud3.png)

### PowerShell

Avant de nous lancer dans Azure PowerShell, il est utile d'introduire PowerShell en premier. PowerShell est un cadre de gestion de la configuration et de l'automatisation des tâches, une interface de ligne de commande et un langage de script. Nous pourrions et oserais-je dire que cela ressemble à ce que nous avons couvert dans la section Linux autour du script shell. PowerShell était très présent sur le système d'exploitation Windows, mais il est maintenant multiplateforme.

Azure PowerShell est un ensemble de cmdlets pour gérer les ressources Azure directement à partir de la ligne de commande PowerShell.

Nous pouvons voir ci-dessous que vous pouvez vous connecter à votre abonnement en utilisant la commande PowerShell `Connect-AzAccount`.

![](Images/Day33_Cloud4.png)

Ensuite, si nous voulions trouver des commandes spécifiques associées aux machines virtuelles Azure, nous pouvons exécuter la commande suivante. Vous pourriez passer des heures à apprendre et à comprendre davantage sur ce langage de programmation PowerShell.

![](Images/Day33_Cloud5.png)

Il existe de superbes guides de démarrage rapide de Microsoft pour commencer et approvisionner des services à partir de PowerShell [ici](https://docs.microsoft.com/en-us/powershell/azure/get-started-azureps?view=azps-7.1.0).

### Visual Studio Code

Comme beaucoup, et comme vous l'avez tous vu, mon IDE de prédilection est Visual Studio Code.

Visual Studio Code est un éditeur de code source libre fait par Microsoft pour Windows, Linux et macOS.

Vous verrez ci-dessous qu'il existe de nombreuses intégrations et outils intégrés dans Visual Studio Code que vous pouvez utiliser pour interagir avec Microsoft Azure et les services qui s'y trouvent.

![](Images/Day33_Cloud6.png)

### Cloud Shell

Azure Cloud Shell est une interface de shell interactive, authentifiée et accessible par navigateur pour gérer les ressources Azure. Il offre la flexibilité de choisir l'expérience shell qui correspond le mieux à votre façon de travailler.

![](Images/Day33_Cloud7.png)

Vous pouvez voir ci-dessous que lorsque nous lançons pour la première fois Cloud Shell dans le portail, nous pouvons choisir entre Bash et PowerShell.

![](Images/Day33_Cloud8.png)

Pour utiliser le cloud shell, vous devrez fournir un peu de stockage dans votre abonnement.

Lorsque vous sélectionnez pour utiliser le cloud shell, il lance une machine ; ces machines sont temporaires, mais vos fichiers sont persistants de deux manières : via une image de disque et un partage de fichiers monté.

![](Images/Day33_Cloud9.png)

- Cloud Shell s'exécute sur un hôte temporaire fourni par session, par utilisateur.
- Cloud Shell s'arrête après 20 minutes sans activité interactive.
- Cloud Shell nécessite un partage de fichiers Azure à monter.
- Cloud Shell utilise le même partage de fichiers Azure pour Bash et PowerShell.
- Cloud Shell est attribué à une machine par compte utilisateur.
- Cloud Shell persiste $HOME en utilisant une image de 5 Go conservée dans votre partage de fichiers.
- Les autorisations sont définies comme un utilisateur Linux régulier dans Bash.

Ce qui précède a été copié de [Vue d'ensemble de Cloud Shell](https://docs.microsoft.com/en-us/azure/cloud-shell/overview).

### Azure CLI

Enfin, je veux couvrir l'Azure CLI. L'Azure CLI peut être installée sur Windows, Linux et macOS. Une fois installée, vous pouvez taper `az` suivi d'autres commandes pour créer, mettre à jour, supprimer et afficher les ressources Azure.

Lorsque je suis entré dans mon apprentissage Azure, j'étais un peu confus par le fait qu'il y avait Azure PowerShell et l'Azure CLI.

J'aimerais avoir des retours de la communauté à ce sujet également. Mais la façon dont je le vois, c'est qu'Azure PowerShell est un module ajouté à Windows PowerShell ou PowerShell Core (également disponible sur d'autres systèmes d'exploitation, mais pas tous) tandis que l'Azure CLI est un programme de ligne de commande multiplateforme qui se connecte à Azure et exécute ces commandes.

Ces deux options ont une syntaxe différente, bien qu'elles puissent, d'après ce que je peux voir et ce que j'ai fait, effectuer des tâches très similaires.

Par exemple, la création d'une machine virtuelle à partir de PowerShell utiliserait le cmdlet `New-AzVM`, tandis que l'Azure CLI utiliserait `az vm create`.

Vous avez vu précédemment que j'ai le module Azure PowerShell installé sur mon système, mais j'ai également l'Azure CLI installé qui peut être appelé via PowerShell sur ma machine Windows.

![](Images/Day33_Cloud10.png)

L'essentiel ici, comme nous l'avons déjà mentionné, concerne le choix du bon outil. Azure fonctionne sur l'automatisation. Chaque action que vous entreprenez dans le portail se traduit quelque part par du code exécuté pour lire, créer, modifier ou supprimer des ressources.

Azure CLI

- Interface de ligne de commande multiplateforme, installable sur Windows, macOS, Linux.
- S'exécute dans Windows PowerShell, Cmd, Bash et autres shells Unix.

Azure PowerShell

- Module PowerShell multiplateforme, s'exécute sur Windows, macOS, Linux.
- Nécessite Windows PowerShell ou PowerShell.

Si pour une raison quelconque vous ne pouvez pas utiliser PowerShell dans votre environnement mais que vous pouvez utiliser .md ou bash, alors l'Azure CLI sera votre choix.

Ensuite, nous prenons toutes les théories que nous avons parcourues et créons quelques scénarios et nous lançons dans Azure.

## Ressources

- [Hybrid Cloud and MultiCloud](https://www.youtube.com/watch?v=qkj5W98Xdvw)
- [Microsoft Azure Fundamentals](https://www.youtube.com/watch?v=NKEFWyqJ5XA&list=WL&index=130&t=12s)
- [Google Cloud Digital Leader Certification Course](https://www.youtube.com/watch?v=UGRDM86MBIQ&list=WL&index=131&t=10s)
- [AWS Basics for Beginners - Full Course](https://www.youtube.com/watch?v=ulprqHHWlng&t=5352s)

À demain pour le [Jour 34](day34.md)