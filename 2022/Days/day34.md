## Microsoft Azure Scénarios Pratiques

Les six derniers jours ont été axés sur Microsoft Azure et le cloud public en général. Une grande partie de cette fondation devait contenir beaucoup de théorie pour comprendre les blocs de construction d'Azure, mais cela se traduira également bien par les autres principaux fournisseurs de cloud.

J'ai mentionné dès le début l'importance d'acquérir une connaissance fondamentale du cloud public et de choisir un fournisseur pour commencer. Si vous dansez entre différents clouds, je pense que vous pouvez facilement vous perdre, tandis que choisir un seul vous permet de comprendre les fondamentaux et, une fois que vous les avez, il est assez facile de passer aux autres clouds et d'accélérer votre apprentissage.

Dans cette dernière session, je vais choisir et sélectionner mes scénarios pratiques à partir de cette page, qui est une référence créée par Microsoft et utilisée pour la préparation du [AZ-104 Microsoft Azure Administrator](https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/).

Il y en a certains ici comme les conteneurs et Kubernetes que nous n'avons pas encore couverts en détail, donc je ne veux pas encore sauter dedans.

Dans les publications précédentes, nous avons créé la plupart des modules 1, 2 et 3.

### Réseautage Virtuel

En suivant le [Module 04](https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/Instructions/Labs/LAB_04-Implement_Virtual_Networking.html) :

J'ai parcouru ce qui précède et modifié quelques noms pour #90DaysOfDevOps. Au lieu d'utiliser le Cloud Shell, j'ai continué et me suis connecté avec mon nouvel utilisateur créé les jours précédents avec l'Azure CLI sur ma machine Windows.

Vous pouvez le faire en utilisant `az login` qui ouvrira un navigateur et vous permettra de vous authentifier sur votre compte.

J'ai ensuite créé un script PowerShell et quelques références à partir du module pour construire certaines des tâches ci-dessous. Vous pouvez trouver les fichiers associés dans ce dossier.
(Cloud/01VirtualNetworking)

Assurez-vous de modifier l'emplacement du fichier dans le script pour qu'il corresponde à votre environnement.

À ce premier stade, nous n'avons aucun réseau virtuel ou machines virtuelles créés dans notre environnement ; j'ai uniquement configuré un emplacement de stockage cloud shell dans mon groupe de ressources.

Je commence par exécuter mon [script PowerShell](Cloud/01VirtualNetworking/Module4_90DaysOfDevOps.ps1).

![](Images/Day34_Cloud1.png)

- Tâche 1 : Créer et configurer un réseau virtuel

![](Images/Day34_Cloud2.png)

- Tâche 2 : Déployer des machines virtuelles dans le réseau virtuel

![](Images/Day34_Cloud3.png)

- Tâche 3 : Configurer les adresses IP privées et publiques des machines virtuelles Azure

![](Images/Day34_Cloud4.png)

- Tâche 4 : Configurer les groupes de sécurité réseau

![](Images/Day34_Cloud5.png)
![](Images/Day34_Cloud6.png)

- Tâche 5 : Configurer Azure DNS pour la résolution de noms internes

![](Images/Day34_Cloud7.png)
![](Images/Day34_Cloud8.png)

### Gestion du Trafic Réseau

En suivant le [Module 06](https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/Instructions/Labs/LAB_06-Implement_Network_Traffic_Management.html) :

Ensuite, nous allons dans notre groupe de ressources et supprimons nos ressources. Si vous n'avez pas configuré le compte utilisateur comme moi pour n'avoir accès qu'à ce groupe de ressources, vous pouvez suivre le module en changeant le nom en `90Days*`, ce qui supprimera toutes les ressources et le groupe de ressources. Ce sera mon processus pour chacun des laboratoires suivants.

Pour ce laboratoire, j'ai également créé un script PowerShell et quelques références à partir du module pour construire certaines des tâches ci-dessous. Vous pouvez trouver les fichiers associés dans ce dossier.
(Cloud/02TrafficManagement)

- Tâche 1 : Fourniture de l'environnement de laboratoire

Je commence par exécuter mon [script PowerShell](Cloud/02TrafficManagement/Mod06_90DaysOfDevOps.ps1).

![](Images/Day34_Cloud9.png)

- Tâche 2 : Configurer la topologie du réseau hub et spoke

![](Images/Day34_Cloud10.png)

- Tâche 3 : Tester la transitivité du peering de réseau virtuel

Pour cela, mon groupe 90DaysOfDevOps n'avait pas accès au Network Watcher en raison des autorisations. Je pense que c'est parce que les Network Watchers sont l'une de ces ressources qui ne sont pas liées à un groupe de ressources, ce qui est l'endroit où notre RBAC a été couvert pour cet utilisateur. J'ai ajouté le rôle de contributeur East US Network Watcher au groupe 90DaysOfDevOps.

![](Images/Day34_Cloud11.png)
![](Images/Day34_Cloud12.png)
![](Images/Day34_Cloud13.png)

