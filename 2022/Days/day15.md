## Commandes Linux pour DevOps (En fait, pour tout le monde)

J'ai mentionné [hier](day14.md) que nous allions passer beaucoup de temps dans le terminal avec certaines commandes pour accomplir des tâches.

J'ai également mentionné qu'avec notre VM provisionnée par Vagrant, nous pouvons utiliser `vagrant ssh` et accéder à notre boîte. Vous devrez être dans le même répertoire que celui à partir duquel nous l'avons provisionné.

Pour SSH, vous n'aurez pas besoin du nom d'utilisateur et du mot de passe, vous n'en aurez besoin que si vous décidez de vous connecter à la console Virtual Box.

C'est ici que nous voulons être, comme indiqué ci-dessous :

![](Images/Day15_Linux1.png)

## Commandes

Je ne peux pas couvrir toutes les commandes ici, il y a des pages et des pages de documentation qui les couvrent, mais aussi si vous êtes un jour dans votre terminal et que vous avez juste besoin de comprendre les options d'une commande spécifique, nous avons les pages `man` pour manual. Nous pouvons les utiliser pour parcourir chacune des commandes que nous abordons dans ce post pour trouver plus d'options pour chacune d'elles. Nous pouvons exécuter `man man` qui vous donnera de l'aide pour les pages de manuel. Pour quitter les pages de manuel, vous devez appuyer sur `q` pour quitter.

![](Images/Day15_Linux2.png)
![](Images/Day15_Linux3.png)

`sudo` Si vous êtes familier avec Windows et le clic droit `exécuter en tant qu'administrateur`, nous pouvons considérer `sudo` comme très similaire. Lorsque vous exécutez une commande avec cette commande, vous l'exécuterez en tant que `root`, elle vous demandera le mot de passe avant d'exécuter la commande.

![](Images/Day15_Linux4.png)

Pour des tâches ponctuelles comme l'installation d'applications ou de services, vous pourriez avoir besoin de cette `commande sudo`, mais que faire si vous avez plusieurs tâches à gérer et que vous voulez vivre en tant que `sudo` pendant un moment ? C'est là que vous pouvez utiliser `sudo su`, de la même manière que `sudo`, une fois entré, vous serez invité à entrer votre mot de passe `root`. Dans une VM de test comme la nôtre, c'est bien, mais je trouverais très difficile de rester en tant que `root` pendant des périodes prolongées, des choses mauvaises peuvent arriver. Pour sortir de cette position élevée, vous tapez simplement `exit`.

![](Images/Day15_Linux5.png)

Je me surprends à utiliser `clear` tout le temps, la commande `clear` fait exactement ce qu'elle dit, elle efface l'écran de toutes les commandes précédentes, mettant votre prompt en haut et vous donnant un espace de travail propre. Sur Windows, je pense que c'est `cls` dans le .mdprompt.

![](Images/Day15_Linux6.png)

Examinons maintenant quelques commandes où nous pouvons réellement créer des choses dans notre système et ensuite les visualiser dans notre terminal. Tout d'abord, nous avons `mkdir` qui nous permettra de créer un dossier dans notre système. Avec la commande suivante, nous pouvons créer un dossier dans notre répertoire personnel appelé Day15 `mkdir Day15`.

![](Images/Day15_Linux7.png)

Avec `cd`, cela nous permet de changer de répertoire, donc pour nous déplacer dans notre répertoire nouvellement créé, nous pouvons le faire avec `cd Day15`, la touche tab peut également être utilisée pour compléter automatiquement le répertoire disponible. Si nous voulons revenir à l'endroit où nous avons commencé, nous pouvons utiliser `cd ..`.

![](Images/Day15_Linux8.png)

