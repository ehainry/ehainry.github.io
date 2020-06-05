---
layout: posts
title: "Suivi de mes parcours à vélo"
categories:
- fr
---

Parmi mes résolutions 2019 et 2020, il y avait celle de faire plus de vélo (en 2019, je m'étais fixé comme objectif de faire 500km et en 2020 de faire 1000km). Je fais régulièrement des petites sorties d'autour d'une heure et je conserve une trace GPS et reporte les distances parcourues dans un carnet.

![page de carnet](/images/IMG_20190818_202641.jpg)

Et même si j'aime cette version analogique, je voulais en avoir une trace numérique.
Pour cela, pourquoi ne pas utiliser le logiciel avec lequel je fais mes comptes ?
J'utilise [hledger](hledger.org) pour cela.
Il s'agit d'un logiciel de comptabilité à double entrée qui travaille sur des fichiers textes.
Une transaction comporte une date, un titre, et une liste de comptes et les valeurs que la transaction ajouté ou retiré à ce compte.
Pour mes trajets à vélo, je fais des transactions comme la suivante :

    2019/08/15 Les Sables d'Olonne
        Distance    18km
        Temps       55min
        Velo:Riverside

Le titre représente les lieux visités, les comptes sont "Distance", "Temps" et "Velo:Riverside" qui indique avec quel vélo j'ai roulé.
Ensuite, je peux consulter avec un navigateur grace à ''hledger-web'' les informations.
Je vois alors sensiblement les mêmes choses que sur mon carnet, plus un graphe :

![Screenshot_hledger](/images/Screenshot_20190818-203907.png)

![Graphe hledger web](/images/Screenshot_20190818-203508.png)

Et via la ligne de commande, je peux constater les "performances" par mois et par vélo par exemple :

    $ hledger bal -M Velo
    Balance changes in 2019/03/01-2019/11/30:

                    ||        2019/03        2019/04        2019/05         2019/06         2019/07         2019/08         2019/09  2019/10       2019/11 
    ================++=====================================================================================================================================
     Velo:Mongoose  || -65km, -250min  -15km, -55min -86km, -320min -159km, -535min  -43km, -140min  -56km, -165min -139km, -430min        0 -21km, -70min 
     Velo:Poulidor  ||              0              0              0               0               0   -10km, -35min               0        0             0 
     Velo:Riverside ||              0 -29km, -100min              0               0 -126km, -410min -159km, -510min               0        0             0 
    ----------------++-------------------------------------------------------------------------------------------------------------------------------------
                    || -65km, -250min -44km, -155min -86km, -320min -159km, -535min -169km, -550min -225km, -710min -139km, -430min        0 -21km, -70min 

