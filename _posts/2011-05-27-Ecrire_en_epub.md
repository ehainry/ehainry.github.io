---
layout: posts
title: "Comment créer un epub"
categories:
- fr
- ebook
- epub
---

Un epub est une archive zip contenant essentiellement des fichiers de contenu
html (ou xhtml ou xml), des fichiers de style CSS, éventuellement des images et
des polices et des fichiers décrivant l'ordre, les propriétés des autres (une
sorte de table des matières). Sigil est un bon outil pour écrire et modifier un
epub sans se poser trop de questions.

Les fichiers html sont écrits de façon classique mais en évitant les informations de forme
qui doivent aller dans les css et en maximisant la structuration (un paragraphe
est dans un `<p>...</p>`, des titres en h1, h2, h3. Donc pour centrer un
paragraphe, pour des exergues ou pour les mises en reliefs, il faut mettre le
texte dans un `div` ou un `span` (ou éventuellement un `em`) et mettre les
règles dans le fichier CSS).

Quelques règles css pour faire un texte qui me plaît :

{% highlight css %}
@page {margin: 3mm}
p {text-align: justify; margin: 1ex 0 0 0; line-height: 1.3}
p+p {text-indent: 2em}
{% endhighlight %}

Le `@page` s'applique au contenu paginé et permet de définir le formatage des
"pages" sur le reader. Ici, j'ai mis des marges, on peut aussi régler les
veuves et orphelins. J'apprécie que le texte soit justifié, que les paragraphes
soient séparés verticalement, que les lignes d'un paragraphes soient un peu
espacées et que les paragraphes qui en suivent un autre soient indentés.

Pour le style des titres de chapitre c'est plus fluctuant. Je choisis des
choses simples. Un peu comme le style Gibson du [ePub Zen Garden](http://epubzengarden.com/). Ce qui peut donner des choses comme ce qui suit.

{% highlight html %}
<h3><span class="nchap">I</span>
    <span class="chaptitle">Titre de chapitre</span></h3>
{% endhighlight %}

Et dans le css

{% highlight css %}
h3 {text-align: center}
.nchap {font-style: italic}
.nchap:before {content: "Chapitre "; text-transform: none; font-style: italic}
.chaptitle {display: block}
{% endhighlight %}


Pour plus d'infos, on pourra lire un [guide sur le format epub](http://www.hxa.name/articles/content/epub-guide_hxa7241_2007.html) et par exemple comment mettre un [couverture dans un epub](http://blog.threepress.org/2009/11/20/best-practices-in-epub-cover-images/) (tout le blog est fort intéressant).
