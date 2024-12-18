## Modèles de Sécurité de Microsoft Azure

Suite à la vue d'ensemble de Microsoft Azure, nous allons commencer par la sécurité Azure et voir comment cela peut nous aider au quotidien. Pour la plupart, j'ai trouvé que les rôles intégrés ont été suffisants, mais savoir que nous pouvons créer et travailler avec de nombreuses zones différentes d'authentification et de configurations. J'ai trouvé que Microsoft Azure est assez avancé avec son arrière-plan Active Directory par rapport aux autres clouds publics.

C'est un domaine dans lequel Microsoft Azure semble fonctionner différemment des autres fournisseurs de cloud public ; dans Azure, il y a TOUJOURS Azure AD.

### Services de Répertoire

- Azure Active Directory héberge les principes de sécurité utilisés par Microsoft Azure et d'autres services cloud Microsoft.
- L'authentification est accomplie via des protocoles tels que SAML, WS-Federation, OpenID Connect et OAuth2.
- Les requêtes sont accomplies via l'API REST appelée Microsoft Graph API.
- Les locataires ont un nom par défaut tenant.onmicrosoft.com mais peuvent également avoir des noms de domaine personnalisés.
- Les abonnements sont associés à un locataire Azure Active Directory.

Si nous pensons à AWS pour comparer, l'offre équivalente serait AWS IAM (Identity & Access Management). Bien que toujours très différent.

Azure AD Connect fournit la capacité de répliquer des comptes d'AD à Azure AD. Cela peut également inclure des groupes et parfois des objets. Cela peut être granulaire et filtré. Prend en charge plusieurs forêts et domaines.

Il est possible de créer des comptes cloud dans Microsoft Azure Active Directory (AD), mais la plupart des organisations ont déjà des comptes pour leurs utilisateurs dans leur propre Active Directory étant sur site.

Azure AD Connect permet également de voir non seulement les serveurs Windows AD, mais aussi d'autres Azure AD, Google et autres. Cela permet également de collaborer avec des personnes et des organisations externes ; cela s'appelle Azure B2B.

Les options d'authentification entre Active Directory Domain Services et Microsoft Azure Active Directory sont possibles avec la synchronisation d'identité avec un hachage de mot de passe.

![](Images/Day30_Cloud1.png)

Le passage du hachage de mot de passe est facultatif ; si cela n'est pas utilisé, une authentification directe est requise.

Il y a une vidéo liée ci-dessous qui entre dans les détails sur l'authentification directe.

