---
layout: posts
title: "Améliorations pour mes cartes du Vendée Globe"
categories:
- fr
- voile
- cartographie
- javascript
- vendee globe
---

J'ai [donc](/2012/11-10/Vendee_Globe.html) réalisé des programmes pour
voir les positions des bateaux du Vendée Globe. Trois versions
[statique](/images/vg_carte.jpg), [dynamique nokia](/vg/nokia.html) et
[dynamique leaflet](/vgjs/leaflet.html) qui donnent respectivement des choses
ressemblant à

![statique mini](/images/vg_vi.jpg)

![dynamique nokia](/images/nokia.jpg)

![dynamique leaflet](/images/leaflet.jpg)

J'ai plusieurs idées de modifications et améliorations mais je ne sais
pas encore trop comment les réaliser ou si ce serait vraiment intéressant.

1. **Affichage des force et direction du vent.** Il devrait être possible
   d'inclure les forces des vents pour deviner par exemple l'anticyclone de Ste
   Hélène. Je pourrais par exemple utiliser les données [GRIB](http://grib.us)
   mais ce n'est pas très facile à traiter et il n'existe pas à ma connaissance
   de bibliothèque javascript pour le vent.

2. **Affichage des points de passage obligés.** Dans quelques jours, les
   navigateurs devront laisser à tribord l'île Gough, puis ils devront passer
   dans la porte atlantique, c'est-à-dire passer entre deux points donnés.
   Comment les représenter ? Une épingle d'une couleur spéciale pour le point à
   laisser à tribord ? un trait pour la porte ?

3. **Calcul de distances orthodromiques.** Ce serait intéressant de pouvoir
   calculer la distance entre deux bateaux ou la distance à un point donné sur
   la carte. Par exemple comme le permet l'outil règle des [cartes
   nokia](http://here.net/).

4. **Zoom sur un groupe donné de bateaux.** En ce moment, il est possible dans
   les versions javascript de zoomer sur *les cinq premiers* ou *toute la
   flotte* ou *toute la flotte + Les Sables d'Olonne*. Comme des groupes se
   sont formés, il pourrait être intéressant de zoomer sur un groupe de bateaux
   particulier, par exemple *Akena*, *Acciona*, *Initiatives Cœur* et *Votre
   nom autour du monde*. Malheureusement, cela nécessite une interface plus
   évoluée que des boutons (par exemple des sliders définissant un min et un
   max).
