## Vue d'ensemble : DevOps et Linux

Linux et DevOps partagent des cultures et des perspectives très similaires ; les deux sont axés sur la personnalisation et l'évolutivité. Ces deux aspects de Linux sont d'une importance particulière pour DevOps.

De nombreuses technologies commencent sur Linux, surtout si elles sont liées au développement de logiciels ou à la gestion de l'infrastructure.

De plus, de nombreux projets open source, en particulier les outils DevOps, ont été conçus pour fonctionner sur Linux dès le départ.

Du point de vue de DevOps ou de tout rôle opérationnel, vous allez rencontrer Linux, je dirais la plupart du temps. Il y a une place pour WinOps, mais la majorité du temps, vous allez administrer et déployer des serveurs Linux.

J'utilise Linux quotidiennement depuis plusieurs années, mais ma machine de bureau de prédilection a toujours été soit macOS soit Windows. Cependant, lorsque je suis passé au rôle Cloud Native que j'occupe actuellement, j'ai décidé de faire le grand saut et de m'assurer que mon ordinateur portable était entièrement basé sur Linux et mon pilote quotidien. Bien que j'aie toujours besoin de Windows pour les applications basées sur le travail et que beaucoup de mon matériel audio et vidéo ne fonctionne pas sous Linux, je me suis forcé à utiliser un bureau Linux à plein temps pour mieux comprendre beaucoup des choses que nous allons aborder au cours des 7 prochains jours.

## Commencer

Je ne suggère pas que vous fassiez la même chose que moi, loin de là, car il existe des options plus faciles et moins destructrices, mais je dirais que faire ce pas à plein temps vous force à apprendre plus rapidement comment faire fonctionner les choses sous Linux.

Pour la majorité de ces 7 jours, je vais déployer une machine virtuelle dans Virtual Box sur ma machine Windows. Je vais également déployer une version de bureau d'une distribution Linux, alors que la plupart des serveurs Linux que vous allez administrer seront probablement des serveurs sans interface graphique et tout sera basé sur le shell. Cependant, comme je l'ai dit au début, beaucoup des outils que nous avons couverts tout au long de ces 90 jours ont commencé sur Linux. Je vous encourage donc fortement à vous plonger également dans l'expérience d'apprentissage de ce bureau Linux.

