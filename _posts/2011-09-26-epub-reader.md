---
layout: posts
title: "Lecteur d'epub"
categories:
- fr
- livres
- epub
---

Existe-t-il un logiciel de lecture des fichiers ePub sous linux qui soit complètement satisfaisant ? J'en ai essayé plusieurs mais je n'ai pas trouvé mon bonheur. Les concurrents : [epubreader], [lucidor], [ebook reader for opera], [aranduka], [calibre] et [FBReader].

### FBReader

[FBReader] explore un dossier et classe les livres contenus par auteur ou genre. Ensuite, il permet de lire le fichier plutôt pas mal. Malheureusement, il zappe beaucoup du style des fichiers. Ce pourrait être un avantage pour éviter les mises en page lourdes qui peuvent arriver à condition que la configuration de base soit excellente ou la configuration facile, ce n'est pas le cas.

Cependant, fbreader est le logiciel que je continue à utiliser pour regarder des livres.

### Calibre

[calibre] gère la bibliothèque, la synchronisation avec le livre électronique et la conversion entre différents formats de livres numériques. Il possède aussi un visualiseur simple. Et particulièrement mauvais : au changement de page, des lignes apparaissent à moitié ou parfois à la fois en dernière ligne d'une page et en première de la suivante. En plus, il est lent (il a même une animation lente, moche, inutile pour le changement de page). Bref, calibre n'est pas du tout la solution pour lire un ePub.

### Aranduka

Je ne sais pas tout ce qu'est censé faire [aranduka], mais c'est prometteur. Son lecteur d'epub fonctionne. Son défaut est qu'il ne sait pas faire la pagination (chaque chapitre est présentée comme une seule très longue page).

### Ebook reader for Opera

[ebook reader for opera] est un widget pour le navigateur Opera. Logique, il s'agit d'afficher du
html/xhtml, qui mieux qu'un navigateur pour faire ça ? Mais ce widget est
malcommode et ne gère pas la pagination.

### Lucidor

[lucidor] est à Firefox ce que Ebook Reader est à Opera. Défaut : pas de pagination.

### Okular

Le lecteur/éditeur de pdf de KDE, [okular] sait lire les epub. Je n'ai pas trouvé comment augmenter la taille de la police.

### Epubreader

Une extension pour firefox : [epubreader]. Sa bibliothèque n'est pas trop commode, mais niveau lecteur, il a l'air le plus abouti et agréable : il fait des pages, il comprend les styles mieux que fbreader, il permet d'outrepasser les thèmes du livre.

### bookworm

Cas à part, [bookworm](http://bookworm.oreilly.com/) est un lecteur d'epub en ligne. Il est [open source](http://code.google.com/p/threepress/) et peut donc être installé sur n'importe quel serveur. Bookworm ne gère pas la pagination.

### epubtopdf

Ça ne répond absolument pas à la problématique de départ mais ça peut être intéressant tout de même, je me suis fait un [script shell epubtopdf](https://bitbucket.org/manu/epubinfo/src/21c36398f143/epubtopdf.sh) qui dépend de wkhtmltopdf pour transformer du html en pdf et de pdfjam pour accoler les différents pdf produits. Certaines images ne passent pas (à cause d'un bug dans wkhtmltopdf). Je trouve le résultat plus joli que celui de calibre.

[epubreader]: https://addons.mozilla.org/en-US/firefox/addon/epubreader/
[lucidor]: http://www.lucidor.org/lucidor/
[ebook reader for opera]: http://widgets.opera.com/widget/15552/
[aranduka]: http://code.google.com/p/aranduka/
[okular]: http://okular.kde.org/
[calibre]: http://calibre-ebook.com/
[FBReader]: http://fbreader.org/
