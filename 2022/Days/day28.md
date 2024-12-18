## Vue d'Ensemble : DevOps et le Cloud

Lorsqu'il s'agit de l'informatique en cloud et de ce qui est offert, cela s'accorde très bien avec l'éthique et les processus DevOps. Nous pouvons considérer l'informatique en cloud comme apportant la technologie et les services, tandis que le DevOps, comme nous l'avons mentionné à plusieurs reprises, concerne le processus et l'amélioration des processus.

Cependant, commencer ce voyage d'apprentissage du cloud est une tâche ardue, et s'assurer que vous connaissez et comprenez tous les éléments ou le meilleur service à choisir pour le bon prix est déroutant.

![](Images/Day28_Cloud1.png)

Le cloud public nécessite-t-il un état d'esprit DevOps ? Ma réponse ici est non, mais pour vraiment tirer parti de l'informatique en nuage et éviter ces grosses factures de cloud que tant de personnes ont rencontrées, il est important de penser à l'informatique en nuage et à DevOps ensemble.

Si nous regardons ce que nous entendons par le cloud public à un niveau élevé, il s'agit de déléguer certaines responsabilités à un service géré pour vous permettre, à vous et à votre équipe, de vous concentrer sur des aspects plus importants, qui devraient être l'application et les utilisateurs finaux. Après tout, le cloud public n'est que l'ordinateur de quelqu'un d'autre.

![](Images/Day28_Cloud2.png)

Dans cette première section, je veux entrer dans les détails et décrire un peu plus ce qu'est un cloud public et certains des blocs de construction qui sont désignés comme le cloud public dans son ensemble.

### SaaS

La première zone à couvrir est le logiciel en tant que service (SaaS). Ce service élimine presque toute la charge administrative d'un service que vous auriez pu exécuter sur site. Prenons l'exemple de Microsoft Exchange pour nos emails. Cela était auparavant une boîte physique qui vivait dans votre centre de données ou peut-être dans le placard sous l'escalier. Vous deviez nourrir et abreuver ce serveur. Par cela, je veux dire que vous deviez le maintenir à jour et que vous étiez responsable de l'achat du matériel serveur, très probablement de l'installation du système d'exploitation, de l'installation des applications requises, puis de leur mise à jour. Si quelque chose tournait mal, vous deviez dépanner et remettre les choses en marche.

Oh, et vous deviez également vous assurer de sauvegarder vos données, bien que cela ne change pas non plus avec le SaaS pour la plupart.

Ce que fait le SaaS, et en particulier Microsoft 365, puisque j'ai mentionné Exchange, c'est éliminer cette charge administrative, et ils fournissent un service qui livre votre fonctionnalité Exchange par le biais du courrier électronique, mais aussi de nombreuses autres options de productivité (Office 365) et de stockage (OneDrive) qui, dans l'ensemble, offrent une excellente expérience à l'utilisateur final.

D'autres applications SaaS sont largement adoptées, telles que Salesforce, SAP, Oracle, Google et Apple. Toutes éliminent le fardeau de la gestion de plus de la pile.

Je suis sûr qu'il y a une histoire avec DevOps et les applications basées sur le SaaS, mais j'ai du mal à trouver ce qu'elles pourraient être. Je sais qu'Azure DevOps a d'excellentes intégrations avec Microsoft 365 que je pourrais examiner et signaler.

![](Images/Day28_Cloud3.png)

### Cloud Public

Ensuite, nous avons le cloud public. La plupart des gens le verraient de différentes manières. Certains le verraient uniquement comme les hyper-scaleurs tels que Microsoft Azure, Google Cloud Platform et AWS.

![](Images/Day28_Cloud4.png)

D'autres verront également le cloud public comme une offre beaucoup plus large qui inclut ces hyper-scaleurs ainsi que les milliers de MSP (Managed Service Providers) du monde entier. Pour ce post, nous allons considérer le cloud public comme incluant les hyper-scaleurs et les MSP, bien que plus tard, nous plongerons spécifiquement dans un ou plusieurs des hyper-scaleurs pour obtenir cette connaissance fondamentale.

![](Images/Day28_Cloud5.png)
_Des milliers d'autres entreprises pourraient figurer ici ; je ne fais que choisir parmi les marques locales, régionales, de télécommunications et mondiales avec lesquelles j'ai travaillé et dont j'ai connaissance._

Nous avons mentionné dans la section SaaS que le cloud élimine la responsabilité ou le fardeau de l'administration de certaines parties d'un système. Si avec le SaaS nous voyons beaucoup des couches d'abstraction supprimées, c'est-à-dire les systèmes physiques, le réseau, le stockage, le système d'exploitation et même l'application dans une certaine mesure. Lorsqu'il s'agit du cloud, il existe divers niveaux d'abstraction que nous pouvons supprimer ou conserver en fonction de vos besoins.

