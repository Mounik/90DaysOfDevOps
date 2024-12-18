## Construction de notre Laboratoire

Nous allons continuer la configuration de notre réseau émulé en utilisant EVE-NG, puis espérons déployer quelques dispositifs et commencer à réfléchir à la manière dont nous pouvons automatiser la configuration de ces dispositifs. Le [Jour 25](day25.md), nous avons couvert l'installation d'EVE-NG sur notre machine en utilisant VMware Workstation.

### Installation du Client EVE-NG

Il existe également un pack client qui nous permet de choisir quelle application est utilisée lorsque nous nous connectons en SSH aux dispositifs. Il configurera également Wireshark pour capturer des paquets entre les liens. Vous pouvez obtenir le pack client pour votre système d'exploitation (Windows, macOS, Linux).

[Téléchargement du Client EVE-NG](https://www.eve-ng.net/index.php/download/)

![](Images/Day26_Networking1.png)

Astuce rapide : Si vous utilisez Linux comme client, il existe ce [pack client](https://github.com/SmartFinn/eve-ng-integration).

L'installation est simple, il suffit de suivre les instructions et je suggère de laisser les paramètres par défaut.

### Obtention des Images Réseau

Cette étape a été un défi. J'ai suivi quelques vidéos que je vais lier à la fin, qui mènent à certaines ressources et téléchargements pour nos images de routeurs et de commutateurs, tout en nous expliquant comment et où les télécharger.

Il est important de noter que j'utilise tout cela à des fins éducatives. Je suggère de télécharger des images officielles auprès des fournisseurs de réseau.

[Blog & Liens vers des Vidéos YouTube](https://loopedback.com/2019/11/15/setting-up-eve-ng-for-ccna-ccnp-ccie-level-studies-includes-multiple-vendor-node-support-an-absolutely-amazing-study-tool-to-check-out-asap/)

[Comment Ajouter une Image Cisco VIRL vIOS à Eve-ng](https://networkhunt.com/how-to-add-cisco-virl-vios-image-to-eve-ng/)

Globalement, les étapes ici sont un peu compliquées et pourraient être beaucoup plus simples, mais les blogs et vidéos ci-dessus expliquent le processus d'ajout des images à votre boîte EVE-NG.

J'ai utilisé FileZilla pour transférer le fichier qcow2 vers la VM via SFTP.

Pour notre laboratoire, nous avons besoin de Cisco vIOS L2 (commutateurs) et de Cisco vIOS (routeur).

### Création d'un Laboratoire

Dans l'interface web d'EVE-NG, nous allons créer notre nouvelle topologie réseau. Nous aurons quatre commutateurs et un routeur qui servira de passerelle vers les réseaux extérieurs.

| Nœud    | Adresse IP   |
| ------- | ------------ |
| Routeur | 10.10.88.110 |
| Commutateur1 | 10.10.88.111 |
| Commutateur2 | 10.10.88.112 |
| Commutateur3 | 10.10.88.113 |
| Commutateur4 | 10.10.88.114 |

#### Ajout de Nos Nœuds à EVE-NG

Lorsque vous vous connectez pour la première fois à EVE-NG, vous verrez un écran comme celui ci-dessous. Nous voulons commencer par créer notre premier laboratoire.

![](Images/Day26_Networking2.png)

Donnez un nom à votre laboratoire ; les autres champs sont facultatifs.

![](Images/Day26_Networking3.png)

Vous serez ensuite accueilli avec une toile vierge pour commencer à créer votre réseau. Faites un clic droit sur votre toile et choisissez "ajouter un nœud".

À partir de là, vous aurez une longue liste d'options de nœuds. Si vous avez suivi les instructions ci-dessus, vous aurez les deux options en bleu ci-dessous, et les autres seront grises et non sélectionnables.

![](Images/Day26_Networking4.png)

Nous voulons ajouter les éléments suivants à notre laboratoire :

- 1 x Cisco vIOS Router
- 4 x Cisco vIOS Switch

Suivez l'assistant simple pour les ajouter à votre laboratoire, et cela devrait ressembler à quelque chose comme ceci.

![](Images/Day26_Networking5.png)

#### Connexion de Nos Nœuds

Nous devons maintenant ajouter la connectivité entre nos routeurs et commutateurs. Nous pouvons le faire assez facilement en survolant le dispositif et en voyant l'icône de connexion comme ci-dessous, puis en connectant cela au dispositif que nous souhaitons connecter.

![](Images/Day26_Networking6.png)

Lorsque vous avez fini de connecter votre environnement, vous pouvez également ajouter un moyen de définir des limites physiques ou des emplacements en utilisant des boîtes ou des cercles, que vous pouvez également trouver dans le menu contextuel. Vous pouvez également ajouter du texte, ce qui est utile lorsque nous voulons définir nos noms ou adresses IP dans nos laboratoires.

J'ai fait en sorte que mon laboratoire ressemble à ce qui suit.

![](Images/Day26_Networking7.png)

Vous remarquerez également que le laboratoire ci-dessus est entièrement éteint. Nous pouvons démarrer notre laboratoire en sélectionnant tout, en faisant un clic droit et en sélectionnant "démarrer la sélection".

![](Images/Day26_Networking8.png)

Une fois notre laboratoire opérationnel, vous pourrez vous connecter à chaque dispositif via la console, et vous remarquerez qu'à ce stade, ils sont assez basiques sans configuration. Nous pouvons ajouter une configuration à chaque nœud en copiant ou en créant la vôtre dans chaque terminal.

Je laisserai ma configuration dans le dossier Networking du dépôt pour référence.

| Nœud    | Configuration         |
| ------- | --------------------- |
| Routeur | [R1](Networking/R1)   |
| Commutateur1 | [SW1](Networking/SW1) |
| Commutateur2 | [SW2](Networking/SW2) |
| Commutateur3 | [SW3](Networking/SW3) |
| Commutateur4 | [SW4](Networking/SW4) |

## Ressources

- [Cours Gratuit : Introduction à EVE-NG](https://www.youtube.com/watch?v=g6B0f_E0NMg)
- [EVE-NG - Créer votre premier laboratoire](https://www.youtube.com/watch?v=9dPWARirtK8)
- [3 Compétences Nécessaires pour l'Automatisation du Réseau](https://www.youtube.com/watch?v=KhiJ7Fu9kKA&list=WL&index=122&t=89s)
- [Cours Complet de Réseautage Informatique](https://www.youtube.com/watch?v=IPvYjXCsTg8)
- [Réseautage Pratique](http://www.practicalnetworking.net/)
- [Automatisation du Réseau Python](https://www.youtube.com/watch?v=xKPzLplPECU&list=WL&index=126)

La plupart des exemples que j'utilise ici, car je ne suis pas un ingénieur réseau, proviennent de ce livre exhaustif qui n'est pas gratuit, mais j'utilise certains des scénarios pour aider à comprendre l'automatisation du réseau.

- [Hands-On Enterprise Automation with Python (Livre)](https://www.packtpub.com/product/hands-on-enterprise-automation-with-python/9781788998512)

À demain pour le [Jour 27](day27.md)