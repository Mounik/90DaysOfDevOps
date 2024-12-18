## Python pour l'Automatisation du Réseau

Python est le langage standard utilisé pour les opérations de réseau automatisées.

Bien qu'il ne soit pas uniquement destiné à l'automatisation du réseau, il semble être omniprésent lorsque vous recherchez des ressources. Comme mentionné précédemment, si ce n'est pas Python, c'est généralement Ansible, qui est également écrit en Python.

Je pense avoir déjà mentionné cela, mais pendant la section "Apprendre un langage de programmation", j'ai choisi Golang plutôt que Python pour des raisons liées au fait que mon entreprise développe en Go, ce qui était une bonne raison pour moi d'apprendre. Mais si ce n'était pas le cas, Python aurait pris cette place.

- **Lisibilité et facilité d'utilisation** : Il semble que Python ait du sens. Il n'y a pas de besoin d'utiliser `{}` dans le code pour commencer et terminer des blocs. Couplé à un IDE puissant comme VS Code, vous avez un bon point de départ pour exécuter du code Python.

PyCharm pourrait être un autre IDE à mentionner ici.

- **Bibliothèques** : L'extensibilité de Python est la véritable mine d'or ici. J'ai mentionné précédemment que ce n'est pas seulement pour l'automatisation du réseau, mais il existe de nombreuses bibliothèques pour toutes sortes de dispositifs et de configurations. Vous pouvez voir la grande quantité ici [PyPi](https://pypi.python.org/pypi).

Lorsque vous souhaitez télécharger la bibliothèque sur votre poste de travail, vous utilisez un outil appelé `pip` pour vous connecter à PyPI et la télécharger localement. Des fournisseurs de réseau comme Cisco, Juniper et Arista ont développé des bibliothèques pour faciliter l'accès à leurs dispositifs.

- **Puissant et efficace** : Souvenez-vous, pendant les jours de Go, nous avons parcouru le scénario "Hello World" et nous avons parcouru, je pense, 6 lignes de code ? En Python, c'est :

```python
print('hello world')
```

Mettez tous les points ci-dessus ensemble et il devrait être facile de voir pourquoi Python est généralement mentionné comme l'outil de référence lorsqu'il s'agit d'automatisation.

Il est important de noter qu'il est possible que plusieurs années auparavant, il y avait des scripts qui interagissaient peut-être avec vos dispositifs réseau pour automatiser la sauvegarde de la configuration ou pour collecter des journaux et d'autres informations sur vos dispositifs. L'automatisation dont nous parlons ici est un peu différente, et c'est parce que le paysage global du réseau a également changé pour mieux s'adapter à cette façon de penser et a permis plus d'automatisation.

- **Réseau Défini par Logiciel (SDN)** : Les contrôleurs SDN prennent la responsabilité de fournir la configuration du plan de contrôle à tous les dispositifs du réseau, ce qui signifie un seul point de contact pour tout changement de réseau, sans avoir à se connecter en telnet ou SSH à chaque dispositif et à compter sur les humains pour le faire, ce qui comporte un risque répété d'échec ou de mauvaise configuration.

- **Orchestration de Haut Niveau** : Montez d'un niveau par rapport à ces contrôleurs SDN et cela permet l'orchestration des niveaux de service, puis il y a l'intégration de cette couche d'orchestration dans vos plateformes de choix, VMware, Kubernetes, Clouds Publics, etc.

- **Gestion basée sur les politiques** : Que voulez-vous avoir ? Quel est l'état souhaité ? Vous décrivez cela et le système a tous les détails sur la manière de le réaliser pour atteindre l'état souhaité.

## Configuration de l'environnement de laboratoire

Tout le monde n'a pas accès à des routeurs, commutateurs et autres dispositifs de réseau physiques.

Je voulais rendre possible pour nous d'examiner certains des outils pré-mentionnés, mais aussi de nous familiariser et d'apprendre à automatiser la configuration de nos réseaux.

En ce qui concerne les options, nous avons plusieurs choix.

