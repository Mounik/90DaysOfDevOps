## Vue d'Ensemble : Installation et Configuration de Git

Git est un outil open-source et multiplateforme pour le contrôle de version. Si vous êtes comme moi, utilisant Ubuntu ou la plupart des environnements Linux, vous pourriez constater que Git est déjà installé sur votre système, mais nous allons passer par l'installation et la configuration.

Même si vous avez déjà Git installé sur votre système, il est également bon de s'assurer que nous sommes à jour.

### Installation de Git

Comme mentionné précédemment, Git est multiplateforme ; nous allons passer par Windows et Linux, mais vous pouvez également trouver macOS listé [ici](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

Pour [Windows](https://git-scm.com/download/win), nous pouvons obtenir nos installateurs à partir du site officiel.

Vous pourriez également utiliser `winget` sur votre machine Windows. Pensez à ceci comme votre gestionnaire de paquets d'applications Windows.

Avant d'installer quoi que ce soit, voyons quelle version nous avons sur notre machine Windows. Ouvrez une fenêtre PowerShell et exécutez `git --version`.

![](Images/Day36_Git1.png)

Nous pouvons également vérifier notre version WSL Ubuntu de Git.

![](Images/Day36_Git2.png)

Au moment de la rédaction, la dernière version Windows est `2.35.1`, donc nous avons quelques mises à jour à faire. Je m'attends à la même chose pour Linux.

J'ai téléchargé le dernier installateur et j'ai parcouru l'assistant et je vais documenter cela ici. La chose importante à noter est que Git désinstallera les versions précédentes avant d'installer la dernière.

Cela signifie que le processus montré ci-dessous est également le même processus pour la plupart des installations à partir de zéro Git.

C'est une installation très simple. Une fois téléchargé, double-cliquez et commencez. Lisez l'accord de licence GNU. Mais rappelez-vous que ceci est un logiciel gratuit et open-source.

![](Images/Day36_Git3.png)

Nous pouvons ensuite choisir des composants supplémentaires que nous souhaitons également installer mais également associer à Git. Sur Windows, je m'assure toujours d'installer Git Bash car cela nous permet d'exécuter des scripts bash sur Windows.

![](Images/Day36_Git4.png)

Nous pouvons ensuite choisir quel exécutable SSH nous souhaitons utiliser. Je le laisse comme l'OpenSSH empaqueté que vous pourriez avoir vu dans la section Linux.

![](Images/Day36_Git5.png)

Nous avons ensuite des fonctionnalités expérimentales que nous pourrions souhaiter activer. Pour moi, je n'en ai pas besoin, donc je ne les active pas. Vous pouvez toujours revenir dans l'installation et activer celles-ci plus tard.

![](Images/Day36_Git6.png)

L'installation est terminée, nous pouvons maintenant choisir d'ouvrir Git Bash ou les dernières notes de version.

![](Images/Day36_Git7.png)

La vérification finale consiste à jeter un coup d'œil dans notre fenêtre PowerShell pour voir quelle version de Git nous avons maintenant.

![](Images/Day36_Git8.png)

Très simple et maintenant nous sommes sur la dernière version. Sur notre machine Linux, nous semblions être un peu en retard, donc nous pouvons également parcourir ce processus de mise à jour.

Je lance simplement la commande `sudo apt-get install git`.

![](Images/Day36_Git9.png)

Vous pourriez également exécuter ce qui suit, qui ajoutera le dépôt pour les installations logicielles Git.

```
sudo add-apt-repository ppa:git-core/ppa -y
sudo apt-get update
sudo apt-get install git -y
git --version
```

### Configuration de Git

Lorsque nous utilisons Git pour la première fois, nous devons définir certains paramètres :

- Nom
- Email
- Éditeur par défaut
- Fin de ligne

Cela peut être fait à trois niveaux :

- Système = Tous les utilisateurs
- Global = Tous les dépôts de l'utilisateur actuel
- Local = Le dépôt actuel

Exemple :

`git config --global user.name "Michael Cade"`

`git config --global user.email Michael.Cade@90DaysOfDevOps.com`

En fonction de votre système d'exploitation, cela déterminera l'éditeur de texte par défaut. Sur ma machine Ubuntu, sans définir la commande suivante, j'utilise nano. La commande suivante changera ceci en Visual Studio Code.

`git config --global core.editor "code --wait"`

Maintenant, si nous voulons pouvoir voir toutes les configurations Git, nous pouvons utiliser la commande suivante.

`git config --global -e`

![](Images/Day36_Git10.png)

Sur n'importe quelle machine, ce fichier sera nommé `.gitconfig`. Sur ma machine Windows, vous le trouverez dans votre répertoire de compte utilisateur.

![](Images/Day36_Git11.png)

### Théorie de Git

J'ai mentionné dans le post d'hier qu'il y avait d'autres types de contrôle de version et que nous pouvons les diviser en deux types différents. L'un est Client-Serveur et l'autre est Distribué.

### Contrôle de Version Client-Serveur

Avant Git, le modèle de contrôle de version Client-Serveur était la méthode par défaut pour le contrôle de version. Un exemple de ceci serait [Apache Subversion](https://subversion.apache.org/), qui est un système de contrôle de version open-source fondé en 2000.

Dans ce modèle de contrôle de version Client-Serveur, la première étape que le développeur télécharge le code source et les fichiers réels du serveur. Cela n'élimine pas les conflits, mais cela élimine la complexité des conflits et comment les résoudre.

![](Images/Day36_Git12.png)

Par exemple, disons que nous avons deux développeurs travaillant sur les mêmes fichiers et que l'un gagne la course et commit ou télécharge son fichier en premier sur le serveur avec ses nouvelles modifications. Lorsque le deuxième développeur va mettre à jour, il a un conflit.

![](Images/Day36_Git13.png)

Donc maintenant, le développeur doit tirer le premier changement de code du développeur suivant pour vérifier et ensuite commettre une fois ces conflits réglés.

![](Images/Day36_Git15.png)

### Contrôle de Version Distribué

Git est loin d'être le seul système de contrôle de version distribué. Mais c'est vraiment le par défaut.

Certains des principaux avantages de Git sont :

- Rapide
- Intelligent
- Flexible
- Sûr et sécurisé

Contrairement au modèle de contrôle de version Client-Serveur, chaque développeur télécharge le dépôt source, ce qui signifie tout. Historique des commits, toutes les branches, etc.

![](Images/Day36_Git16.png)

## Ressources

- [Qu'est-ce que le contrôle de version ?](https://www.youtube.com/watch?v=Yc8sCSeMhi4)
- [Types de systèmes de contrôle de version](https://www.youtube.com/watch?v=kr62e_n6QuQ)
- [Tutoriel Git pour débutants](https://www.youtube.com/watch?v=8JJ101D3knE&t=52s)
- [Tutoriel Git pour professionnels](https://www.youtube.com/watch?v=Uszj_k0DGsg)
- [Git et GitHub pour débutants - Cours complet](https://www.youtube.com/watch?v=RGOj5yH7evk&t=8s)
- [Tutoriel complet sur Git et GitHub](https://www.youtube.com/watch?v=apGV9Kg7ics)

À demain pour le [Jour 37](day37.md)