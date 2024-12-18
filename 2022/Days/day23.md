Le contenu ci-dessous provient principalement de la série [Networking Fundamentals](https://www.youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi) de Practical Networking. Si vous préférez ce contenu sous forme de vidéo, consultez cette vidéo :

* [Network Protocols - ARP, FTP, SMTP, HTTP, SSL, TLS, HTTPS, DNS, DHCP](https://www.youtube.com/watch?v=E5bSumTAHZE&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=12)

## Protocoles Réseau

Un ensemble de règles et de messages qui forment une norme. Une norme Internet.

- ARP - Address Resolution Protocol

Si vous voulez vraiment entrer dans les détails sur ARP, vous pouvez lire la norme Internet ici : [RFC 826](https://datatracker.ietf.org/doc/html/rfc826).

Connecte les adresses IP aux adresses physiques fixes des machines, également connues sous le nom d'adresses MAC sur un réseau de couche 2.

![](Images/Day23_Networking1.png)

- FTP - File Transfer Protocol

Permet le transfert de fichiers de la source vers la destination. Généralement, ce processus est authentifié, mais il est possible, si configuré, d'utiliser un accès anonyme. Vous verrez plus fréquemment maintenant FTPS, qui fournit une connectivité SSL/TLS aux serveurs FTP depuis le client pour une meilleure sécurité. Ce protocole se trouve dans la couche Application du modèle OSI.

![](Images/Day23_Networking2.png)

- SMTP - Simple Mail Transfer Protocol

Utilisé pour la transmission de courriels, les serveurs de messagerie utilisent SMTP pour envoyer et recevoir des messages. Même avec Microsoft 365, le protocole SMTP est toujours utilisé à cette fin.

![](Images/Day23_Networking3.png)

- HTTP - Hyper Text Transfer Protocol

HTTP est la base d'Internet et de la navigation sur le contenu. Il nous permet d'accéder facilement à nos sites web préférés. HTTP est encore largement utilisé, mais HTTPS devrait être utilisé sur la plupart de vos sites préférés.

![](Images/Day23_Networking4.png)

- SSL - Secure Sockets Layer | TLS - Transport Layer Security

TLS a pris le relais de SSL. TLS est un **protocole cryptographique** qui assure des communications sécurisées sur un réseau. Il peut et sera trouvé dans le courrier électronique, la messagerie instantanée et d'autres applications, mais il est le plus couramment utilisé pour sécuriser HTTPS.

![](Images/Day23_Networking5.png)

- HTTPS - HTTP sécurisé avec SSL/TLS

Une extension de HTTP, utilisée pour des communications sécurisées sur un réseau, HTTPS est crypté avec TLS comme mentionné ci-dessus. L'objectif ici était d'apporter authentification, confidentialité et intégrité pendant l'échange de données entre les hôtes.

![](Images/Day23_Networking6.png)

- DNS - Domain Name System

Le DNS est utilisé pour mapper des noms de domaine conviviaux. Par exemple, nous connaissons tous [google.com](https://google.com), mais si vous ouvrez un navigateur et tapez [8.8.8.8](https://8.8.8.8), vous obtiendrez Google tel que nous le connaissons. Cependant, bonne chance pour essayer de mémoriser toutes les adresses IP de tous vos sites web, où pour certains d'entre eux nous utilisons même Google pour trouver des informations.

C'est là que le DNS intervient ; il garantit que les hôtes, les services et autres ressources sont accessibles.

Sur tous les hôtes, s'ils nécessitent une connectivité Internet, ils doivent avoir un DNS pour pouvoir résoudre ces noms de domaine. Le DNS est un domaine dans lequel vous pourriez passer des jours et des années à apprendre. Je dirais également par expérience que le DNS est la cause la plus courante de toutes les erreurs en matière de réseau. Je ne suis pas sûr qu'un ingénieur réseau serait d'accord avec cela, cependant.

![](Images/Day23_Networking7.png)

- DHCP - Dynamic Host Configuration Protocol

Nous avons beaucoup discuté des protocoles nécessaires pour faire fonctionner nos hôtes, qu'il s'agisse d'accéder à Internet ou de transférer des fichiers entre eux.

Il y a 4 choses dont nous avons besoin sur chaque hôte pour qu'il puisse accomplir ces deux tâches.

- Adresse IP
- Masque de sous-réseau
- Passerelle par défaut
- DNS

Nous avons vu que l'adresse IP est une adresse unique pour votre hôte sur le réseau où il réside ; nous pouvons considérer cela comme notre numéro de maison.

Nous aborderons bientôt le masque de sous-réseau, mais vous pouvez le considérer comme un code postal ou un code ZIP.

Une passerelle par défaut est l'adresse IP de notre routeur, généralement sur notre réseau, nous fournissant cette connectivité de couche 3. Vous pourriez considérer cela comme la route unique qui nous permet de sortir de notre rue.

Ensuite, nous avons le DNS, comme nous venons de le voir, pour nous aider à convertir des adresses IP publiques compliquées en noms de domaine plus appropriés et mémorables. Peut-être pouvons-nous considérer cela comme le grand bureau de tri pour nous assurer que nous recevons le bon courrier.

Comme je l'ai dit, chaque hôte a besoin de ces 4 choses. Si vous avez 1000 ou 10 000 hôtes, cela prendra beaucoup de temps pour déterminer chacune de ces choses individuellement. C'est là que le DHCP intervient et vous permet de déterminer une portée pour votre réseau, puis ce protocole distribuera à tous les hôtes disponibles dans votre réseau.

Un autre exemple est lorsque vous entrez dans un café, prenez un café et vous asseyez avec votre ordinateur portable ou votre téléphone, appelons cela votre hôte. Vous connectez votre hôte au Wi-Fi du café et vous obtenez accès à Internet, des messages et des courriels commencent à arriver et vous pouvez naviguer sur des pages web et des réseaux sociaux. Lorsque vous vous êtes connecté au Wi-Fi du café, votre machine aura obtenu une adresse DHCP soit d'un serveur DHCP dédié, soit, plus probablement, du routeur gérant également le DHCP.

![](Images/Day23_Networking8.png)

### Sous-réseaux

Un sous-réseau est une subdivision logique d'un réseau IP.

Les sous-réseaux divisent de grands réseaux en réseaux plus petits et plus gérables qui fonctionnent plus efficacement.

Chaque sous-réseau est une subdivision logique du réseau plus grand. Les dispositifs connectés avec un sous-réseau suffisant partagent des identifiants d'adresses IP communs, leur permettant de communiquer entre eux.

Les routeurs gèrent la communication entre les sous-réseaux.

La taille d'un sous-réseau dépend des besoins de connectivité et de la technologie réseau utilisée.

Une organisation est responsable de la détermination du nombre et de la taille des sous-réseaux dans les limites de l'espace d'adressage disponible, et les détails restent locaux à cette organisation. Les sous-réseaux peuvent également être segmentés en sous-réseaux encore plus petits pour des choses comme des liaisons point à point ou des sous-réseaux supportant quelques dispositifs.

Parmi d'autres avantages, la segmentation de grands réseaux en sous-réseaux permet la réaffectation des adresses IP et soulage la congestion du réseau, rationalisant la communication et l'efficacité du réseau.

Les sous-réseaux peuvent également améliorer la sécurité du réseau. Si une section d'un réseau est compromise, elle peut être mise en quarantaine, rendant difficile pour les acteurs malveillants de se déplacer dans le réseau plus large.

![](Images/Day23_Networking9.png)

## Ressources

- [Networking Fundamentals](https://www.youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi)
- [Subnetting Mastery](https://www.youtube.com/playlist?list=PLIFyRwBY_4bQUE4IB5c4VPRyDoLgOdExE)
- [Computer Networking full course](https://www.youtube.com/watch?v=IPvYjXCsTg8)

À demain pour le [Jour 24](day24.md)