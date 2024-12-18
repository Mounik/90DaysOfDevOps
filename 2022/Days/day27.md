## Mise en Pratique avec Python et Réseau

Dans cette dernière section des fondamentaux du réseautage, nous allons couvrir certaines tâches et outils d'automatisation avec notre environnement de laboratoire créé le [Jour 26](day26.md).

Nous allons utiliser un tunnel SSH pour nous connecter à nos dispositifs depuis notre client plutôt que telnet. Le tunnel SSH créé entre le client et le dispositif est chiffré. Nous avons également couvert SSH dans la section Linux le [Jour 18](day18.md).

## Accéder à notre environnement émulé virtuel

Pour interagir avec nos commutateurs, nous avons besoin soit d'une station de travail à l'intérieur du réseau EVE-NG, soit vous pouvez déployer une boîte Linux avec Python installé pour effectuer votre automatisation ([Ressource pour configurer Linux à l'intérieur d'EVE-NG](https://www.youtube.com/watch?v=3Qstk3zngrY)) ou vous pouvez faire quelque chose comme moi et définir un cloud pour l'accès depuis votre station de travail.

![](Images/Day27_Networking3.png)

Pour ce faire, nous avons fait un clic droit sur notre toile et avons sélectionné "réseau", puis "Management(Cloud0)". Cela créera un pont vers notre réseau domestique.

![](Images/Day27_Networking4.png)

Cependant, nous n'avons rien à l'intérieur de ce réseau, donc nous devons ajouter des connexions du nouveau réseau à chacun de nos dispositifs. (Mes connaissances en réseautage nécessitent plus d'attention et je pense que vous pourriez simplement faire cette étape suivante vers le routeur principal, puis avoir une connectivité avec le reste du réseau via ce seul câble ?)

Je me suis ensuite connecté à chacun de nos dispositifs et j'ai exécuté les commandes suivantes pour les interfaces applicables à l'endroit où le cloud entre.

```
enable
config t
int gi0/0
IP add DHCP
no sh
exit
exit
sh ip int br
```

La dernière étape nous donne l'adresse DHCP de notre réseau domestique. Ma liste de réseau de dispositifs est la suivante :

| Nœud    | Adresse IP   | IP Réseau Domestique |
| ------- | ------------ | --------------- |
| Routeur  | 10.10.88.110 | 192.168.169.115 |
| Commutateur1 | 10.10.88.111 | 192.168.169.178 |
| Commutateur2 | 10.10.88.112 | 192.168.169.193 |
| Commutateur3 | 10.10.88.113 | 192.168.169.125 |
| Commutateur4 | 10.10.88.114 | 192.168.169.197 |

### SSH vers un dispositif réseau

Avec ce qui précède en place, nous pouvons maintenant nous connecter à nos dispositifs sur notre réseau domestique en utilisant notre station de travail. J'utilise Putty mais j'ai également accès à d'autres terminaux comme git bash qui me permettent de me connecter en SSH à nos dispositifs.

Ci-dessous, vous pouvez voir que nous avons une connexion SSH à notre dispositif routeur (R1).

![](Images/Day27_Networking5.png)

### Utiliser Python pour collecter des informations de nos dispositifs

Le premier exemple de la manière dont nous pouvons utiliser Python est de collecter des informations de tous nos dispositifs, et en particulier, je veux pouvoir me connecter à chacun et exécuter une commande simple pour me fournir la configuration et les paramètres de l'interface. J'ai stocké ce script ici [netmiko_con_multi.py](Networking/netmiko_con_multi.py).

Maintenant, lorsque j'exécute ceci, je peux voir la configuration de chaque port sur tous mes dispositifs.

![](Images/Day27_Networking6.png)

Cela pourrait être utile si vous avez beaucoup de dispositifs différents ; créez ce script pour pouvoir contrôler et comprendre rapidement toutes les configurations en un seul endroit.

### Utiliser Python pour configurer nos dispositifs

Ce qui précède est utile, mais qu'en est-il de l'utilisation de Python pour configurer nos dispositifs ? Dans notre scénario, nous avons un port trunké entre `SW1` et `SW2`. Imaginez si cela devait être fait sur de nombreux commutateurs similaires ; nous voulons automatiser cela et ne pas avoir à nous connecter manuellement à chaque commutateur pour effectuer le changement de configuration.

Nous pouvons utiliser [netmiko_sendchange.py](Networking/netmiko_sendchange.py) pour y parvenir. Cela se connectera via SSH et effectuera ce changement sur notre `SW1`, ce qui changera également `SW2`.

![](Images/Day27_Networking7.png)

Maintenant, pour ceux qui regardent le code, vous verrez que le message apparaît et nous dit `envoi de la configuration au dispositif`, mais il n'y a pas de confirmation que cela s'est produit. Nous pourrions ajouter un code supplémentaire à notre script pour effectuer cette vérification et cette validation sur notre commutateur, ou nous pourrions modifier notre script précédent pour nous montrer cela. [netmiko_con_multi_vlan.py](Networking/netmiko_con_multi_vlan.py)

![](Images/Day27_Networking8.png)

### Sauvegarder les configurations de vos dispositifs

Un autre cas d'utilisation serait de capturer nos configurations réseau et de nous assurer que nous les avons sauvegardées, mais encore une fois, nous ne voulons pas nous connecter à chaque dispositif que nous avons sur notre réseau, donc nous pouvons également automatiser cela en utilisant [backup.py](Networking/backup.py). Vous devrez également remplir le fichier [backup.txt](Networking/backup.txt) avec les adresses IP que vous souhaitez sauvegarder.

Exécutez votre script et vous devriez voir quelque chose comme ci-dessous.

![](Images/Day27_Networking9.png)

Cela pourrait être moi écrivant juste un simple script d'impression en Python, donc je devrais vous montrer les fichiers de sauvegarde aussi.

![](Images/Day27_Networking10.png)

### Paramiko

Un module Python largement utilisé pour SSH. Vous pouvez en savoir plus sur le lien GitHub officiel [ici](https://github.com/paramiko/paramiko).

Nous pouvons installer ce module en utilisant la commande `pip install paramiko`.

![](Images/Day27_Networking1.png)

Nous pouvons vérifier l'installation en entrant dans le shell Python et en important le module paramiko.

![](Images/Day27_Networking2.png)

### Netmiko

Le module netmiko cible spécifiquement les dispositifs réseau, tandis que paramiko est un outil plus large pour gérer les connexions SSH dans l'ensemble.

Netmiko, que nous avons utilisé ci-dessus avec paramiko, peut être installé en utilisant `pip install netmiko`.

Netmiko prend en charge de nombreux fournisseurs et dispositifs réseau ; vous pouvez trouver une liste des dispositifs pris en charge sur la [page GitHub](https://github.com/ktbyers/netmiko#supports).

### Autres modules

Il est également utile de mentionner quelques autres modules que nous n'avons pas eu l'occasion d'examiner, mais ils offrent beaucoup plus de fonctionnalités en matière d'automatisation du réseau.

`netaddr` est utilisé pour travailler avec et manipuler les adresses IP ; encore une fois, l'installation est simple avec `pip install netaddr`.

Vous pourriez vous retrouver à vouloir stocker beaucoup de votre configuration de commutateur dans une feuille de calcul Excel ; `xlrd` permettra à vos scripts de lire le classeur Excel et de convertir les lignes et les colonnes en une matrice. Utilisez `pip install xlrd` pour installer le module.

D'autres cas d'utilisation où l'automatisation du réseau peut être utilisée et que je n'ai pas eu l'occasion d'examiner peuvent être trouvés [ici](https://github.com/ktbyers/pynet/tree/master/presentations/dfwcug/examples).

Je pense que cela conclut notre section Réseautage de #90DaysOfDevOps. Le réseautage est un domaine que je n'ai pas vraiment touché depuis un certain temps, et il y a tellement plus à couvrir, mais j'espère qu'entre mes notes et les ressources partagées tout au long, cela sera utile pour certains.

## Ressources

- [Cours Gratuit : Introduction à EVE-NG](https://www.youtube.com/watch?v=g6B0f_E0NMg)
- [EVE-NG - Créer votre premier laboratoire](https://www.youtube.com/watch?v=9dPWARirtK8)
- [3 Compétences Nécessaires pour l'Automatisation du Réseau](https://www.youtube.com/watch?v=KhiJ7Fu9kKA&list=WL&index=122&t=89s)
- [Cours Complet de Réseautage Informatique](https://www.youtube.com/watch?v=IPvYjXCsTg8)
- [Réseautage Pratique](http://www.practicalnetworking.net/)
- [Automatisation du Réseau Python](https://www.youtube.com/watch?v=xKPzLplPECU&list=WL&index=126)

La plupart des exemples que j'utilise ici, car je ne suis pas un ingénieur réseau, proviennent de ce livre exhaustif qui n'est pas gratuit, mais j'utilise certains des scénarios pour aider à comprendre l'automatisation du réseau.

- [Hands-On Enterprise Automation with Python (Livre)](https://www.packtpub.com/product/hands-on-enterprise-automation-with-python/9781788998512)

À demain pour le [Jour 28](day28.md), où nous commencerons à nous pencher sur le cloud computing et à obtenir une bonne compréhension et des connaissances fondamentales sur le sujet et ce qui est disponible.