## Modèles de Calcul de Microsoft Azure

Suite à la couverture des bases autour des modèles de sécurité dans Microsoft Azure hier, aujourd'hui, nous allons examiner les différents services de calcul disponibles pour nous dans Azure.

### Options de Disponibilité des Services

Cette section est proche de mon cœur étant donné mon rôle dans la gestion des données. Comme pour les solutions sur site, il est crucial de garantir la disponibilité de vos services.

- Haute Disponibilité (Protection au sein d'une région)
- Récupération après Sinistre (Protection entre les régions)
- Sauvegarde (Récupération à partir d'un point dans le temps)

Microsoft déploie plusieurs régions au sein d'une frontière géopolitique.

Deux concepts avec Azure pour la disponibilité des services : les ensembles et les zones.

Ensembles de Disponibilité : Fournissent de la résilience au sein d'un centre de données.

Zones de Disponibilité : Fournissent de la résilience entre les centres de données au sein d'une région.

### Machines Virtuelles

Probablement le point de départ pour quiconque dans le cloud public.

- Fournit une VM à partir d'une variété de séries et de tailles avec différentes capacités (parfois écrasantes) [Tailles pour les machines virtuelles dans Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/sizes)
- Il existe de nombreuses options et focalisations différentes pour les VM, allant des options de haute performance et de faible latence aux options de VM à mémoire élevée.
- Nous avons également un type de VM extensible que l'on peut trouver sous la série B. Cela est idéal pour les charges de travail où vous pouvez avoir une faible exigence de CPU la plupart du temps, mais nécessiter cette exigence de pic de performance peut-être une fois par mois.
- Les machines virtuelles sont placées sur un réseau virtuel qui peut fournir une connectivité à n'importe quel réseau.
- Prise en charge des systèmes d'exploitation invités Windows et Linux.
- Il existe également des noyaux optimisés pour Azure lorsqu'il s'agit de distributions Linux spécifiques. [Noyaux optimisés pour Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/endorsed-distros#azure-tuned-kernels)

### Modèles

J'ai mentionné précédemment que tout ce qui se trouve derrière ou sous Microsoft Azure est en JSON.

Il existe plusieurs portails et consoles de gestion différents que nous pouvons utiliser pour créer nos ressources ; la voie préférée sera via des modèles JSON.

Déploiements idempotents en mode incrémental ou complet - c'est-à-dire un état souhaité répétable.

Il existe une large sélection de modèles qui peuvent exporter des définitions de ressources déployées. J'aime penser à cette fonctionnalité de modèles comme quelque chose de similaire à AWS CloudFormation ou pourrait être Terraform pour une option multi-cloud. Nous couvrirons Terraform plus en détail dans la section Infrastructure as Code.

### Mise à l'Échelle

La mise à l'échelle automatique est une fonctionnalité importante du cloud public, permettant de réduire les ressources que vous n'utilisez pas ou de les augmenter lorsque vous en avez besoin.

Dans Azure, nous avons quelque chose appelé Virtual Machine Scale Sets (VMSS) pour IaaS. Cela permet la création et la mise à l'échelle automatiques à partir d'une image standard dorée basée sur des plannings et des métriques.

Cela est idéal pour mettre à jour les fenêtres afin que vous puissiez mettre à jour vos images et les déployer avec le moins d'impact possible.

D'autres services tels que Azure App Services ont une mise à l'échelle automatique intégrée.

### Conteneurs

Nous n'avons pas couvert les conteneurs en tant que cas d'utilisation et ce qu'ils sont et comment ils peuvent et devraient être nécessaires dans notre parcours d'apprentissage DevOps, mais nous devons mentionner qu'Azure a certains services spécifiques axés sur les conteneurs à mentionner.

Azure Kubernetes Service (AKS) : Fournit une solution Kubernetes gérée, sans avoir à se soucier du plan de contrôle ou de la gestion de la gestion sous-jacente du cluster. Plus sur Kubernetes également plus tard.

Azure Container Instances : Conteneurs en tant que service avec facturation à la seconde. Exécutez une image et intégrez-la à votre réseau virtuel, sans besoin d'orchestration de conteneurs.

Service Fabric : A de nombreuses capacités mais inclut l'orchestration pour les instances de conteneurs.

Azure dispose également du Container Registry qui fournit un registre privé pour les images Docker, les charts Helm, les artefacts OCI et les images. Encore plus à ce sujet lorsque nous atteindrons la section sur les conteneurs.

Nous devons également mentionner que de nombreux services de conteneurs peuvent effectivement utiliser des conteneurs sous le capot, mais cela est abstrait de votre besoin de gestion.

Ces services axés sur les conteneurs mentionnés se trouvent également dans d'autres clouds publics.

### Services d'Applications

- Azure Application Services fournit une solution d'hébergement d'applications qui offre une méthode facile pour établir des services.
- Déploiement et mise à l'échelle automatiques.
- Prise en charge des solutions basées sur Windows et Linux.
- Les services s'exécutent dans un plan de service d'application qui a un type et une taille.
- Nombre de services différents, y compris les applications web, les applications API et les applications mobiles.
- Prise en charge des slots de déploiement pour des tests et une promotion fiables.

### Informatique Serverless

Pour moi, le serverless est une étape passionnante à venir que je suis extrêmement intéressé à en savoir plus.

L'objectif du serverless est que nous ne payons que pour le temps d'exécution de la fonction et que nous n'avons pas besoin d'avoir des machines virtuelles ou des applications PaaS en cours d'exécution tout le temps. Nous exécutons simplement notre fonction lorsque nous en avons besoin, puis elle disparaît.

Azure Functions : Fournit du code serverless. Si nous nous souvenons de notre premier aperçu du cloud public, nous nous souviendrons de la couche d'abstraction de gestion ; avec les fonctions serverless, vous ne gérerez que le code.

Déclenché par des événements avec une mise à l'échelle massive, j'ai un plan pour construire quelque chose lorsque j'aurai une expérience pratique ici, espérons-le plus tard.

Fournit une liaison d'entrée et de sortie à de nombreux services Azure et tiers.

Prend en charge de nombreux langages de programmation différents. (C#, NodeJS, Python, PHP, batch, bash, Golang et Rust. Ou tout exécutable)

Azure Event Grid permet de déclencher une logique à partir de services et d'événements.

Azure Logic App fournit un workflow et une intégration basés sur des graphiques.

Nous pouvons également regarder Azure Batch, qui peut exécuter des travaux à grande échelle sur des nœuds Windows et Linux avec une gestion et une planification cohérentes.

## Ressources

- [Hybrid Cloud and MultiCloud](https://www.youtube.com/watch?v=qkj5W98Xdvw)
- [Microsoft Azure Fundamentals](https://www.youtube.com/watch?v=NKEFWyqJ5XA&list=WL&index=130&t=12s)
- [Google Cloud Digital Leader Certification Course](https://www.youtube.com/watch?v=UGRDM86MBIQ&list=WL&index=131&t=10s)
- [AWS Basics for Beginners - Full Course](https://www.youtube.com/watch?v=ulprqHHWlng&t=5352s)

À demain pour le [Jour 32](day32.md)