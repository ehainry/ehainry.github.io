---
layout: postsen
title: "Games libraries"
categories:
- en
- linux
- games
---

Gaming on Linux was once a desolated land containing only small open source games and one or two gems ([Battle for Wesnoth](http://www.wesnoth.org/) for example).
However, this is no longer the case essentially since 2010 and the first [Humble indie bundle](http://en.wikipedia.org/wiki/Humble_Bundle#Humble_Indie_Bundle), and more recently with steam coming to linux, many games comming along and steam even announcing future gaming machines running Linux as their primary OS.

Apart from that, there are also ways to get old games to play under Linux (and other OSes) through the reimplementation of their engine.
For example, if you have the files for *Broken Sword*, you can play it under Linux using Scummvm.
[Scummvm](http://www.scummvm.org) in fact contains engines to run dozens of adventure games from the 90s such as Broken Sword, Day of the Tentacle, Monkey Island, Indiana Jones and the Fate of Atlantis, Space Quest, Kyrandia...
Other new engines for old games include [FreeSynd](http://freesynd.sourceforge.net/) for playing Syndicate, [REminiscence](http://cyxdown.free.fr/reminiscence/) for playing Flashback, or [rott](http://icculus.org/rott/) to play Rise of the Triad.
Wikipedia has [a list for this](https://en.wikipedia.org/wiki/Game_engine_recreation).

And then, there are wine and dosbos.
[wine](http://winehq.com) allows you to launch windows programs, including games, under Linux.
[dosbox](http://www.dosbox.com/) does the same for dos games.
The performance in both cases is however not spectacular.

And with all those games, most of them not coming through the package manager, there is a need for organisation and simple installing.
Steam and Desura are doing it, through their somewhat bloated client.
The Open Source [Lutris](http://lutris.net/) also promises this but, I cannot grasp how to use it.
The installation of games part is on par with the experience on other OSes, not as great as using the package manager (apt-get/synaptic), but reasonably simple.
Concerning the organisation need, it should already be filled by the native support for *desktop-files*.
Indeed, executable programs usually install a small file with the extension ``.desktop`` that associates a legend and an icon to the launch command.
Then the Desktop Manager knows how to treat those files, for example in gnome, pressing the Meta key (also called Windows key) brings a menu in which it is possible to launch programs, even to display all those from a given category (say Games)...

And *desktop-files* are not difficult to write by oneself.
For example, the following is a complete desktop file:

    [Desktop Entry]
    Name=Gobliins 2
    Exec=scummvm -n -p /home/manu/.local/share/scummvm/gobliins2 gob2cd-fr
    Type=Application
    Icon=gobliiins
    Categories=Game;

For DEs to find those files and their icons, they need to be in specific locations: desktop files can be put in `~/.local/share/applications/` and icons in `~/.local/share/icons/` for example.

When not using Desktop Environments, it can be more difficult, but launchers such as [kupfer](http://engla.github.io/kupfer/) understand them, and there usually exist scripts to generate a menu for your desktop entries: for example a [pipemenu for openbox](http://openbox.org/wiki/Openbox:Pipemenus:obam); I did a similar program in lua for awesome, which I could share.
