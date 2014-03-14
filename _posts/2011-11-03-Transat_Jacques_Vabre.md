---
layout: posts
title: "Transat Jacques Vabre cartographiée sans flash"
categories:
- fr
- voile
- python
---

La transat Jacques Vabre est partie hier. Pour voir où sont les voiliers, le site propose uniquement une application flash. J'ai commis un petit script qui fabrique des cartes sur lesquelles sont reportées les positions des bateaux :
[programme smap](https://bitbucket.org/manu/vg/overview)

La commande

    ./smap.py -c class40 jacquesvabre.py

produit une carte comme 

[<img src="/images/jv.jpg">](http://velsheda.lateralis.org/cartes/choc_11_2009-11-07_09.jpg)

À l'origine, j'avais écrit ce programme pour le Vendée Globe 2008-2009. Je l'ai rendu plus générique pour suivre d'autres courses depuis (Barcelona World Race, St Gilles Croix de Vie - Saint Petersbourg - Saint Gilles, la route du rhum, la route du chocolat...)