Pour le reste de cet article, nous allons nous concentrer sur la mise en place et l'exécution d'une machine virtuelle Ubuntu Desktop dans notre environnement Virtual Box. Nous pourrions simplement télécharger [Virtual Box](https://www.virtualbox.org/) et obtenir la dernière [ISO Ubuntu](https://ubuntu.com/download) à partir des sites liés et continuer à construire notre environnement de bureau, mais cela ne serait pas très DevOps de notre part, n'est-ce pas ?

Une autre bonne raison d'utiliser la plupart des distributions Linux est qu'elles sont gratuites et open source. Nous choisissons également Ubuntu car c'est probablement la distribution la plus largement utilisée déployée, sans penser aux appareils mobiles et aux serveurs RedHat Enterprise. Je pourrais me tromper, mais avec CentOS et l'histoire qui s'y rattache, je parie qu'Ubuntu est en haut de la liste et c'est super simple.

## Présentation de HashiCorp Vagrant

Vagrant est un utilitaire en ligne de commande qui gère le cycle de vie de vos machines virtuelles. Nous pouvons utiliser Vagrant pour démarrer et arrêter des machines virtuelles sur de nombreuses plateformes différentes, y compris vSphere, Hyper-V, Virtual Box et également Docker. Il dispose d'autres fournisseurs, mais nous allons nous en tenir à Virtual Box ici pour que nous soyons prêts à partir.

La première chose que nous devons faire est d'installer Vagrant sur notre machine. Lorsque vous allez sur la page de téléchargements, vous verrez tous les systèmes d'exploitation répertoriés pour votre choix. [HashiCorp Vagrant](https://www.vagrantup.com/downloads) J'utilise Windows, donc j'ai pris le binaire pour mon système et je suis allé de l'avant et j'ai installé ceci sur mon système.

Ensuite, nous devons également installer [Virtual Box](https://www.virtualbox.org/wiki/Downloads). Encore une fois, cela peut également être installé sur de nombreux systèmes d'exploitation différents, et une bonne raison de choisir ceci et Vagrant est que si vous exécutez Windows, macOS ou Linux, nous vous avons couvert ici.

Les deux installations sont assez simples et les deux ont de grandes communautés autour d'elles, donc n'hésitez pas à les contacter si vous avez des problèmes et je peux également essayer de vous aider.

> Si vous utilisez m1 macOS, je vous recommande d'utiliser [multiplass](https://multipass.run/) au lieu de Vagrant et VirtualBox. (référence : https://github.com/MichaelCade/90DaysOfDevOps/issues/365)

## Notre premier VAGRANTFILE

Le VAGRANTFILE décrit le type de machine que nous voulons déployer. Il définit également la configuration et l'approvisionnement de cette machine.

Lorsqu'il s'agit de sauvegarder ces fichiers et d'organiser vos VAGRANTFILES, j'ai tendance à les mettre dans leurs dossiers dans mon espace de travail. Vous pouvez voir ci-dessous à quoi cela ressemble sur mon système. Espérons que vous jouerez avec Vagrant et verrez la facilité de démarrer différents systèmes. C'est aussi génial pour ce terrier connu sous le nom de saut de distribution pour les bureaux Linux.

![](Images/Day14_Linux1.png)

Jetons un coup d'œil à ce VAGRANTFILE et voyons ce que nous construisons.

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "chenhan/ubuntu-desktop-20.04"
  config.vm.provider :virtualbox do |v|
    v.memory  = 8096
    v.cpus    = 4
    v.customize ["modifyvm", :id, "--vram", "128"]
  end
end
```

C'est un VAGRANTFILE très simple dans l'ensemble. Nous disons que nous voulons une "box" spécifique, une box étant éventuellement une image publique ou une version privée du système que vous recherchez. Vous pouvez trouver une longue liste de "boxes" publiquement disponibles ici dans le [catalogue public des boxes Vagrant](https://app.vagrantup.com/boxes/search).

À la ligne suivante, nous disons que nous voulons utiliser un fournisseur spécifique et dans ce cas, c'est `VirtualBox`. Nous définissons également la mémoire de notre machine à `8 Go` et le nombre de CPU à `4`. Mon expérience me dit que vous voudrez peut-être également ajouter la ligne suivante si vous rencontrez des problèmes d'affichage. Cela définira la mémoire vidéo sur ce que vous souhaitez, je monterais cela directement à `128 Mo`, mais cela dépend de votre système.

```ruby
v.customize ["modifyvm", :id, "--vram", ""]
```

J'ai également placé une copie de ce fichier Vagrant spécifique dans le [dossier Linux](Linux/VAGRANTFILE).

## Approvisionnement de notre bureau Linux

Nous sommes maintenant prêts à faire fonctionner notre première machine, dans le terminal de notre poste de travail. Dans mon cas, j'utilise PowerShell sur ma machine Windows. Accédez à votre dossier de projets et là où vous trouverez votre VAGRANTFILE. Une fois là-bas, vous pouvez taper la commande `vagrant up` et si tout va bien, vous verrez quelque chose comme ceci.

![](Images/Day14_Linux2.png)

Une autre chose à ajouter ici est que le réseau sera défini sur `NAT` sur votre machine virtuelle. À ce stade, nous n'avons pas besoin de connaître le NAT et je prévois d'avoir une session entière pour en parler dans la session de mise en réseau. Sachez que c'est le bouton facile lorsqu'il s'agit de mettre une machine sur votre réseau domestique, c'est également le mode de mise en réseau par défaut sur Virtual Box. Vous pouvez en savoir plus dans la [documentation de Virtual Box](https://www.virtualbox.org/manual/ch06.html#network_nat).

Une fois `vagrant up` terminé, nous pouvons maintenant utiliser `vagrant ssh` pour passer directement au terminal de notre nouvelle VM.

![](Images/Day14_Linux3.png)

C'est ici que nous allons faire la plupart de nos explorations au cours des prochains jours, mais je veux également me plonger dans certaines personnalisations pour votre poste de travail de développeur que j'ai faites et qui rendent votre vie beaucoup plus simple lorsque vous l'exécutez comme votre pilote quotidien, et bien sûr, êtes-vous vraiment dans DevOps à moins d'avoir un terminal cool non standard ?

Mais juste pour confirmer dans Virtual Box, vous devriez voir l'invite de connexion lorsque vous sélectionnez votre VM.

![](Images/Day14_Linux4.png)

Oh, et si vous êtes arrivé jusqu'ici et que vous vous êtes demandé "QUEL EST LE NOM D'UTILISATEUR ET LE MOT DE PASSE ?",

- Nom d'utilisateur = vagrant
- Mot de passe = vagrant

Demain, nous allons nous pencher sur certaines des commandes et ce qu'elles font. Le terminal sera l'endroit où tout se passera.

## Ressources

- [Apprenez les fondamentaux de Linux - Partie 1](https://www.youtube.com/watch?v=kPylihJRG70)
- [Linux pour les hackers (ne vous inquiétez pas, vous n'avez pas besoin d'être un hacker !)](https://www.youtube.com/watch?v=VbEx7B_PTOE)

Il y aura beaucoup de ressources que je trouverai au fur et à mesure que nous avancerons, et tout comme les ressources Go, je vais généralement les garder gratuites afin que nous puissions tous participer et apprendre ici.

Comme je l'ai mentionné, nous allons ensuite examiner les commandes que nous pourrions utiliser quotidiennement dans nos environnements Linux.

À bientôt sur [Jour 15](day15.md).