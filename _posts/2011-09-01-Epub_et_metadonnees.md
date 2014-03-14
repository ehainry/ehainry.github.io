---
layout: posts
title: "epub et métadonnées"
categories:
- fr
- ebook
- epub
- propriétés
---

Comme je l'ai déjà dit [précédemment](/2011/05-27/Ecrire_en_epub.html), un fichier epub est en réalité une archive zip ayant une structure et un contenu bien défini. Tout d'abord, il contient un fichier nommé `mimetype` contenant le texte `application/epub+zip`, premier fichier dans l'archive, sauvegardé sans compression. Pourquoi ? Tout simplement pour que les octets 30 à 57 du fichier contiennent exactement le texte `mimetypeapplication/epub+zip`.

Les autres fichiers peuvent être compressés et n'ont pas à respecter d'ordre.

Deuxième fichier obligatoire : `META-INF/container.xml`. Ce fichier semble avoir pour unique intérêt de dire où se trouve et comment se nomme le fichier de squelette (opf). Il est donc inutile de parcourir tous les fichiers à la recherche d'un fichier opf et cela permet de ne pas se tromper quand il y en a plusieurs... Expérience vécue : après avoir trouvé un fichier .opf, je m'aperçois qu'il ne contient absolument pas ce qu'il devrait et je comprends ma douleur en voyant qu'il s'agit de `__MACOSX/OEBPS/._content.opf` c'est-à-dire un fichier caché créé par un mac et qui n'a rien à faire dans un livre que je viens d'acheter, n'est-ce pas Bragelonne...

Le fichier qui m'intéresse aujourd'hui : le fichier opf. Celui-ci contient d'une part les métadonnées (titre, auteur(s), date de publication, etc.), d'autre part les fichiers utiles de l'archive ainsi que l'ordre dans lequel on parcourra le texte.

Par exemple (extrait de http://jean-claude.dunyach.pagesperso-orange.fr/Articles/Article.epub, je laisse le lecteur trouver le nom de l'auteur et le titre de l'article tout seul) :

{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<package xmlns="http://www.idpf.org/2007/opf" version="2.0" unique-identifier="BookId">
<metadata xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:opf="http://www.idpf.org/2007/opf">
<dc:title>Le livre va-t-il sombrer dans la mer numérique ?</dc:title>
<dc:creator opf:file-as="Dunyach, Jean-Claude" opf:role="aut">Jean-Claude Dunyach</dc:creator>
<dc:subject>ebook</dc:subject>
<dc:description>Une réflexion sur l'avenir du livre numérique</dc:description>
<dc:publisher>Moi-même</dc:publisher>
<dc:date>2010-10-22</dc:date>
<dc:identifier id="BookId">V 1.01</dc:identifier>
<dc:language>fr</dc:language>
<dc:rights>Creative Commons 2.0</dc:rights>
<meta name="price" content="0"/>
<meta name="cover" content="img1"/>
</metadata>
<manifest>
<item id="ncx" href="toc.ncx" media-type="application/x-dtbncx+xml"/>
<item id="style" href="style.css" media-type="text/css"/>
<item id="id001" href="001.html" media-type="application/xhtml+xml"/>
<item id="id002" href="002.html" media-type="application/xhtml+xml"/>
<item id="id003" href="003.html" media-type="application/xhtml+xml"/>
<item id="img1" href="images/img1.jpg" media-type="image/jpeg"/>
<item id="img2" href="images/img2.png" media-type="image/png"/>
<item id="img3" href="images/img3.png" media-type="image/png"/>
</manifest>
<spine toc="ncx">
<itemref idref="id001" linear="no"/>
<itemref idref="id002"/>
<itemref idref="id003"/>
</spine>
<guide>
<reference type="cover" title="Cover image" href="001.html"/>
</guide>
</package>
{% endhighlight %}

On trouve donc bien les informations promises (des dc:machin) et on apprend qu'il y a 3 fichiers html à commencer par celui ayant l'identifiant `id001` qui se trouve être le fichier `001.html`.

Quatrième fichier important et malheureusement mal exploité par certains éditeurs, la table des matières : `toc.ncx`. Mais ce sera pour un prochain épisode.

Pour en revenir aux métadonnées, je me suis confectionné un petit programme [epubinfo](https://bitbucket.org/manu/epubinfo) pour les lire et modifier. Je l'utilise en particulier pour changer les dates de publications (je classe les livres en fonction de cette date), corriger les noms d'auteur (par exemple le nom de famille d'*Alexandre Dumas fils* n'est pas *fils*) et mettre la bonne langue (ce qui permet à mon [reader](http://bookeen.com/fr/cybook/?id=2) de faire la césure comme il faut) sans ouvrir un vrai éditeur d'epub lourd (sigil) ni le faire complètement à la main.

Ensuite, je compte utiliser ce programme pour classer mes livres de façon un peu plus intelligente qu'actuellement (un dossier par auteur dans lequel les fichiers sont classés par date de publication) en groupant plusieurs auteurs dans un même dossier tant que cela représente moins de 12 livres par exemple mais sans séparer les livres d'un même auteur en deux dossiers différents.
