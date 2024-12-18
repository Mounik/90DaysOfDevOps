Le contenu ci-dessous provient principalement de la série [Networking Fundamentals](https://www.youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi) de Practical Networking. Si vous préférez ce contenu sous forme de vidéo, consultez ces deux vidéos :

* [The OSI Model: A Practical Perspective - Layers 1 / 2 / 3](https://www.youtube.com/watch?v=LkolbURrtTs&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=3)
* [The OSI Model: A Practical Perspective - Layers 4 / 5+](https://www.youtube.com/watch?v=0aGqGKrRE0g&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=4)

## Le Modèle OSI - Les 7 Couches

L'objectif global du réseau en tant qu'industrie est de permettre à deux hôtes de partager des données. Avant le réseau, si je voulais transférer des données d'un hôte à un autre, je devais brancher quelque chose dans cet hôte, le transporter jusqu'à l'autre hôte et le brancher sur l'autre hôte.

Le réseau nous permet d'automatiser cela en permettant à l'hôte de partager des données automatiquement via le câble. Pour que ces hôtes puissent le faire, ils doivent suivre un ensemble de règles.

Cela n'est pas différent de toute autre langue. L'anglais a un ensemble de règles que deux locuteurs anglais doivent suivre. L'espagnol a son propre ensemble de règles. Le français a son propre ensemble de règles, tandis que le réseau a également son propre ensemble de règles.

Les règles pour le réseau sont divisées en sept couches différentes, et ces couches sont connues sous le nom de modèle OSI.

### Introduction au Modèle OSI

Le Modèle OSI (Open Systems Interconnection Model) est un cadre utilisé pour décrire les fonctions d'un système de réseau. Le modèle OSI caractérise les fonctions informatiques en un ensemble universel de règles et d'exigences pour soutenir l'interopérabilité entre différents produits et logiciels. Dans le modèle de référence OSI, les communications entre un système informatique sont divisées en sept couches d'abstraction différentes : **Physique, Liaison de Données, Réseau, Transport, Session, Présentation et Application**.

![](Images/Day22_Networking1.png)

### Physique

La couche 1 du modèle OSI est connue sous le nom de couche physique. Elle permet de transférer des données d'un hôte à un autre via un moyen, qu'il s'agisse d'un câble physique ou du Wi-Fi, qui peut également être considéré dans cette couche. Nous pourrions également voir certains matériels plus anciens ici, comme des concentrateurs et des répéteurs, pour transporter les données d'un hôte à un autre.

![](Images/Day22_Networking2.png)

### Liaison de Données

La couche 2, la liaison de données, permet un transfert de nœud à nœud où les données sont empaquetées en trames. Il y a également un niveau de correction d'erreurs qui pourrait avoir eu lieu au niveau de la couche physique. C'est également là que nous introduisons ou voyons pour la première fois les adresses MAC.

C'est ici que nous voyons la première mention des commutateurs que nous avons couverts lors de notre premier jour de réseau sur le [Jour 21](day21.md).

![](Images/Day22_Networking3.png)

### Réseau

Vous avez probablement entendu parler des commutateurs de couche 3 ou des commutateurs de couche 2. Dans notre modèle OSI, la couche 3, le Réseau, a pour objectif une livraison de bout en bout. C'est ici que nous voyons également nos adresses IP mentionnées dans l'aperçu du premier jour.

Les routeurs et les hôtes existent à la couche 3 ; rappelez-vous que le routeur permet de router entre plusieurs réseaux. Tout ce qui a une adresse IP pourrait être considéré comme de la couche 3.

![](Images/Day22_Networking4.png)

Pourquoi avons-nous besoin de schémas d'adressage à la fois sur les couches 2 et 3 ? (Adresses MAC vs Adresses IP)

Si nous pensons à transférer des données d'un hôte à un autre, chaque hôte a une adresse IP, mais il y a plusieurs commutateurs et routeurs entre eux. Chacun de ces dispositifs a cette adresse MAC de couche 2.

L'adresse MAC de couche 2 ira de l'hôte au commutateur/routeur uniquement ; elle se concentre sur les sauts, tandis que les adresses IP de couche 3 resteront avec ce paquet de données jusqu'à ce qu'il atteigne son hôte de destination. (De bout en bout)

Adresses IP - Couche 3 = Livraison de bout en bout

Adresses MAC - Couche 2 = Livraison de saut en saut

Il existe un protocole réseau que nous aborderons, mais pas aujourd'hui, appelé ARP (Address Resolution Protocol), qui lie nos adresses de couche 3 et de couche 2.

### Transport

Livraison de service à service, la couche 4 est là pour distinguer les flux de données. De la même manière que les couches 3 et 2 avaient leurs schémas d'adressage, en couche 4, nous avons des ports.

![](Images/Day22_Networking5.png)

### Session, Présentation, Application

La distinction entre les couches 5, 6 et 7 est ou est devenue quelque peu floue.

Il vaut la peine de regarder le [Modèle TCP/IP](https://www.geeksforgeeks.org/tcp-ip-model/) pour obtenir une compréhension plus récente.

Essayons maintenant d'expliquer ce qui se passe lorsque les hôtes communiquent entre eux en utilisant cette pile de réseau. Cet hôte a une application qui va générer des données destinées à être envoyées à un autre hôte.

L'hôte source va passer par ce que l'on appelle le processus d'encapsulation. Ces données seront d'abord envoyées à la couche 4.

La couche 4 va ajouter un en-tête à ces données, ce qui peut faciliter l'objectif de la couche 4, qui est la livraison de service à service. Il s'agira d'un port utilisant soit TCP, soit UDP. Il inclura également le port source et le port de destination.

Cela peut également être connu sous le nom de segment (Données et Port).

Ce segment sera transmis à la pile OSI vers la couche 3, la couche réseau, et la couche réseau ajoutera un autre en-tête à ces données.
Cet en-tête facilitera l'objectif de la couche 3, qui est la livraison de bout en bout, ce qui signifie que dans cet en-tête, vous aurez une adresse IP source et une adresse IP de destination. L'en-tête plus les données peuvent également être appelés un paquet.

La couche 3 prendra ensuite ce paquet et le transmettra à la couche 2. La couche 2 ajoutera à nouveau un autre en-tête à ces données pour accomplir l'objectif de la couche 2, qui est la livraison de saut en saut, ce qui signifie que cet en-tête inclura une adresse MAC source et de destination.
Cela est connu sous le nom de trame lorsque vous avez l'en-tête de couche 2 et les données.

Cette trame est ensuite convertie en uns et en zéros et envoyée sur le câble physique de couche 1 ou le Wi-Fi.

![](Images/Day22_Networking6.png)

J'ai mentionné ci-dessus la dénomination de chaque couche d'en-tête plus les données, mais j'ai décidé de dessiner cela également.

![](Images/Day22_Networking7.png)

L'application envoyant les données est envoyée quelque part, donc la réception est quelque peu inversée pour remonter la pile et entrer dans l'hôte récepteur.

![](Images/Day22_Networking8.png)

## Ressources

* [Networking Fundamentals](https://www.youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi)
* [Computer Networking full course](https://www.youtube.com/watch?v=IPvYjXCsTg8)

À demain pour le [Jour 23](day23.md)