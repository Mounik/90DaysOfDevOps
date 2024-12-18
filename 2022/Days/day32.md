## Modèles de Stockage de Microsoft Azure

### Services de Stockage

- Les services de stockage Azure sont fournis par des comptes de stockage.
- Les comptes de stockage sont principalement accessibles via l'API REST.
- Un compte de stockage doit avoir un nom unique qui fait partie d'un nom DNS `<Nom du compte de stockage>.core.windows.net`.
- Diverses options de réplication et de chiffrement.
- Se trouve dans un groupe de ressources.

Nous pouvons créer notre groupe de stockage en recherchant simplement "Groupe de stockage" dans la barre de recherche en haut du portail Azure.

![](Images/Day32_Cloud1.png)

Nous pouvons ensuite suivre les étapes pour créer notre compte de stockage en nous souvenant que ce nom doit être unique et qu'il doit être en minuscules, sans espaces, mais peut inclure des chiffres.

![](Images/Day32_Cloud2.png)

Nous pouvons également choisir le niveau de redondance que nous souhaitons pour notre compte de stockage et tout ce que nous y stockons. Plus vous descendez dans la liste, plus l'option est coûteuse, mais aussi plus vos données sont réparties.

Même l'option de redondance par défaut nous donne trois copies de nos données.

[Redondance du stockage Azure](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy)

Résumé du lien ci-dessus :

- **Stockage localement redondant** : réplique vos données trois fois dans un seul centre de données de la région principale.
- **Stockage géo-redondant** : copie vos données de manière synchrone trois fois dans un seul emplacement physique de la région principale en utilisant LRS.
- **Stockage redondant par zone** : réplique vos données Azure Storage de manière synchrone dans trois zones de disponibilité Azure de la région principale.
- **Stockage géo-redondant par zone** : combine la haute disponibilité fournie par la redondance entre les zones avec la protection contre les pannes régionales fournie par la géo-réplication. Les données d'un compte de stockage GZRS sont copiées dans trois zones de disponibilité Azure de la région principale et sont également répliquées dans une deuxième région géographique pour se protéger contre les catastrophes régionales.

![](Images/Day32_Cloud3.png)

En revenant aux options de performance. Nous avons le choix entre Standard et Premium. Nous avons choisi Standard dans notre parcours, mais Premium vous offre certaines options spécifiques.

![](Images/Day32_Cloud4.png)

Ensuite, dans le menu déroulant, vous pouvez voir que nous avons ces trois options à choisir.

![](Images/Day32_Cloud5.png)

Il existe de nombreuses autres options avancées disponibles pour votre compte de stockage, mais pour l'instant, nous n'avons pas besoin de nous plonger dans ces domaines. Ces options concernent le chiffrement et la protection des données.

### Disques Gérés

L'accès au stockage peut être réalisé de plusieurs manières différentes.

Accès authentifié via :

- Une clé partagée pour un contrôle total.
- Une signature d'accès partagé pour un accès délégué et granulaire.
- Azure Active Directory (lorsque disponible).

Accès public :

- Un accès public peut également être accordé pour permettre un accès anonyme, y compris via HTTP.
- Un exemple pourrait être d'héberger du contenu et des fichiers de base dans un blob de blocs afin qu'un navigateur puisse voir et télécharger ces données.

Si vous accédez à votre stockage depuis un autre service Azure, le trafic reste au sein d'Azure.

En ce qui concerne les performances de stockage, nous avons deux types différents :

- **Standard** : nombre maximum d'IOPS.
- **Premium** : nombre garanti d'IOPS.

IOPS => opérations d'entrée/sortie par seconde.

Il y a également une différence entre les disques non gérés et gérés à considérer lors du choix du stockage adapté à la tâche que vous avez.

### Stockage de Machines Virtuelles

- Les disques de système d'exploitation de machines virtuelles sont généralement stockés sur un stockage persistant.
- Certaines charges de travail sans état ne nécessitent pas de stockage persistant, et une latence réduite est un avantage plus important.
- Il existe des machines virtuelles qui prennent en charge des disques gérés par le système d'exploitation éphémère qui sont créés sur le stockage local du nœud.
  - Ceux-ci peuvent également être utilisés avec des ensembles de mise à l'échelle de machines virtuelles.

Les disques gérés sont un stockage de blocs durable qui peut être utilisé avec les machines virtuelles Azure. Vous pouvez avoir un stockage de disques Ultra, SSD Premium, SSD Standard ou HDD Standard. Ils portent également certaines caractéristiques.

- Prise en charge des instantanés et des images.
- Mouvement simple entre les unités SKU.
- Meilleure disponibilité lorsqu'ils sont combinés avec des ensembles de disponibilité.
- Facturé en fonction de la taille du disque, et non du stockage consommé.

## Stockage d'Archives

- **Niveau Cool** : un niveau cool de stockage est disponible pour les blobs de blocs et les blobs d'ajout.
  - Coût de stockage plus bas.
  - Coût de transaction plus élevé.
