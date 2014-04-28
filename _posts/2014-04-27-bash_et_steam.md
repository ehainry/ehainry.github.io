---
layout: posts
title: "Steam sous debian plantait"
date: 2014-04-27 20:34:00+02:00
categories:
- linux
- jeux
---

Depuis quelques jours, Steam (bibliothèque et vendeur de jeux) se plaignait au lancement de l'absence de `libc.so.6`, ce qui est quand même assez inquiêtant, mais se lançait quand même.
Par contre, un certain nombre de jeux ne démarraient plus du tout, d'autres par contre continuaient de tourner normalement.

A priori ce message d'erreur se produit sur les architectures 64 bits n'ayant pas installé les bibliothèques 32bits, ce qui n'est pas mon cas.
En pratique, il est affiché dès que ldd renvoie un message d'erreur pour une des bibliothèques de steam.
Ce n'est donc pas le bon message d'erreur.
En lançant ldd avec les mêmes paramètres (c'est-à-dire avec la variable `LD_LIBRARY_PATH` contenant les chemins vers les bibliothèques steam), le vrai message d'erreur était

    bash: symbol lookup error: /lib/i386-linux-gnu/libncurses.so.5: undefined symbol: _nc_putchar

Message lui aussi étonnant puisque bash n'est pas le shell que j'utilise.
J'ai ainsi appris que `ldd` était un script shell et que le bash d'une debian testing utilisait une version de ncurses différente de celle de steam...

Le correctif a simplement consisté à installer `bash-static` (qui comme son nom l'indique n'utilise pas de bibliothèque partagées) et changer les premières lignes des scripts shell lançant les jeux en remplaçant `#!/bin/bash` par `#!/bin/bash-static`...
Et tous les jeux se lancent de nouveau.

Je me demande par contre s'il ne serait pas plus futé de la part de Debian de ne mettre que des programmes statiques dans `/bin` comme le fait, je crois, netBSD, ce qui aurait permis d'éviter ce petit désagrément et limiterait le risque qu'une mise à jour d'une bibliothèque casse un utilitaire indispensable.