- [GNS3 VM](https://www.gns3.com/software/download-vm)
- [Eve-ng](https://www.eve-ng.net/)
- [Unimus](https://unimus.net/) Ce n'est pas un environnement de laboratoire, mais un concept intéressant.

Nous allons construire notre laboratoire en utilisant [Eve-ng](https://www.eve-ng.net/). Comme mentionné précédemment, vous pouvez utiliser un dispositif physique, mais honnêtement, un environnement virtuel signifie que nous pouvons avoir un environnement de bac à sable pour tester de nombreux scénarios différents. De plus, pouvoir jouer avec différents dispositifs et topologies pourrait être intéressant.

Nous allons tout faire sur EVE-NG avec l'édition communautaire.

### Démarrage

L'édition communautaire est disponible en formats ISO et OVF pour [téléchargement](https://www.eve-ng.net/index.php/download/).

Nous allons utiliser le téléchargement OVF, mais avec l'ISO, il y a l'option de construire sur un serveur bare metal sans avoir besoin d'un hyperviseur.

![](Images/Day25_Networking1.png)

Pour notre guide, nous allons utiliser VMware Workstation car j'ai une licence via mon vExpert, mais vous pouvez également utiliser VMware Player ou l'une des autres options mentionnées dans la [documentation](https://www.eve-ng.net/index.php/documentation/installation/system-requirement/). Malheureusement, nous ne pouvons pas utiliser notre VirtualBox précédemment utilisé !

C'est aussi là que j'ai eu un problème avec GNS3 avec VirtualBox même si c'est supporté.

[Télécharger VMware Workstation Player - GRATUIT](https://www.vmware.com/uk/products/workstation-player.html)

[VMware Workstation PRO](https://www.vmware.com/uk/products/workstation-pro.html) Il est également noté qu'il y a une période d'évaluation gratuite !

### Installation sur VMware Workstation PRO

Maintenant que nous avons téléchargé et installé notre logiciel d'hyperviseur, et que nous avons téléchargé l'OVF EVE-NG. Si vous utilisez VMware Player, veuillez me faire savoir si ce processus est le même.

Nous sommes maintenant prêts à configurer les choses.

Ouvrez VMware Workstation, puis sélectionnez `file` et `open`.

![](Images/Day25_Networking2.png)

Lorsque vous téléchargez l'image OVF EVE-NG, elle se trouvera dans un fichier compressé. Extrayez le contenu dans son dossier pour qu'il ressemble à ceci.

![](Images/Day25_Networking3.png)

Accédez à l'emplacement où vous avez téléchargé l'image OVF EVE-NG et commencez l'importation.

Donnez-lui un nom reconnaissable et stockez la machine virtuelle quelque part sur votre système.

![](Images/Day25_Networking4.png)

Lorsque l'importation est terminée, augmentez le nombre de processeurs à 4 et la mémoire allouée à 8 Go. (Cela devrait être le cas après l'importation avec la dernière version, sinon, modifiez les paramètres de la VM.)

Assurez-vous également que la case à cocher Virtualiser Intel VT-x/EPT ou AMD-V/RVI est activée. Cette option indique à VMware Workstation de transmettre les indicateurs de virtualisation à l'OS invité (virtualisation imbriquée). C'était le problème que j'avais avec GNS3 avec VirtualBox même si mon CPU le permet.

![](Images/Day25_Networking5.png)

### Mise sous tension et accès

Remarque et piste : Souvenez-vous que j'ai mentionné que cela ne fonctionnerait pas avec VirtualBox ! Eh bien, j'ai eu le même problème avec VMware Workstation et EVE-NG, mais ce n'était pas la faute de la plateforme de virtualisation !

J'ai WSL2 en cours d'exécution sur ma machine Windows et cela semble supprimer la capacité de pouvoir exécuter quoi que ce soit imbriqué dans votre environnement. Je suis confus quant à la raison pour laquelle la VM Ubuntu fonctionne car elle semble supprimer l'aspect de virtualisation Intel VT-d du CPU lors de l'utilisation de WSL2.

Pour résoudre ce problème, nous pouvons exécuter la commande suivante sur notre machine Windows et redémarrer le système. Notez que tant que cela est désactivé, vous ne pourrez pas utiliser WSL2.

`bcdedit /set hypervisorlaunchtype off`

Lorsque vous voulez revenir et utiliser WSL2, vous devrez exécuter cette commande et redémarrer.

`bcdedit /set hypervisorlaunchtype auto`

Ces deux commandes doivent être exécutées en tant qu'administrateur !

Retour au spectacle, vous devriez maintenant avoir une machine sous tension dans VMware Workstation et vous devriez avoir une invite ressemblant à ceci.

![](Images/Day25_Networking6.png)

Sur l'invite ci-dessus, vous pouvez utiliser :

nom d'utilisateur = root
mot de passe = eve

Vous devrez ensuite fournir à nouveau le mot de passe root, qui sera utilisé pour se connecter en SSH à l'hôte plus tard.

Nous pouvons ensuite changer le nom d'hôte.

![](Images/Day25_Networking7.png)

Ensuite, nous définissons un nom de domaine DNS. J'ai utilisé celui ci-dessous, mais je ne suis pas sûr s'il devra être modifié plus tard.

![](Images/Day25_Networking8.png)

Ensuite, nous configurons le réseau. Je sélectionne statique afin que l'adresse IP donnée soit persistante après les redémarrages.

![](Images/Day25_Networking9.png)

La dernière étape consiste à fournir une adresse IP statique à partir d'un réseau accessible depuis votre poste de travail.

![](Images/Day25_Networking10.png)

Il y a quelques étapes supplémentaires ici où vous devrez fournir un masque de sous-réseau pour votre réseau, une passerelle par défaut et un DNS.

Une fois terminé, il redémarrera. Lorsqu'il sera de nouveau opérationnel, vous pourrez prendre votre adresse IP statique et la mettre dans votre navigateur.

![](Images/Day25_Networking11.png)

Le nom d'utilisateur par défaut pour l'interface graphique est `admin` et le mot de passe est `eve`, tandis que le nom d'utilisateur par défaut pour SSH est `root` et le mot de passe est `eve`, mais cela aurait été modifié si vous l'avez changé pendant la configuration.

![](Images/Day25_Networking12.png)

J'ai choisi HTML5 pour la console plutôt que native, car cela ouvrira un nouvel onglet dans votre navigateur lorsque vous naviguerez à travers différentes consoles.

Ensuite, nous allons :

- Installer le pack client EVE-NG
- Charger quelques images réseau dans EVE-NG
- Construire une topologie réseau
- Ajouter des nœuds
- Connecter des nœuds
- Commencer à construire des scripts Python
- Regarder telnetlib, Netmiko, Paramiko et Pexpect

## Ressources

- [Cours gratuit : Introduction à EVE-NG](https://www.youtube.com/watch?v=g6B0f_E0NMg)
- [EVE-NG - Créer votre premier laboratoire](https://www.youtube.com/watch?v=9dPWARirtK8)
- [3 compétences nécessaires pour l'automatisation du réseau](https://www.youtube.com/watch?v=KhiJ7Fu9kKA&list=WL&index=122&t=89s)
- [Cours complet de réseautage informatique](https://www.youtube.com/watch?v=IPvYjXCsTg8)
- [Réseautage pratique](http://www.practicalnetworking.net/)
- [Automatisation du réseau Python](https://www.youtube.com/watch?v=xKPzLplPECU&list=WL&index=126)

À demain pour le [Jour 26](day26.md)