- **Niveau Archive** : le stockage d'archives est disponible pour les blobs de blocs.
  - Configuré sur une base par blob.
  - Coût moins élevé, latence de récupération des données plus longue.
  - Même durabilité des données que le stockage Azure régulier.
  - La hiérarchisation personnalisée des données peut être activée selon les besoins.

### Partage de Fichiers

À partir de la création ci-dessus de notre compte de stockage, nous pouvons maintenant créer des partages de fichiers.

![](Images/Day32_Cloud6.png)

Cela fournira des partages de fichiers SMB2.1 et 3.0 dans Azure.

Utilisable au sein d'Azure et à l'extérieur via SMB3 et le port 445 ouvert sur Internet.

Fournit un stockage de fichiers partagé dans Azure.

Peut être mappé à l'aide de clients SMB standard en plus de l'API REST.

Vous pourriez également remarquer [Azure NetApp Files](https://vzilla.co.uk/vzilla-blog/azure-netapp-files-how) (SMB et NFS).

### Services de Mise en Cache et de Médias

Le réseau de distribution de contenu Azure fournit une mise en cache de contenu web statique avec des emplacements dans le monde entier.

Azure Media Services fournit des technologies de transcodage de médias en plus des services de lecture.

## Modèles de Base de Données Microsoft Azure

Le [Jour 28](day28.md), nous avons couvert diverses options de services. L'une d'entre elles était PaaS (Platform as a Service) où vous abstrait une grande partie de l'infrastructure et du système d'exploitation, et vous êtes laissé avec le contrôle de l'application ou, dans ce cas, des modèles de base de données.

### Bases de Données Relationnelles

Azure SQL Database fournit une base de données relationnelle en tant que service basée sur Microsoft SQL Server.

Il s'agit de SQL exécutant la dernière branche SQL avec le niveau de compatibilité de la base de données disponible où une version de fonctionnalité spécifique est requise.

Il existe quelques options sur la manière dont cela peut être configuré ; nous pouvons fournir une seule base de données qui fournit une base de données dans l'instance, tandis qu'un pool élastique permet plusieurs bases de données qui partagent un pool de capacité et se mettent à l'échelle collectivement.

Ces instances de base de données peuvent être accédées comme des instances SQL régulières.

Offres gérées supplémentaires pour MySQL, PostgreSQL et MariaDB.

![](Images/Day32_Cloud7.png)

### Solutions NoSQL

Azure Cosmos DB est une implémentation NoSQL agnostique de schéma.

99,99 % de SLA.

Base de données distribuée mondialement avec des latences à un chiffre à la 99e percentile partout dans le monde avec un homing automatique.

Clé de partition utilisée pour le partitionnement/sharding/distribution des données.

Prend en charge divers modèles de données (documents, clé-valeur, graphe, colonne).

Prend en charge diverses API (DocumentDB SQL, MongoDB, Azure Table Storage et Gremlin).

![](Images/Day32_Cloud9.png)

Divers modèles de cohérence sont disponibles en fonction du [théorème CAP](https://en.wikipedia.org/wiki/CAP_theorem).

![](Images/Day32_Cloud8.png)

### Mise en Cache

Sans entrer dans les détails des systèmes de mise en cache tels que Redis, je voulais inclure le fait que Microsoft Azure dispose d'un service appelé Azure Cache for Redis.

Azure Cache for Redis fournit un magasin de données en mémoire basé sur le logiciel Redis.

- C'est une implémentation du cache Redis open-source.
  - Une instance de cache Redis hébergée et sécurisée.
  - Différents niveaux sont disponibles.
  - L'application doit être mise à jour pour utiliser le cache.
  - Destiné à une application qui a des exigences de lecture élevées par rapport aux écritures.
  - Basé sur un magasin clé-valeur.

![](Images/Day32_Cloud10.png)

J'apprécie que les derniers jours aient été beaucoup de prise de notes et de théorie sur Microsoft Azure, mais je voulais couvrir les éléments de base avant de nous plonger dans les aspects pratiques de la manière dont ces composants fonctionnent ensemble et fonctionnent.

Nous avons encore un peu de théorie sur la mise en réseau avant de pouvoir déployer des services basés sur des scénarios. Nous voulons également examiner certaines des différentes manières dont nous pouvons interagir avec Microsoft Azure plutôt que d'utiliser simplement le portail que nous avons utilisé jusqu'à présent.

## Ressources

- [Hybrid Cloud and MultiCloud](https://www.youtube.com/watch?v=qkj5W98Xdvw)
- [Microsoft Azure Fundamentals](https://www.youtube.com/watch?v=NKEFWyqJ5XA&list=WL&index=130&t=12s)
- [Google Cloud Digital Leader Certification Course](https://www.youtube.com/watch?v=UGRDM86MBIQ&list=WL&index=131&t=10s)
- [AWS Basics for Beginners - Full Course](https://www.youtube.com/watch?v=ulprqHHWlng&t=5352s)

À demain pour le [Jour 33](day33.md)