`rmdir` nous permet de supprimer le répertoire, si nous exécutons `rmdir Day15`, alors le dossier sera supprimé (note : cela ne fonctionnera que si vous n'avez rien dans le dossier).

![](Images/Day15_Linux9.png)

Je suis sûr que nous l'avons tous fait où nous avons navigué dans les profondeurs de notre système de fichiers vers un répertoire et que nous ne savions pas où nous étions. `pwd` nous donne l'impression du répertoire de travail, pwd autant que cela ressemble à un mot de passe, cela signifie print working directory.

![](Images/Day15_Linux10.png)

Nous savons comment créer des dossiers et des répertoires, mais comment créons-nous des fichiers ? Nous pouvons créer des fichiers en utilisant la commande `touch`, si nous exécutions `touch Day15`, cela créerait un fichier. Ignorez `mkdir`, nous allons le revoir plus tard.

![](Images/Day15_Linux11.png)

`ls` Je peux parier ma maison dessus, vous utiliserez cette commande tellement de fois, cela va lister tous les fichiers et dossiers dans le répertoire actuel. Voyons si nous pouvons voir ce fichier que nous venons de créer.

![](Images/Day15_Linux12.png)

Comment pouvons-nous trouver des fichiers sur notre système Linux ? `locate` va nous permettre de rechercher dans notre système de fichiers. Si nous utilisons `locate Day15`, il rapportera l'emplacement du fichier. Le bonus est que si vous savez que le fichier existe mais que vous obtenez un résultat vide, alors exécutez `sudo updatedb` qui indexera tous les fichiers dans le système de fichiers, puis exécutez votre `locate` à nouveau. Si vous n'avez pas `locate` disponible, vous pouvez l'installer en utilisant cette commande `sudo apt install mlocate`.

![](Images/Day15_Linux13.png)

Et pour déplacer des fichiers d'un emplacement à un autre ? `mv` va nous permettre de déplacer vos fichiers. Exemple `mv Day15 90DaysOfDevOps` déplacera votre fichier vers le dossier 90DaysOfDevOps.

![](Images/Day15_Linux14.png)

Nous avons déplacé notre fichier, mais que faire si nous voulons maintenant le renommer en autre chose ? Nous pouvons le faire en utilisant à nouveau la commande `mv`... WOT!!!? oui, nous pouvons simplement utiliser `mv Day15 day15` pour changer en majuscule ou nous pourrions utiliser `mv day15 AnotherDay` pour le changer complètement, maintenant utilisez `ls` pour vérifier le fichier.

![](Images/Day15_Linux15.png)

Assez, c'est assez, débarrassons-nous (supprimons) de notre fichier et peut-être même de notre répertoire si nous en avons créé un. `rm` simplement `rm AnotherDay` supprimera notre fichier. Nous utiliserons également beaucoup `rm -R` qui fonctionnera de manière récursive à travers un dossier ou un emplacement. Nous pourrions également utiliser `rm -R -f` pour forcer la suppression de tous ces fichiers. Spoiler : si vous exécutez `rm -R -f /` ajoutez sudo et vous pouvez dire au revoir à votre système....!

![](Images/Day15_Linux16.png)

Nous avons vu comment déplacer des fichiers, mais que faire si je veux juste copier des fichiers d'un dossier à un autre, tout simplement c'est très similaire à la commande `mv` mais nous utilisons `cp` donc nous pouvons maintenant dire `cp Day15 Desktop`.

![](Images/Day15_Linux17.png)

Nous avons créé des dossiers et des fichiers, mais nous n'avons mis aucun contenu dans notre dossier, nous pouvons ajouter du contenu de plusieurs façons, mais une façon facile est `echo`, nous pouvons également utiliser `echo` pour imprimer beaucoup de choses dans notre terminal, j'utilise echo beaucoup pour imprimer des variables système pour savoir si elles sont définies ou non au moins. nous pouvons utiliser `echo "Hello #90DaysOfDevOps" > Day15` et cela ajoutera cela à notre fichier. Nous pouvons également ajouter à notre fichier en utilisant `echo "Commands are fun!" >> Day15`.

![](Images/Day15_Linux18.png)

Une autre de ces commandes que vous utiliserez beaucoup ! `cat` pour concaténer. Nous pouvons utiliser `cat Day15` pour voir le contenu à l'intérieur du fichier. Génial pour lire rapidement ces fichiers de configuration.

![](Images/Day15_Linux19.png)

Si vous avez un fichier de configuration long et complexe et que vous voulez ou avez besoin de trouver quelque chose rapidement dans ce fichier plutôt que de lire chaque ligne, alors `grep` est votre ami, cela nous permettra de rechercher dans votre fichier un mot spécifique en utilisant `cat Day15 | grep "#90DaysOfDevOps"`.

![](Images/Day15_Linux20.png)

Si vous êtes comme moi et que vous utilisez beaucoup cette commande `clear`, vous pourriez manquer certaines des commandes exécutées précédemment, nous pouvons utiliser `history` pour découvrir toutes ces commandes que nous avons exécutées auparavant. `history -c` supprimera l'historique.

Lorsque vous exécutez `history` et que vous souhaitez choisir une commande spécifique, vous pouvez utiliser `!3` pour choisir la 3ème commande de la liste.

Vous pouvez également utiliser `history | grep "Command"` pour rechercher quelque chose de spécifique.

Sur les serveurs pour retracer quand une commande a été exécutée, il peut être utile d'ajouter la date et l'heure à chaque commande dans le fichier d'historique.

La variable système suivante contrôle ce comportement :

```
HISTTIMEFORMAT="%d-%m-%Y %T "
```

Vous pouvez facilement l'ajouter à votre bash_profile :

```
echo 'export HISTTIMEFORMAT="%d-%m-%Y %T "' >> ~/.bash_profile
```

Ainsi, il est utile de permettre au fichier d'historique de devenir plus grand :

```
echo 'export HISTSIZE=100000' >> ~/.bash_profile
echo 'export HISTFILESIZE=10000000' >> ~/.bash_profile
```

![](Images/Day15_Linux21.png)

Besoin de changer votre mot de passe ? `passwd` va nous permettre de changer notre mot de passe. Notez que lorsque vous ajoutez votre mot de passe comme ceci lorsqu'il est caché, il ne sera pas affiché dans `history`, cependant, si votre commande a `-p PASSWORD`, alors cela sera visible dans votre `history`.

![](Images/Day15_Linux22.png)

Nous pourrions également vouloir ajouter de nouveaux utilisateurs à notre système, nous pouvons le faire avec `useradd`, nous devons ajouter l'utilisateur en utilisant notre commande `sudo`, nous pouvons ajouter un nouvel utilisateur avec `sudo useradd NewUser`.

![](Images/Day15_Linux23.png)

Créer un groupe nécessite à nouveau `sudo` et nous pouvons utiliser `sudo groupadd DevOps`, puis si nous voulons ajouter notre nouvel utilisateur à ce groupe, nous pouvons le faire en exécutant `sudo usermod -a -G DevOps`, `-a` est ajouter et `-G` est le nom du groupe.

![](Images/Day15_Linux24.png)

Comment ajoutons-nous des utilisateurs au groupe `sudo` ? Ce serait une occasion très rare pour que cela se produise, mais pour le faire, ce serait `usermod -a -G sudo NewUser`.

### Permissions

lire, écrire et exécuter sont les permissions que nous avons sur tous nos fichiers et dossiers sur notre système Linux.

Une liste complète :

- 0 = Aucune `---`
- 1 = Exécuter uniquement `--X`
- 2 = Écrire uniquement `-W-`
- 3 = Écrire et exécuter `-WX`
- 4 = Lire uniquement `R--`
- 5 = Lire et exécuter `R-X`
- 6 = Lire et écrire `RW-`
- 7 = Lire, écrire et exécuter `RWX`

Vous verrez également `777` ou `775` et ceux-ci représentent les mêmes nombres que la liste ci-dessus, mais chacun représente **Utilisateur - Groupe - Tout le monde**.

Jetons un coup d'œil à notre fichier. `ls -al Day15` vous pouvez voir les 3 groupes mentionnés ci-dessus, l'utilisateur et le groupe ont lire et écrire mais tout le monde n'a que lire.

![](Images/Day15_Linux25.png)

Nous pouvons changer cela en utilisant `chmod`, vous pourriez vous retrouver à faire cela si vous créez beaucoup de binaires sur vos systèmes et que vous avez besoin de donner la capacité d'exécuter ces binaires. `chmod 750 Day15` maintenant exécutez `ls -al Day15` si vous voulez exécuter cela pour un dossier entier, alors vous pouvez utiliser `-R` pour le faire de manière récursive.

![](Images/Day15_Linux26.png)

Et pour changer le propriétaire du fichier ? Nous pouvons utiliser `chown` pour cette opération, si nous voulions changer la propriété de notre `Day15` de l'utilisateur `vagrant` à `NewUser`, nous pouvons exécuter `sudo chown NewUser Day15`, à nouveau `-R` peut être utilisé.

![](Images/Day15_Linux27.png)

Une commande que vous rencontrerez est `awk` qui est très utile lorsque vous avez une sortie dont vous n'avez besoin que de données spécifiques. comme exécuter `who`, nous obtenons des lignes avec des informations, mais peut-être que nous n'avons besoin que des noms. Nous pouvons exécuter `who | awk '{print $1}'` pour obtenir juste une liste de cette première colonne.

![](Images/Day15_Linux28.png)

Si vous cherchez à lire des flux de données à partir de l'entrée standard, puis générer et exécuter des lignes de commande ; cela signifie qu'il peut prendre la sortie d'une commande et la passer en argument d'une autre commande. `xargs` est un outil utile pour ce cas d'utilisation. Par exemple, si je veux une liste de tous les comptes utilisateurs Linux sur le système, je peux exécuter `cut -d: -f1 < /etc/passwd` et obtenir la longue liste que nous voyons ci-dessous.

![](Images/Day15_Linux29.png)

Si je veux compacter cette liste, je peux le faire en utilisant `xargs` dans une commande comme celle-ci `cut -d: -f1 < /etc/passwd | sort | xargs`.

![](Images/Day15_Linux30.png)

Je n'ai pas non plus mentionné la commande `cut`, cela nous permet de supprimer des sections de chaque ligne d'un fichier. Il peut être utilisé pour couper des parties d'une ligne par position d'octet, caractère et champ. La commande `cut -d " " -f 2 list.txt` nous permet de supprimer cette première lettre que nous avons et d'afficher simplement nos numéros. Il y a tellement de combinaisons qui peuvent être utilisées ici avec cette commande, je suis sûr que j'ai passé trop de temps à essayer d'utiliser cette commande alors que j'aurais pu extraire des données plus rapidement manuellement.

![](Images/Day15_Linux31.png)

Aussi à noter, si vous tapez une commande et que vous n'êtes plus satisfait de celle-ci et que vous voulez recommencer, appuyez simplement sur control + c et cela annulera cette ligne et vous redémarrera.

## Ressources

- [Apprenez les fondamentaux de Linux - Partie 1](https://www.youtube.com/watch?v=kPylihJRG70)
- [Linux pour les hackers (ne vous inquiétez pas, vous n'avez pas besoin d'être un hacker !)](https://www.youtube.com/watch?v=VbEx7B_PTOE)

À demain pour le [Jour 16](day16.md)

C'est déjà une liste assez lourde, mais je peux dire en toute sécurité que j'ai utilisé toutes ces commandes dans ma vie quotidienne, que ce soit pour administrer des serveurs Linux ou sur mon bureau Linux, il est très facile lorsque vous êtes sous Windows ou macOS de naviguer dans l'interface utilisateur, mais dans les serveurs Linux, ils ne sont pas là, tout se fait via le terminal.