---
layout: posts
title: "Écrire simplement un ePub"
categories:
- fr
- ebook
- epub
---

Dans un précédent article, j'ai prétendu expliquer [comment créer un epub](/journal/2011/05-27/Ecrire_en_epub.html) mais ai surtout parlé de ce qu'est un fichier epub. Aujourd'hui, comment écrire un tel fichier depuis zéro.

Comment écrit-on un texte sur un ordinateur ? Il y a deux écoles : d'une part le logiciel de traitement de texte (microsoft word, libreoffice writer, apple pages...) d'autre part un langage de formatage (html, tex, markdown, mediawiki, restructuredtext, ...) dans un éditeur de texte (gedit, textmate, vim, emacs, bloc-note, piratepad...). Je ne ferai pas de commentaire sur ces deux choix, il est possible de fabriquer un epub depuis un traitement de texte ou à partir d'un texte brut.

+ Libreoffice + plugin [writer2epub](http://extensions.services.openoffice.org/en/project/Writer2ePub). Si vous êtes plutôt traitement de texte, voici un choix intéressant. Vous pouvez reprendre un texte déjà écrit dans votre traitement de texte préféré, l'ouvrir avec libreoffice et fabriquer un epub automatiquement.
+ [Sigil](https://code.google.com/p/sigil/). Il est possible d'écrire directement le document dans sigil, éditeur d'epub. On peut utiliser sigil comme un traitement de texte ou comme un éditeur de texte en allant modifier directement le code html et le code CSS.
+ Conversion html ou xhtml puis sigil. Solution intermédiaire : si le document à transformer est au format html ou xhtml ou peut facilement être transformé en l'un de ces formats, on peut ensuite les insérer dans sigil en tant que nouveaux chapitres, sigil se chargeant d'inclure les images et les feuilles de style liées. Ça permet par exemple de faire un recueil d'articles glanés sur le web.
+ Markdown avec [pandoc](http://johnmacfarlane.net/pandoc/). La solution que j'utilise. J'écris dans mon éditeur de texte favori du code [markdown](https://en.wikipedia.org/wiki/Markdown) agrémenté de notes de bas de pages, de tableaux et éventuellement de mathématiques et je convertis à l'aide de pandoc. Pandoc peut également transformer des choses écrites en tex, en restructuredtext ou en html en epub (ou en html, tex, groff, rtf ou plein d'autres formats).


Il existe d'autres solutions (scripts maison, [atlantis](http://www.atlantiswordprocessor.com/fr/), [calibre](http://www.calibre-ebook.com/), [Pages](http://www.apple.com/iwork/pages/), quarkXpress, [la poule ou l'œuf](http://www.pouleouoeuf.org/),  ...). Si aucune des 3 ou 4 propositions ci-dessus ne convient, peut-être faudra-t-il se tourner vers une de ces solutions, mais ayant essayé l'approche scripts maison ainsi que calibre, je préfère largement pandoc, sigil et éventuellement writer2epub.
