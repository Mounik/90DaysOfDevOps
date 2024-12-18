## Automatisation du Réseau

### Fondamentaux de l'automatisation du réseau

Principaux moteurs de l'automatisation du réseau

- Atteindre l'agilité
- Réduire les coûts
- Éliminer les erreurs
- Assurer la conformité
- Gestion centralisée

Le processus d'adoption de l'automatisation est spécifique à chaque entreprise. Il n'y a pas de solution unique lorsqu'il s'agit de déployer l'automatisation ; la capacité à identifier et à adopter l'approche qui fonctionne le mieux pour votre organisation est cruciale pour avancer vers le maintien ou la création d'un environnement plus agile. L'accent doit toujours être mis sur la valeur commerciale et l'expérience de l'utilisateur final. (Nous avons dit quelque chose de similaire dès le début concernant l'ensemble de DevOps et le changement de culture et le processus automatisé que cela apporte.)

Pour décomposer cela, vous devez identifier comment la tâche ou le processus que vous essayez d'automatiser va atteindre et améliorer l'expérience de l'utilisateur final ou la valeur commerciale tout en suivant une approche systématique étape par étape.

"Si vous ne savez pas où vous allez, n'importe quel chemin vous y mènera."

Ayez un cadre ou une structure de conception que vous essayez d'atteindre, sachez quel est votre objectif final, puis travaillez étape par étape pour atteindre cet objectif en mesurant le succès de l'automatisation à divers stades en fonction des résultats commerciaux.

Construisez des concepts modélisés autour des applications existantes ; il n'est pas nécessaire de concevoir les concepts autour de l'automatisation dans une bulle car ils doivent être appliqués à votre application, votre service et votre infrastructure. Commencez donc à construire les concepts et à les modéliser autour de votre infrastructure existante, de vos applications existantes.

### Approche de l'automatisation du réseau

Nous devons identifier les tâches et effectuer une découverte des demandes de changement de réseau afin d'avoir les problèmes et les problèmes les plus courants à automatiser une solution.

- Faites une liste de toutes les demandes de changement et des flux de travail qui sont actuellement traités manuellement.
- Déterminez les activités les plus courantes, chronophages et sujettes aux erreurs.
- Priorisez les demandes en adoptant une approche axée sur les affaires.
- C'est le cadre pour construire un processus d'automatisation, ce qui doit être automatisé et ce qui ne doit pas l'être.

Nous devons ensuite diviser les tâches et analyser comment différentes fonctions de réseau fonctionnent et interagissent les unes avec les autres.

- L'équipe infrastructure/réseau reçoit des tickets de changement à plusieurs niveaux pour déployer des applications.
- En fonction des services réseau, divisez-les en différentes zones et comprenez comment ils interagissent les uns avec les autres.
  - Optimisation des applications
  - ADC (Application Delivery Controller)
  - Pare-feu
  - DDI (DNS, DHCP, IPAM, etc.)
  - Routage
  - Autres
- Identifiez diverses dépendances pour traiter les différences commerciales et culturelles et apporter une collaboration inter-équipes.

Politiques réutilisables, définir et simplifier les tâches de service, les processus et les entrées/sorties réutilisables.

- Définir les offres pour divers services, processus et entrées/sorties.
- Simplifier le processus de déploiement réduira le délai de mise sur le marché pour les nouvelles charges de travail et les charges de travail existantes.
- Une fois que vous avez un processus standard, il peut être séquencé et aligné sur des demandes individuelles pour une approche multi-thread et une livraison.

Combinez les politiques avec des activités spécifiques à l'entreprise. Comment la mise en œuvre de cette politique aide-t-elle l'entreprise ? Économise du temps ? Économise de l'argent ? Fournit un meilleur résultat commercial ?

- Assurez-vous que les tâches de service sont interopérables.
- Associez les tâches de service incrémentielles de sorte qu'elles s'alignent pour créer des services commerciaux.
- Permettez la flexibilité d'associer et de réassocier les tâches de service à la demande.
- Déployez des capacités en libre-service et ouvrez la voie à une efficacité opérationnelle améliorée.
- Permettez à plusieurs ensembles de compétences technologiques de continuer à contribuer avec supervision et conformité.

**Itérez** sur les politiques et les processus, en ajoutant et en améliorant tout en maintenant la disponibilité et le service.

- Commencez petit en automatisant les tâches existantes.
- Familiarisez-vous avec le processus d'automatisation, afin de pouvoir identifier d'autres domaines qui peuvent bénéficier de l'automatisation.
- Itérez vos initiatives d'automatisation, en ajoutant de l'agilité de manière incrémentielle tout en maintenant la disponibilité requise.
- Adopter une approche incrémentielle ouvre la voie au succès !

Orchestrez le service réseau !

