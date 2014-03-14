---
layout: posts
title: "Naviguer autrement avec luakit"
date: 2010-11-25 08:57:11
categories:
- fr
comments: 
- {text: "<p>midori est passé par le problème du download manager et a donc une faq là-dessus <a href=\"http://wiki.xfce.org/midori/faq#download_managers\" rel=\"nofollow\">http://wiki.xfce.org/midori/fa...</a> . Vais tester uget, ainsi que admiral (qui a l'air d'être une version à peine plus élaborée que mon script) et peut-être attendre eatmymonkey (un front-end à aria2).</p>",
author: milosh}
---

Je teste régulièrement des navigateurs pour remplacer celui qui est mon préféré depuis presque 10 ans : opera. Firefox n'a jamais réussi à me convaincre. Je ne sais pas trop pourquoi epiphany ne ma plaît pas. Midori est sympathique mais manque d'un gestionnaire de mots de passe et parfois de stabilité. Chromium, bah, il est moche et a le même défaut que firefox : les extensions. Et voilà qu'opera est en train de gonfler (consomme plus de mémoire que firefox !) et ajoute des extensions aussi. Franchement, à quoi servent les extensions ? À modifier les sites que je visite ? Il y a les userscripts pour ça. À avoir de vraies applications bâties sur le navigateur ? Opera a déjà unite et widgets pour ça. Bref, exit Opera.

J'ai été intéressé par [uzbl](http://www.uzbl.org/) il y a quelques temps mais je ne m'y suis pas adapté (et je n'ai pas eu le courage d'adapter sa configuration à mes goûts). Mais l'idée du navigateur minimal avec un vrai moteur me séduisait. C'est sur la liste de diffusion d'[awesome](http://awesome.naquadah.org) que j'ai appris l'existence de luakit qui m'a plu au premier abord.

[luakit](http://luakit.org/) est un navigateur en kit en lua (basé sur webkit). Les fichiers de configuration permettent de définir tout ce qu'on veut en plus, il suffit de savoir lire lua (et il n'y a rien de compliqué dans lua). Et en fait les configurations par défaut sont très bien.

Luakit possède même un gestionnaire de mots de passe (formfiller). Je mets mon login et mon mot de passe, je tape 'zn' et un fichier texte qui va être sauvegardé dans `~/.local/share/luakit/forms/url` apparaît avec les infos en question. Après, 'zl' remplira les champs avec les mêmes infos. (Aide-mémoire : l pour load, n pour new (et aussi e pour edit et a pour add)).

Deux défauts tout de même :

* pas de mouse gestures. Mais en fait luakit marche très bien sans souris, donc ça ne me manque pas trop.
* les téléchargements : luakit utilise wget pour télécharger (c'est fondamentalement très bien). Le problème est qu'il n'y a pas de suivi possible : pas de barre de progression, pas de notification de fin de téléchargement. Pour la notification, j'ai échangé get contre un script perso qui fait un notify-send à la fin du téléchargement.

Pour finir, quelques modifications de la configuration que j'ai faites

{% highlight lua %}
-- binds.lua
add_cmds({
    -- Tabs
    cmd({"buffernext", "bn"},       function (w)    w:prev_tab() end),
    cmd({"bufferprevious", "bp"},   function (w)    w:next_tab() end)
})

add_binds("normal", {
    -- Tabs
    key({"Control"}, "Left",        function (w)    w:prev_tab() end),
    key({"Control"}, "Right",       function (w)    w:next_tab() end),
    -- standard back/forward combo
    key({"Mod1"}, "Left",           function (w)    w:back()     end),
    key({"Mod1"}, "Right",          function (w)    w:forward()  end),
    -- readability
    buf("^gor$", function (w) w:eval_js("javascript:(function(){readStyle=...})();", "javascript") end),
    -- instapaper
    buf("^goi$", function (w) w:eval_js("javascript:function...;void(0)", "javascript") end),
    -- delicious
    buf("^god$", function (w) w:eval_js("javascript:(function(){location.href='http://www.delicious.com/save?url='+encodeURIComponent(window.location.href)+'&title='+encodeURIComponent(document.title)+'&v=5&jump=yes'})()", "javascript") end)
})
{% endhighlight %}

Les `javascript:...` correspondent au lien javascript donné par le bookmarklet.

* * *

**Update**

Luakit ayant un peu évolué, les lignes ci-dessus pour les appels javascript ne sont plus corrects : il faut remplacer `w:eval_js` par `w.view:eval_js` et le second argument est déprécié. Ce qui donne des lignes du genre

{% highlight lua %}
buf("^gor$", function (w) w.view:eval_js("javascript:(function(){_readableOptions=...;})()") end),
{% endhighlight %}
