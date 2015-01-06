---
layout: posts
title: "Jeux GOG sous Linux"
categories:
- jeux
---

[GOG](http://www.gog.com/), anciennement *Good Old Games* est une boutique en ligne de jeux vidéo.
Originellement spécialisée dans les vieux jeux, elle s'est récemment diversifiée en proposant de plus en plus de jeux indépendants récents.
Elle clame être opposée aux DRM (mesures techniques de protection ou MTP en français) et propose depuis peu des jeux linux.

Mais les jeux proposés pour linux ne sont pas les seuls jouables sous linux, en effet, la plupart des vieux jeux sont proposés pour windows avec une machine virtuelle telle que [scummvm] ou [dosbox] qui tournent parfaitement sous linux.
Même des jeux récents peuvent être exécutés de façon native sous linux sans émulateur windows (comme wine) !

Voici une marche à suivre pour quelques jeux.
Tout d'abord, les programmes que je cite par la suite :

* [lgogdownloader]
* [innoextract]
* [scummvm]
* [dosbox]
* [ags]

Hormis `ags`, ils sont tous disponibles dans les dépôts debian, donc ubuntu et autres dérivés.


## Téléchargeons un jeu

Je suppose avoir quelques jeux dans ma bibliothèque GOG.
*Beneath a Steel Sky* par exemple est gratuitement proposé à tout le monde (il est également disponible dans toutes les bonnes distributions linux).
S'il n'y a pas d'installeur linux, il faut télécharger l'installeur windows.
Cela peut être fait directement depuis le site.
On peut également utiliser [lgogdownloader].
Voici quelques lignes de commande typique :

    lgogdownloader --list-details --game beneath
    lgogdownloader --download --game beneath --no-extras

La première ligne liste les paquets pour les jeux dont le nom contient *beneath*.
La deuxième télécharge tous les paquets sauf les extras dans un dossier nommé comme le jeu.
On se retrouve alors avec un fichier `setup_nom_du_jeu_x.y.z.exe` avec `x.y.z` la version de l'installeur.

## Extrayons les données du jeu

Le fichier setup est un installeur innosetup.
Le programme [innoextract] sert à le décompresser.
Il suffit dans le dossier où a été téléchargé le fichier setup de lancer la commande

    innoextract setup_nom_du_jeu_x.y.z.exe

Si tout se passe bien[^1], on se retrouve avec un dossier `tmp` et un dossier `app`.
Le dossier `tmp` contient le programme d'installation proprement dit, il ne nous sert à rien, nous pouvons l'effacer.
Les données du jeu sont dans le dossier `app`.

## Jouons

Plaçons-nous maintenant dans le dossier `app`.

### scummvm

Si le jeu est supporté par scummvm, il faut trouver le nom du jeu pour scummvm dans la liste des jeux supportés donnée par

    scummvm -z

puis lancer le jeu, par exemple, pour *Beneath a Steel Sky* :

    scummvm -p . sky

Il est également possible de lancer `scummvm` sans argument et d'ajouter le jeu en donnant le chemin où sont les données.

### dosbox

Pour dosbox, il peut y avoir besoin de chercher le bon fichier de configuration (avec un nom de la forme `dosboxNomdujeuxxx.conf`), voire à le modifier avant de lancer

    dosbox -conf dosboxNomdujeuxxx.conf

### Adventure Game Studio

De nombreux [jeux Point n Click "modernes"](http://www.gog.com/games##sort=bestselling&devpub=wadjet_eye_games&page=1) sont réalisés avec [Adventure Game Studio](http://www.adventuregamestudio.co.uk/).
Ils passent en général bien sous wine, mais on peut souvent y jouer sans émulateur en installant l'interpréteur `ags`.
`ags` n'est pas empaqueté sous debian ou ubuntu, mais l'installer à la main est faisable :

On peut cloner le [dépôt git ags](https://github.com/adventuregamestudio/ags/) 
puis compiler en suivant la documentation :

    sudo apt-get install git debhelper build-essential pkg-config libaldmb1-dev libfreetype6-dev libtheora-dev libvorbis-dev libogg-dev
    git clone git://github.com/adventuregamestudio/ags.git
	cd ags
	fakeroot debian/rules binary

Il ne reste plus qu'à installer le paquet debian créé :

    sudo dpkg -i ../ags_3.3.2.0-1_i386.deb

Pour lancer un jeu, il suffit de retourner dans le dossier `app` obtenu précédemment (que l'on peut renommer bien sur) et de lancer ags:

    cd .../nomdujeu/app/
    ags

On peut modifier le fichier acsetup.cfg pour changer certaines options (choix fenêtre/plein écran par exemple). [Voici une explication en allemand des paramètres du fichier acsetup.cfg](http://wiki.ubuntuusers.de/Adventure_Game_Studio?redirect=no#acsetup-cfg).

Notons que ce n'est pas spécifique à gog.
Les jeux ags disponibles ailleurs peuvent également être lancés ainsi s'ils n'utilisent pas de bibliothèques spécifiques.

    




[scummvm]: http://www.scummvm.org/
[dosbox]: http://www.dosbox.com/
[lgogdownloader]: https://sites.google.com/site/gogdownloader/
[innoextract]: http://constexpr.org/innoextract/
[ags]: https://github.com/adventuregamestudio/ags/
[^1]: Malheureusement, depuis peu, les choses pourraient mal se passer puisque gog chiffre certains installeurs qui ne sont donc plus utilisables <https://www.gog.com/forum/general/on_gnulinux_has_anyone_be_able_to_extract_the_rar_innosetup_installers/post116>. Et tant pis pour le refus des mesures techniques de protection...
