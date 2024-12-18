## Configuration de la station de travail de développement - Toutes les jolies choses

À ne pas confondre avec la configuration des serveurs Linux, mais je voulais également montrer le choix et la flexibilité que nous avons avec le bureau Linux.

J'utilise un bureau Linux depuis presque un an maintenant et je l'ai configuré exactement comme je le souhaite en termes d'apparence et de sensation. En utilisant notre VM Ubuntu sur Virtual Box, nous pouvons parcourir certaines des personnalisations que j'ai apportées à mon système principal.

J'ai réalisé une vidéo YouTube qui présente le reste, car certaines personnes pourraient mieux suivre de cette manière :

[![Cliquez pour accéder à la vidéo YouTube](Images/Day20_YouTube.png)](https://youtu.be/jeEslAtHfKc)

Dès la sortie de la boîte, notre système ressemblera à ceci :

![](Images/Day20_Linux1.png)

Nous pouvons également voir notre shell bash par défaut ci-dessous :

![](Images/Day20_Linux2.png)

Une grande partie de cela repose sur les dotfiles, quelque chose que nous allons aborder dans cette dernière session Linux de la série.

### Dotfiles

Tout d'abord, je veux creuser dans les dotfiles. J'ai dit précédemment que Linux est composé de fichiers de configuration. Ces dotfiles sont des fichiers de configuration pour votre système Linux et vos applications.

J'ajouterai également que les dotfiles ne servent pas seulement à personnaliser et à rendre votre bureau joli, il existe également des modifications et des configurations de dotfiles qui vous aideront à améliorer votre productivité.

Comme je l'ai mentionné, de nombreux programmes logiciels stockent leurs configurations dans ces dotfiles. Ces dotfiles aident à gérer la fonctionnalité.

Chaque dotfile commence par un `.`. Vous pouvez probablement deviner d'où vient le nom ?

Jusqu'à présent, nous avons utilisé bash comme notre shell, ce qui signifie que vous aurez un .bashrc et un .bash_profile dans notre dossier personnel. Vous pouvez voir ci-dessous quelques dotfiles que nous avons sur notre système.

![](Images/Day20_Linux3.png)

Nous allons changer notre shell, nous verrons donc plus tard un nouveau fichier de configuration dotfile `.zshrc`.

Mais maintenant vous savez que si nous faisons référence à des dotfiles, vous savez qu'il s'agit de fichiers de configuration. Nous pouvons les utiliser pour ajouter des alias à notre invite de commande ainsi que des chemins vers différents emplacements. Certaines personnes publient leurs dotfiles pour qu'ils soient publiquement disponibles. Vous trouverez les miens ici sur mon GitHub [MichaelCade/dotfiles](https://github.com/MichaelCade/dotfiles). Ici, vous trouverez mon fichier `.zshrc` personnalisé, mon terminal de choix est terminator qui a également quelques fichiers de configuration dans le dossier, puis également quelques options d'arrière-plan.

### ZSH

Comme je l'ai mentionné tout au long de nos interactions jusqu'à présent, nous avons utilisé un shell bash, le shell par défaut avec Ubuntu. ZSH est très similaire mais il présente certains avantages par rapport à bash.

Zsh possède des fonctionnalités telles que la complétion interactive par tabulation, la recherche automatique de fichiers, l'intégration des expressions régulières, des raccourcis avancés pour définir la portée des commandes, et un moteur de thème riche.

Nous pouvons utiliser notre gestionnaire de paquets `apt` pour installer zsh sur notre système. Allons-y et exécutons `sudo apt install zsh` à partir de notre terminal bash. Je vais le faire depuis la console de la VM plutôt que d'être connecté via SSH.

Lorsque la commande d'installation est terminée, vous pouvez exécuter `zsh` dans votre terminal, cela démarrera ensuite un script de configuration de shell.

![](Images/Day20_Linux4.png)

J'ai sélectionné `1` pour la question ci-dessus et maintenant nous avons plus d'options.

![](Images/Day20_Linux5.png)

Vous pouvez voir à partir de ce menu que nous pouvons apporter quelques modifications dès la sortie de la boîte pour configurer ZSH selon nos besoins.

Si vous quittez l'assistant avec un `0` puis utilisez `ls -al | grep .zshrc`, vous devriez voir que nous avons un nouveau fichier de configuration.

Maintenant, nous voulons faire de zsh notre shell par défaut à chaque fois que nous ouvrons notre terminal. Nous pouvons le faire en exécutant la commande suivante pour changer notre shell `chsh -s $(which zsh)`. Ensuite, nous devons nous déconnecter et nous reconnecter pour que les modifications prennent effet.

Lorsque vous vous reconnectez et ouvrez un terminal, cela devrait ressembler à ceci. Nous pouvons également confirmer que notre shell a maintenant été changé en exécutant `which $SHELL`.

![](Images/Day20_Linux6.png)

En général, j'effectue cette étape sur chaque bureau Ubuntu que je lance et je trouve en général, sans aller plus loin, que le shell zsh est un peu plus rapide que bash.

### OhMyZSH

Ensuite, nous voulons améliorer un peu les choses et ajouter également quelques fonctionnalités pour nous aider à nous déplacer dans le terminal.

OhMyZSH est un framework gratuit et open source pour gérer votre configuration zsh. Il existe de nombreux plugins, thèmes et autres éléments qui rendent l'interaction avec le shell zsh beaucoup plus agréable.

Vous pouvez en savoir plus sur [ohmyzsh](https://ohmyz.sh/).

Installons Oh My ZSH. Nous avons quelques options avec `curl`, `wget` ou `fetch`, nous avons les deux premières disponibles sur notre système, mais je vais commencer avec `curl`.

`sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

Lorsque vous avez exécuté la commande ci-dessus, vous devriez voir une sortie similaire à celle ci-dessous.

![](Images/Day20_Linux7.png)

Maintenant, nous pouvons passer à l'étape suivante pour ajouter un thème à notre expérience. Il y en a bien plus de 100 inclus avec Oh My ZSH, mais mon choix pour toutes mes applications et tout le reste est le thème Dracula.

Je veux également ajouter que ces deux plugins sont indispensables lors de l'utilisation de Oh My ZSH.

`git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions`

`git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting`

`nano ~/.zshrc`

modifiez les plugins pour inclure maintenant `plugins=(git zsh-autosuggestions zsh-syntax-highlighting)`

## Extensions Gnome

J'utilise également des extensions Gnome, et en particulier la liste ci-dessous :

[Extensions Gnome](https://extensions.gnome.org)

    - Caffeine
    - CPU Power Manager
    - Dash to Dock
    - Desktop Icons
    - User Themes

## Installation de logiciels

Une courte liste des programmes que j'installe sur la machine en utilisant `apt` :

    - VSCode
    - azure-cli
    - containerd.io
    - docker
    - docker-ce
    - google-cloud-sdk
    - insomnia
    - packer
    - terminator
    - terraform
    - vagrant

### Thème Dracula

Ce site est le seul thème que j'utilise actuellement. Il a l'air clair et propre, et tout a l'air super. [Thème Dracula](https://draculatheme.com/). Il vous couvre également lorsque vous avez beaucoup d'autres programmes que vous utilisez sur votre machine.

À partir du lien ci-dessus, nous pouvons rechercher zsh sur le site et vous trouverez au moins deux options.

Suivez les instructions listées pour installer manuellement ou en utilisant git. Ensuite, vous devrez enfin modifier votre fichier de configuration `.zshrc` comme indiqué ci-dessous.

![](Images/Day20_Linux8.png)

Ensuite, vous voudrez le [thème Dracula pour Gnome Terminal](https://draculatheme.com/gnome-terminal) avec toutes les instructions disponibles ici également.

Il me faudrait beaucoup de temps pour documenter chaque étape, j'ai donc créé une vidéo expliquant le processus. (**Cliquez sur l'image ci-dessous**)

[![](Images/Day20_YouTube.png)](https://youtu.be/jeEslAtHfKc)

Si vous êtes arrivé jusqu'ici, nous avons maintenant terminé notre section Linux de #90DaysOfDevOps. Encore une fois, je suis ouvert aux commentaires et aux ajouts de ressources ici.

J'ai également pensé qu'il serait plus facile de vous montrer beaucoup des étapes à travers une vidéo plutôt que de les écrire ici. Qu'en pensez-vous ? J'ai pour objectif de revenir sur ces jours et, lorsque cela est possible, de créer des vidéos expliquant et montrant certaines des choses que nous avons couvertes. Qu'en pensez-vous ?

## Ressources

- [Bash en 100 secondes](https://www.youtube.com/watch?v=I4EWvMFj37g)
- [Script bash avec des exemples pratiques - Cours complet](https://www.youtube.com/watch?v=TPRSJbtfK4M)
- [Client SSH GUI - Remmina](https://remmina.org/)
- [Le guide du débutant pour SSH](https://www.youtube.com/watch?v=2QXkrLVsRmk)
- [Vim en 100 secondes](https://www.youtube.com/watch?v=-txKSRn0qeA)
- [Tutoriel Vim](https://www.youtube.com/watch?v=IiwGbcd8S7I)
- [Apprenez les fondamentaux de Linux - Partie 1](https://www.youtube.com/watch?v=kPylihJRG70)
- [Linux pour les hackers (ne vous inquiétez pas, vous n'avez pas besoin d'être un hacker !)](https://www.youtube.com/watch?v=VbEx7B_PTOE)

Demain, nous commençons nos 7 jours de plongée dans le réseau. Nous chercherons à nous donner les connaissances et la compréhension fondamentales du réseau autour de DevOps.

À demain pour le [Jour 21](day21.md)