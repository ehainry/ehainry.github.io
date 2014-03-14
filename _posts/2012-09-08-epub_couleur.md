---
layout: posts
title: "ePub en couleurs"
categories:
- fr
- livres
- epub
---

Pourquoi ? Mais pourquoi ?

Pourquoi quelqu'un mettrait dans le style des paragraphes d'un livre
électronique l'instruction d'écrire en gris ?

Je suis tombé là-dessus :

{% highlight css %}
p {
    ...
    color:#4c4c4c;
    ...
}
{% endhighlight %}

Ce livre est fait pour être lu sur une liseuse. Il n'y a pas si longtemps, ces appareils n'affichaient que 4 niveaux de gris. Maintenant c'est un peu plus,
mais le contraste reste visiblement inférieur à celui des livres papier (même quand on qualifie la liseuse de "paperwhite"). Alors
réduire volontairement la lisibilité me paraît la dernière des idioties.

Et finalement la supériorité du livre numérique sur le livre papier tient
peut-être dans l'option *Styles originaux* qui, désactivée, permet de ne pas
subir les lubies des éditeurs (auteurs, stylistes ou autres) qui tiennent à ce
que leur livre soit lu en rose sur fond rouge.