Nous avons déjà mentionné le SaaS, mais il y en a au moins deux autres à mentionner concernant le cloud public.

Infrastructure en tant que service (IaaS) : Vous pouvez considérer cette couche comme une machine virtuelle, mais alors que sur site vous devriez vous occuper de la couche physique, dans le cloud ce n'est pas le cas. Le physique est de la responsabilité du fournisseur de cloud, et vous gérerez et administrerez le système d'exploitation, les données et les applications que vous souhaitez exécuter.

Plateforme en tant que service (PaaS) : Cela continue à éliminer la responsabilité des couches, et il s'agit vraiment de vous permettre de contrôler les données et l'application sans avoir à vous soucier du matériel sous-jacent ou du système d'exploitation.

Il existe de nombreuses autres offres aaS, mais ce sont les deux fondamentales. Vous pourriez voir des offres autour de StaaS (Storage as a Service) qui vous fournissent votre couche de stockage sans avoir à vous soucier du matériel sous-jacent. Ou vous pourriez avoir entendu parler de CaaS pour Containers as a Service, que nous aborderons plus tard. Une autre offre aaS que nous chercherons à couvrir au cours des 7 prochains jours est FaaS (Functions as a Service), où peut-être vous n'avez pas besoin d'un système en cours d'exécution tout le temps et vous voulez simplement qu'une fonction soit exécutée à la demande.

Il existe de nombreuses façons dont le cloud public peut fournir des couches d'abstraction de contrôle que vous souhaitez transmettre et payer.

![](Images/Day28_Cloud6.png)

### Cloud Privé

Avoir son propre centre de données n'est pas une chose du passé. Je pense que cela est devenu une résurgence parmi de nombreuses entreprises qui ont trouvé le modèle OPEX difficile à gérer ainsi que les compétences nécessaires pour utiliser uniquement le cloud public.

Il est important de noter ici que le cloud public est désormais probablement de votre responsabilité et qu'il sera sur vos locaux.

Nous avons des choses intéressantes qui se passent dans cet espace, non seulement avec VMware qui a dominé l'ère de la virtualisation et les environements d'infrastructure sur site. Nous avons également les hyper-scaleurs offrant une version sur site de leurs clouds publics.

![](Images/Day28_Cloud7.png)

### Cloud Hybride

Pour suivre les mentions de cloud public et privé, nous pouvons également couvrir ces deux environnements pour offrir de la flexibilité entre eux, peut-être tirer parti des services disponibles dans le cloud public, puis également tirer parti des fonctionnalités et des fonctionnalités d'être sur site ou cela pourrait être une réglementation qui dicte que vous devez stocker des données localement.

![](Images/Day28_Cloud8.png)

En mettant tout cela ensemble, nous avons beaucoup de choix pour l'endroit où nous stockons et exécutons nos charges de travail.

![](Images/Day28_Cloud9.png)

Avant de nous plonger dans un hyper-scaleur spécifique, j'ai demandé à Twitter où nous devrions aller.

![](Images/Day28_Cloud10.png)

[Lien vers le sondage Twitter](https://twitter.com/MichaelCade1/status/1486814904510259208?s=20&t=x2n6QhyOXSUs7Pq0itdIIQ)

Quel que soit celui qui obtient le pourcentage le plus élevé, nous plongerons plus profondément dans les offres. Je pense qu'il est important de mentionner que les services de tous ces fournisseurs sont assez similaires, c'est pourquoi je dis de commencer avec l'un d'eux, car j'ai constaté qu'en connaissant les bases de l'un d'eux et en sachant comment créer des machines virtuelles, configurer le réseau, etc., j'ai pu passer rapidement aux autres domaines.

Quoi qu'il en soit, je vais partager quelques ressources **GRATUITES** qui couvrent les trois hyper-scaleurs.

Je vais également élaborer un scénario comme je l'ai fait dans les autres sections où nous pouvons construire quelque chose au fur et à mesure que nous avançons dans les jours.

## Ressources

- [Hybrid Cloud and MultiCloud](https://www.youtube.com/watch?v=qkj5W98Xdvw)
- [Microsoft Azure Fundamentals](https://www.youtube.com/watch?v=NKEFWyqJ5XA&list=WL&index=130&t=12s)
- [Google Cloud Digital Leader Certification Course](https://www.youtube.com/watch?v=UGRDM86MBIQ&list=WL&index=131&t=10s)
- [AWS Basics for Beginners - Full Course](https://youtu.be/k1RI5locZE4?si=0wPB2cdTY5hHgjl5)

À demain pour le [Jour 29](day29.md)