^ Cela est attendu puisque les deux réseaux virtuels spoke ne se connectent pas l'un à l'autre (le peering de réseau virtuel n'est pas transitif).

- Tâche 4 : Configurer le routage dans la topologie hub et spoke

J'ai eu un autre problème ici avec mon compte qui ne pouvait pas exécuter le script en tant qu'utilisateur au sein du groupe 90DaysOfDevOps, ce dont je ne suis pas sûr, donc j'ai sauté dans mon compte admin principal. Le groupe 90DaysOfDevOps est propriétaire de tout dans le groupe de ressources 90DaysOfDevOps, donc j'aimerais comprendre pourquoi je ne peux pas exécuter une commande à l'intérieur de la machine virtuelle ?

![](Images/Day34_Cloud14.png)
![](Images/Day34_Cloud15.png)

Ensuite, j'ai pu retourner dans mon compte michael.cade@90DaysOfDevOps.com et continuer cette section. Ici, nous exécutons le même test, mais maintenant avec le résultat accessible.

![](Images/Day34_Cloud16.png)

- Tâche 5 : Mettre en œuvre Azure Load Balancer

![](Images/Day34_Cloud17.png)
![](Images/Day34_Cloud18.png)

- Tâche 6 : Mettre en œuvre Azure Application Gateway

![](Images/Day34_Cloud19.png)
![](Images/Day34_Cloud20.png)

### Stockage Azure

En suivant le [Module 07](https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/Instructions/Labs/LAB_07-Manage_Azure_Storage.html) :

Pour ce laboratoire, j'ai également créé un script PowerShell et quelques références à partir du module pour construire certaines des tâches ci-dessous. Vous pouvez trouver les fichiers associés dans ce dossier.
(Cloud/03Storage)

- Tâche 1 : Fourniture de l'environnement de laboratoire

Je commence par exécuter mon [script PowerShell](Cloud/03Storage/Mod07_90DaysOfDevOps.ps1).

![](Images/Day34_Cloud21.png)

- Tâche 2 : Créer et configurer des comptes de stockage Azure

![](Images/Day34_Cloud22.png)

- Tâche 3 : Gérer le stockage blob

![](Images/Day34_Cloud23.png)

- Tâche 4 : Gérer l'authentification et l'autorisation pour le stockage Azure

![](Images/Day34_Cloud24.png)
![](Images/Day34_Cloud25.png)

J'étais un peu impatient d'attendre que cela soit autorisé, mais cela a fini par fonctionner.

![](Images/Day34_Cloud26.png)

- Tâche 5 : Créer et configurer des partages de fichiers Azure

Sur la commande d'exécution, cela ne fonctionnerait pas avec michael.cade@90DaysOfDevOps.com, donc j'ai utilisé mon compte élevé.

![](Images/Day34_Cloud27.png)
![](Images/Day34_Cloud28.png)
![](Images/Day34_Cloud29.png)

- Tâche 6 : Gérer l'accès réseau pour le stockage Azure

![](Images/Day34_Cloud30.png)

### Serverless (Mettre en œuvre des applications web)

En suivant le [Module 09a](https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/Instructions/Labs/LAB_09a-Implement_Web_Apps.html) :

- Tâche 1 : Créer une application web Azure

![](Images/Day34_Cloud31.png)

- Tâche 2 : Créer un emplacement de déploiement de préparation

![](Images/Day34_Cloud34.png)

- Tâche 3 : Configurer les paramètres de déploiement de l'application web

![](Images/Day34_Cloud33.png)

- Tâche 4 : Déployer du code vers l'emplacement de déploiement de préparation

![](Images/Day34_Cloud32.png)

- Tâche 5 : Échanger les emplacements de préparation

![](Images/Day34_Cloud35.png)

- Tâche 6 : Configurer et tester l'auto-scaling de l'application web Azure

Ce script que j'utilise peut être trouvé dans (Cloud/04Serverless)

![](Images/Day34_Cloud36.png)

Cela conclut la section sur Microsoft Azure et le cloud public en général. Je dirais que j'ai eu beaucoup de plaisir à travailler à travers ces scénarios.

## Ressources

- [Hybrid Cloud and MultiCloud](https://www.youtube.com/watch?v=qkj5W98Xdvw)
- [Microsoft Azure Fundamentals](https://www.youtube.com/watch?v=NKEFWyqJ5XA&list=WL&index=130&t=12s)
- [Google Cloud Digital Leader Certification Course](https://www.youtube.com/watch?v=UGRDM86MBIQ&list=WL&index=131&t=10s)
- [AWS Basics for Beginners - Full Course](https://www.youtube.com/watch?v=ulprqHHWlng&t=5352s)

Ensuite, nous allons plonger dans les systèmes de contrôle de version, spécifiquement autour de git, puis également dans les aperçus des dépôts de code, et nous choisirons GitHub comme option préférée.

À demain pour le [Jour 35](day35.md)