- L'automatisation du processus de déploiement est nécessaire pour fournir rapidement des applications.
- La création d'un environnement de service agile nécessite la gestion de différents éléments à travers les ensembles de compétences technologiques.
- Préparez une orchestration de bout en bout qui permet un contrôle sur l'automatisation et l'ordre des déploiements.

## Outils d'Automatisation du Réseau

La bonne nouvelle ici est que, pour la plupart, les outils que nous utilisons ici pour l'automatisation du réseau sont généralement les mêmes que ceux que nous utiliserons pour d'autres domaines de l'automatisation ou ceux que nous avons déjà couverts ou que nous couvrirons dans les sessions futures.

Système d'exploitation - Comme je l'ai fait tout au long de ce défi, je me concentre sur l'apprentissage principalement avec un OS Linux. Les raisons en ont été données dans la section Linux, mais presque tous les outils que nous allons aborder, bien qu'ils soient multiplateformes, ont commencé comme des applications ou des outils basés sur Linux.

Environnement de développement intégré (IDE) - Encore une fois, il n'y a pas grand-chose à dire ici, sauf que tout au long de ce défi, je suggérerais Visual Studio Code comme votre IDE, en raison des nombreux plugins disponibles pour tant de langages différents.

Gestion de la configuration - Nous n'avons pas encore abordé la section sur la gestion de la configuration, mais il est très clair qu'Ansible est un favori dans ce domaine pour la gestion et l'automatisation des configurations. Ansible est écrit en Python, mais vous n'avez pas besoin de connaître Python.

- Sans agent
- Nécessite uniquement SSH
- Grande communauté de support
- Beaucoup de modules réseau
- Modèle push uniquement
- Configuré avec YAML
- Open Source !

[Lien vers les modules réseau Ansible](https://docs.ansible.com/ansible/2.9/modules/list_of_network_modules.html)

Nous aborderons également **Ansible Tower** dans la section sur la gestion de la configuration ; voyez cela comme l'interface graphique frontale pour Ansible.

CI/CD - Encore une fois, nous aborderons davantage les concepts et les outils autour de cela, mais il est important de le mentionner ici car cela couvre non seulement le réseau mais aussi toute la fourniture de services et de plateformes.

En particulier, Jenkins fournit ou semble être un outil populaire pour l'automatisation du réseau.

- Surveille le dépôt git pour les changements, puis les initie.

Contrôle de version - Encore quelque chose que nous approfondirons plus tard.

- Git fournit un contrôle de version de votre code sur votre appareil local - Multiplateforme
- GitHub, GitLab, BitBucket, etc. sont des sites web en ligne où vous définissez vos dépôts et téléchargez votre code.

Langage | Script - Quelque chose que nous n'avons pas couvert ici est Python en tant que langage. J'ai décidé de plonger dans Go à la place en tant que langage de programmation en fonction de mes circonstances. Je dirais que c'était un choix serré entre Golang et Python, et Python semble être le gagnant pour l'automatisation du réseau.

- Nornir est quelque chose à mentionner ici, un cadre d'automatisation écrit en Python. Cela semble prendre le rôle d'Ansible mais spécifiquement autour de l'automatisation du réseau. [Documentation Nornir](https://nornir.readthedocs.io/en/latest/)

Analyser les API - Postman est un excellent outil pour analyser les API RESTful. Aide à construire, tester et modifier les API.

- POST >>> Pour créer des ressources objets.
- GET >>> Pour récupérer une ressource.
- PUT >>> Pour créer ou remplacer les ressources.
- PATCH >>> Pour créer ou mettre à jour l'objet de ressources.
- Delete >>> Pour supprimer une ressource

[Téléchargement de l'outil Postman](https://www.postman.com/downloads/)

### Autres outils à mentionner

[Cisco NSO (Network Services Orchestrator)](https://www.cisco.com/c/en/us/products/cloud-systems-management/network-services-orchestrator/index.html)

[NetYCE - Simplifier l'automatisation du réseau](https://netyce.com/)

[Automatisation des tests réseau](https://pubhub.devnetcloud.com/media/genie-feature-browser/docs/#/)

Au cours des 3 prochains jours, je prévois de me familiariser davantage avec certaines des choses que nous avons couvertes et de faire un peu de travail autour de Python et de l'automatisation du réseau.

Nous n'avons pas encore couvert tous les sujets de réseau, mais nous voulions rendre cela suffisamment large pour suivre et continuer à apprendre des ressources que j'ajoute ci-dessous.

## Ressources

- [3 compétences nécessaires pour l'automatisation du réseau](https://www.youtube.com/watch?v=KhiJ7Fu9kKA&list=WL&index=122&t=89s)
- [Cours complet de réseautage informatique](https://www.youtube.com/watch?v=IPvYjXCsTg8)
- [Réseautage pratique](http://www.practicalnetworking.net/)
- [Automatisation du réseau Python](https://www.youtube.com/watch?v=xKPzLplPECU&list=WL&index=126)

À demain pour le [Jour 25](day25.md)