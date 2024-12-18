## Fondamentaux de Microsoft Azure

Avant de commencer, le gagnant du sondage Twitter était Microsoft Azure, d'où le titre de la page. C'était serré et intéressant de voir les résultats arriver au cours des 24 heures.

![](Images/Day29_Cloud1.png)

Je dirais que couvrir ce sujet me donnera une meilleure compréhension et une mise à jour des services disponibles sur Microsoft Azure. Je penche vers Amazon AWS dans ma vie quotidienne. Cependant, j'ai laissé des ressources que j'avais préparées pour les trois principaux fournisseurs de cloud.

J'apprécie qu'il y en ait plus et que le sondage n'incluait que ces 3, et en particulier, il y avait des commentaires sur Oracle Cloud. J'aimerais en savoir plus sur d'autres fournisseurs de cloud utilisés dans le monde réel.

### Les Bases

- Fournit des services de cloud public
- Géographiquement distribué (60+ régions dans le monde)
- Accessible via Internet et/ou des connexions privées
- Modèle multi-locataire
- Facturation basée sur la consommation - (Payer à l'utilisation | Payer à la croissance)
- Un grand nombre de types de services et d'offres pour différentes exigences.

- [Infrastructure Globale Microsoft Azure](https://infrastructuremap.microsoft.com/explore)

Bien que nous ayons parlé de SaaS et de cloud hybride, nous ne prévoyons pas de couvrir ces sujets ici.

La meilleure façon de commencer et de suivre est de cliquer sur le lien, qui vous permettra de créer un [Compte Microsoft Azure Gratuit](https://azure.microsoft.com/en-gb/free/).

### Régions

J'ai lié la carte interactive ci-dessus, mais nous pouvons voir l'image ci-dessous montrant l'étendue des régions proposées sur la plateforme Microsoft Azure dans le monde.

![](Images/Day29_Cloud2.png)
_image prise de [Microsoft Docs - 01/05/2021](https://docs.microsoft.com/en-us/azure/networking/microsoft-global-network)_

Vous verrez également plusieurs clouds "souverains", ce qui signifie qu'ils ne sont pas liés ou capables de communiquer avec les autres régions. Par exemple, ceux-ci seraient associés à des gouvernements comme `AzureUSGovernment` ainsi que `AzureChinaCloud` et d'autres.

Lorsque nous déployons nos services dans Microsoft Azure, nous choisirons une région pour presque tout. Cependant, il est important de noter que tous les services ne sont pas disponibles dans toutes les régions. Vous pouvez voir les [Produits disponibles par région](https://azure.microsoft.com/en-us/global-infrastructure/services/?products=all) au moment où j'écris ceci, dans le centre-ouest des États-Unis, nous ne pouvons pas utiliser Azure Databricks.

J'ai également mentionné "presque tout" ci-dessus ; il existe certains services liés à la région, tels que Azure Bot Services, Bing Speech, Azure Virtual Desktop, Static Web Apps, et d'autres.

En coulisses, une région peut être composée de plus d'un centre de données. Ceux-ci seront appelés Zones de Disponibilité.

Dans l'image ci-dessous, vous verrez, et encore une fois, ceci est tiré de la documentation officielle de Microsoft, elle décrit ce qu'est une région et comment elle est composée de Zones de Disponibilité. Cependant, toutes les régions n'ont pas plusieurs Zones de Disponibilité.

![](Images/Day29_Cloud3.png)

La documentation de Microsoft est très bonne, et vous pouvez en lire plus sur les [Régions et Zones de Disponibilité](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview) ici.

### Abonnements

Souvenez-vous, nous avons mentionné que Microsoft Azure est un modèle de cloud basé sur la consommation ; vous constaterez que tous les principaux fournisseurs de cloud suivent ce modèle.

Si vous êtes une entreprise, vous voudrez peut-être ou aurez un Contrat Entreprise établi avec Microsoft pour permettre à votre entreprise de consommer ces services Azure.

Si vous êtes comme moi et que vous utilisez Microsoft Azure à des fins éducatives, nous avons quelques autres options.

Nous avons le [Compte Microsoft Azure Gratuit](https://azure.microsoft.com/en-gb/free/) qui, en général, vous donne plusieurs crédits cloud gratuits à dépenser dans Azure sur une certaine période.

Il y a aussi la possibilité d'utiliser un abonnement Visual Studio qui vous donne peut-être quelques crédits gratuits chaque mois en plus de votre abonnement annuel à Visual Studio, ceci était communément connu sous le nom de MSDN il y a quelques années. [Visual Studio](https://azure.microsoft.com/en-us/pricing/member-offers/credit-for-visual-studio-subscribers/)

Enfin, il y a l'option de remettre une carte de crédit et d'avoir un modèle de paiement à l'utilisation. [Paiement à l'utilisation](https://azure.microsoft.com/en-us/pricing/purchase-options/pay-as-you-go/)

Un abonnement peut être vu comme une limite entre différents abonnements, potentiellement des centres de coûts, mais des environnements complètement différents. Un abonnement est l'endroit où les ressources sont créées.

### Groupes de Gestion

Les groupes de gestion nous donnent la possibilité de séparer le contrôle dans notre Azure Active Directory (AD) ou notre environnement de locataire. Les groupes de gestion nous permettent de contrôler les politiques, le Contrôle d'Accès Basé sur les Rôles (RBAC) et les budgets.

Les abonnements appartiennent à ces groupes de gestion, vous pouvez donc avoir plusieurs abonnements dans votre locataire Azure AD. Ces abonnements peuvent également contrôler les politiques, le RBAC et les budgets.

### Gestionnaire de Ressources et Groupes de Ressources

#### Azure Resource Manager

- API basée sur JSON construite sur des fournisseurs de ressources.
- Les ressources appartiennent à un groupe de ressources et partagent un cycle de vie commun.
- Parallélisme
- Les déploiements basés sur JSON sont déclaratifs, idempotents et comprennent les dépendances entre les ressources pour gouverner la création et l'ordre.

#### Groupes de Ressources

- Chaque ressource Azure Resource Manager existe dans un et un seul groupe de ressources !
- Les groupes de ressources sont créés dans une région qui peut contenir des ressources en dehors de la région.
- Les ressources peuvent être déplacées entre les groupes de ressources.
- Les groupes de ressources ne sont pas cloisonnés par rapport aux autres groupes de ressources ; il peut y avoir une communication entre les groupes de ressources.
- Les groupes de ressources peuvent également contrôler les politiques, le RBAC et les budgets.

### Mise en Pratique

Allons nous connecter et assurons-nous d'avoir un **Abonnement** disponible pour nous. Nous pouvons vérifier notre **Groupe de Gestion** simple prêt à l'emploi, puis nous pouvons créer un nouveau **Groupe de Ressources** dédié dans notre **Région** préférée.

Lorsque nous nous connectons pour la première fois à notre [portail Azure](https://portal.azure.com/#home), vous verrez en haut la possibilité de rechercher des ressources, des services et des documents.

![](Images/Day29_Cloud4.png)

Nous allons d'abord regarder notre abonnement ; vous verrez ici que j'utilise un abonnement Visual Studio Professional qui me donne quelques crédits gratuits chaque mois.

![](Images/Day29_Cloud5.png)

Si nous y allons, vous obtiendrez une vue plus large et un aperçu de ce qui se passe ou de ce qui peut être fait avec l'abonnement. Nous pouvons voir les informations de facturation avec des fonctions de contrôle à gauche où vous pouvez définir le contrôle d'accès IAM, et plus bas, il y a plus de ressources disponibles.

![](Images/Day29_Cloud6.png)

Il pourrait y avoir un scénario où vous avez plusieurs abonnements et vous souhaitez les gérer tous sous un seul groupe de gestion ; c'est là que les groupes de gestion peuvent être utilisés pour séparer les groupes de responsabilité. Dans le mien ci-dessous, vous pouvez voir qu'il y a juste mon groupe racine de locataire avec mon abonnement.

Vous verrez également dans l'image précédente que l'identifiant du groupe de gestion parent est le même que celui utilisé sur le groupe racine du locataire.

![](Images/Day29_Cloud7.png)

Ensuite, nous avons des groupes de ressources ; c'est là que nous combinons nos ressources et que nous pouvons facilement les gérer en un seul endroit. J'en ai créé quelques-uns pour divers autres projets.

![](Images/Day29_Cloud8.png)

Avec ce que nous allons faire au cours des prochains jours, nous voulons créer notre groupe de ressources. Cela se fait facilement dans cette console en cliquant sur l'option de création dans l'image précédente.

![](Images/Day29_Cloud9.png)

Une étape de validation a lieu, puis vous avez la possibilité de réviser votre création, puis de créer. Vous verrez également en bas "Télécharger un modèle pour l'automatisation" ; cela nous permet de récupérer le format JSON afin que nous puissions effectuer cela de manière automatisée plus tard si nous le souhaitons. Nous couvrirons également cela plus tard.

![](Images/Day29_Cloud10.png)

Cliquez sur créer, puis dans notre liste de groupes de ressources, nous avons maintenant notre groupe "90DaysOfDevOps" prêt pour ce que nous ferons dans la prochaine session.

![](Images/Day29_Cloud11.png)

## Ressources

- [Hybrid Cloud and MultiCloud](https://www.youtube.com/watch?v=qkj5W98Xdvw)
- [Microsoft Azure Fundamentals](https://www.youtube.com/watch?v=NKEFWyqJ5XA&list=WL&index=130&t=12s)
- [Google Cloud Digital Leader Certification Course](https://www.youtube.com/watch?v=UGRDM86MBIQ&list=WL&index=131&t=10s)
- [AWS Basics for Beginners - Full Course](https://www.youtube.com/watch?v=ulprqHHWlng&t=5352s)

À demain pour le [Jour 30](day30.md)