[Connexion des utilisateurs avec l'authentification directe Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-pta)

![](Images/Day30_Cloud2.png)

### Fédération

Il est juste de dire que si vous utilisez Microsoft 365, Microsoft Dynamics et Active Directory sur site, il est assez facile de comprendre et de s'intégrer à Azure AD pour la fédération. Cependant, vous pourriez utiliser d'autres services en dehors de l'écosystème Microsoft.

Azure AD peut agir comme un courtier de fédération pour ces autres applications Non-Microsoft et d'autres services de répertoire.

Cela sera vu dans le portail Azure en tant qu'applications d'entreprise, dont il existe un grand nombre d'options.

![](Images/Day30_Cloud3.png)

Si vous faites défiler vers le bas sur la page des applications d'entreprise, vous allez voir une longue liste d'applications présentées.

![](Images/Day30_Cloud4.png)

Cette option permet également l'intégration "apportez la vôtre", une application que vous développez ou une application non-galerie.

Je n'ai pas regardé cela auparavant, mais je peux voir que c'est un ensemble de fonctionnalités assez important par rapport aux autres fournisseurs de cloud et capacités.

### Contrôle d'Accès Basé sur les Rôles

Nous avons déjà couvert le [Jour 29](day29.md) les étendues que nous allons couvrir ici ; nous pouvons définir notre contrôle d'accès basé sur les rôles selon l'une de ces zones.

- Abonnements
- Groupe de Gestion
- Groupe de Ressources
- Ressources

Les rôles peuvent être divisés en trois ; il y a de nombreux rôles intégrés dans Microsoft Azure. Ces trois sont :

- Propriétaire
- Contributeur
- Lecteur

Le propriétaire et le contributeur sont très similaires dans leurs limites de portée ; cependant, le propriétaire peut changer les autorisations.

D'autres rôles sont spécifiques à certains types de ressources Azure ainsi que des rôles personnalisés.

Nous devrions nous concentrer sur l'attribution d'autorisations aux groupes plutôt qu'aux utilisateurs.

Les autorisations sont héritées.

Si nous revenons en arrière et regardons le groupe de ressources "90DaysOfDevOps" que nous avons créé et vérifions le contrôle d'accès (IAM) à l'intérieur, vous pouvez voir que nous avons une liste de contributeurs et un administrateur d'accès utilisateur client, et nous avons une liste de propriétaires (mais je ne peux pas montrer cela).

![](Images/Day30_Cloud5.png)

Nous pouvons également vérifier les rôles que nous avons attribués ici s'ils sont BuiltInRoles et sous quelle catégorie ils tombent.

![](Images/Day30_Cloud6.png)

Nous pouvons également utiliser l'onglet vérifier l'accès si nous voulons vérifier un compte par rapport à ce groupe de ressources et nous assurer que le compte auquel nous souhaitons avoir cet accès dispose des autorisations correctes, ou peut-être voulons-nous vérifier si un utilisateur a trop d'accès.

![](Images/Day30_Cloud7.png)

### Microsoft Defender pour le Cloud

- Microsoft Defender pour le Cloud (anciennement connu sous le nom de Azure Security Center) fournit des informations sur la sécurité de l'ensemble de l'environnement Azure.
- Un tableau de bord unique pour la visibilité sur la santé globale de la sécurité de toutes les ressources Azure et non-Azure (via Azure Arc) et des conseils de renforcement de la sécurité.
- Le niveau gratuit inclut une évaluation continue et des recommandations de sécurité.
- Plans payants pour les types de ressources protégées (par exemple, Servers, AppService, SQL, Storage, Containers, KeyVault).

J'ai basculé vers un autre abonnement pour voir le Centre de Sécurité Azure et vous pouvez voir ici, en fonction de très peu de ressources, que j'ai quelques recommandations en un seul endroit.

![](Images/Day30_Cloud8.png)

### Azure Policy

- Azure Policy est un service natif Azure qui aide à faire respecter les normes organisationnelles et à évaluer la conformité à grande échelle.
- Intégré dans Microsoft Defender pour le Cloud. Azure Policy audite les ressources non conformes et applique des mesures correctives.
- Communément utilisé pour gouverner la cohérence des ressources, la conformité réglementaire, la sécurité, le coût et les normes de gestion.
- Utilise le format JSON pour stocker la logique d'évaluation et déterminer si une ressource est conforme ou non, et toute action à entreprendre en cas de non-conformité (par exemple, Audit, AuditIfNotExists, Deny, Modify, DeployIfNotExists).
- Gratuit à utiliser. L'exception est les ressources connectées Azure Arc facturées par serveur/mois pour l'utilisation de la configuration invitée Azure Policy.

### Mise en Pratique

J'ai acheté www.90DaysOfDevOps.com et j'aimerais ajouter ce domaine à mon portail Azure Active Directory, [Ajouter votre nom de domaine personnalisé à l'aide du portail Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/add-custom-domain).

![](Images/Day30_Cloud9.png)

Avec cela maintenant, nous pouvons créer un nouvel utilisateur sur notre nouveau domaine Active Directory.

![](Images/Day30_Cloud10.png)

Maintenant, nous voulons créer un groupe pour tous nos nouveaux utilisateurs 90DaysOfDevOps dans un seul groupe. Nous pouvons créer un groupe comme ci-dessous, notez que j'utilise "Dynamic User" ce qui signifie qu'Azure AD interrogera les comptes utilisateurs et les ajoutera dynamiquement par rapport à assigné où vous ajoutez manuellement l'utilisateur à votre groupe.

![](Images/Day30_Cloud11.png)

Il y a beaucoup d'options lorsqu'il s'agit de créer votre requête ; je prévois de simplement trouver le nom principal et de m'assurer que le nom contient @90DaysOfDevOps.com.

![](Images/Day30_Cloud12.png)

Maintenant, parce que nous avons créé notre compte utilisateur pour michael.cade@90DaysOfDevOps.com, nous pouvons valider que les règles fonctionnent. Pour comparaison, j'ai également ajouté un autre compte que j'ai associé à un autre domaine ici et vous pouvez voir qu'en raison de cette règle, notre utilisateur ne sera pas dans ce groupe.

![](Images/Day30_Cloud13.png)

J'ai depuis ajouté un nouvel utilisateur1@90DaysOfDevOps.com et si nous allons vérifier le groupe, nous pouvons voir nos membres.

![](Images/Day30_Cloud14.png)

Si nous avons cette exigence x100, nous ne voudrons pas faire tout cela dans la console ; nous voudrons tirer parti des options en bloc pour créer, inviter et supprimer des utilisateurs, ou vous voudrez peut-être regarder PowerShell pour atteindre cette approche automatisée pour évoluer.

Maintenant, nous pouvons aller dans notre groupe de ressources et spécifier que sur le groupe de ressources 90DaysOfDevOps, nous voulons que le propriétaire soit le groupe que nous venons de créer.

![](Images/Day30_Cloud15.png)

Nous pouvons également aller ici et refuser l'accès aux attributions de notre groupe de ressources.

Maintenant, si nous nous connectons au portail Azure avec notre nouveau compte utilisateur, vous pouvez voir que nous n'avons accès qu'à notre groupe de ressources 90DaysOfDevOps et non aux autres vus dans les images précédentes car nous n'avons pas l'accès.

![](Images/Day30_Cloud16.png)

Ce qui précède est génial si cet utilisateur a accès aux ressources à l'intérieur de votre portail Azure ; tous les utilisateurs n'ont pas besoin d'être conscients du portail, mais pour vérifier l'accès, nous pouvons utiliser le [Portail Apps](https://myapps.microsoft.com/). C'est un portail d'authentification unique pour nous tester.

![](Images/Day30_Cloud17.png)

Vous pouvez personnaliser ce portail avec votre image de marque et cela pourrait être quelque chose que nous reviendrons plus tard.

## Ressources

- [Hybrid Cloud and MultiCloud](https://www.youtube.com/watch?v=qkj5W98Xdvw)
- [Microsoft Azure Fundamentals](https://www.youtube.com/watch?v=NKEFWyqJ5XA&list=WL&index=130&t=12s)
- [Google Cloud Digital Leader Certification Course](https://www.youtube.com/watch?v=UGRDM86MBIQ&list=WL&index=131&t=10s)

À demain pour le [Jour 31](day31.md)