---
layout: posts
title: "Deux bugs et un contournement pour mon cybook"
date: 2012-10-10 18:00
categories:
- fr
- cybook
---

Depuis quelques temps je rencontrais deux "bugs" sur mon livre cybook orizon qui se corrigeaient parfois tout seul. J'ai maintenant compris pourquoi cela arrivait et trouvé un moyen de contourner le bug.

## Les bugs

1. D'une part quand j'ajoute un nouveau livre à ma bibliothèque, le redémarrage prend un peu de temps (pour fabriquer une vignette de la couverture). C'est parfaitement normal. Mais, ça ne devrait arriver qu'une fois, or récemment, ça se produisait à chaque allumage (après extinction, pas après mise en veille). Et le temps était loin d'être négligeable, ce qui rendait la chose fort désagréable.
2. L'écran d'accueil montre normalement les cinq derniers livres lus. Mais de temps en temps, il montre le livre que je lis à ce moment et quatre livres qui ne changent plus. Mais ça se corrigeait parfois tout seul avant de recommencer.

## La cause

Quand la batterie s'épuise, la date revient en 2010. Ce qui fait que les vignettes sont plus vieilles que les livres (donc la liseuse pense que le fichier a été mis à jour et qu'il faut donc refabriquer la vignette). Et pour les livres récents, même chose, le deuxième livre le plus récent que j'ai lu date d'avant ceux où la liseuse a perdu la date.

## Contournement

Deux possibilités : soit connecter le livre par wifi, ce qui va le remettre à l'heure. Soit à la main en ajoutant dans le dossier ``system`` un fichier rtc.dat contenant la date et l'heure au bon format : la [procédure est parfaitement expliquée sur mobileread](http://www.mobileread.com/forums/showpost.php?p=168344&postcount=1).

## Conclusion

Deux bugs compris et contournés (à défaut de corrigés). Je suis content.
