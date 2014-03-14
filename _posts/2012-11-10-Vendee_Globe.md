---
layout: posts
title: "Suivre le Vendée Globe sans flash"
categories:
- fr
- voile
- cartographie
- python
- javascript
- vendee globe
---

Hop, départ du Vendée Globe 2012. Comme d'habitude, la cartographie se fait dans une application flash. C'est lourd, ça ne marche pas sur mon téléphone et ça fait souffler mon ordinateur comme une baleine ! J'ai ressorti mon [script python pour fabriquer des cartes statiques](https://bitbucket.org/manu/vg/) qui donne des [cartes plus ou moins jolies](http://velsheda.lateralis.org/cartes/vg_carte.jpg). Et pour être moderne (et apprendre à utiliser les API de cartographie), j'ai aussi fait deux versions en javascript : [vendeejs](https://bitbucket.org/manu/vendeejs/).


![Exemple de carte statique](/images/vg_vi.jpg)


En bref trois cartes des positions des bateaux du Vendée Globe :
* [carte jpg statique (mais à jour)](/images/vg_carte.jpg)
* [carte dynamique v1](/vg/nokia.html)
* [carte dynamique v2](/vgjs/leaflet.html)

Les versions javascript utilisent
* d'une part l'[API de cartographie nokia](http://api.maps.nokia.com/en/index.html)
* d'autre part l'[API Leaflet](http://leaflet.cloudmade.com/) avec des tuiles [ESRI](http://www.esri.com/getting-started/developers). Les icones des bateaux ne sont pas terribles, mais j'ai fait une version plus jolie accessible en enlevant "js" dans l'adresse.

J'ai découvert que ce n'était plus possible de charger un fichier html sur un autre serveur[^1] depuis un script javascript alors que j'aimerais le faire pour récupérer le classement. Ceci pour éviter les [attaques XSS](https://fr.wikipedia.org/wiki/Cross-site_scripting). J'ai aussi redécouvert que javascript est vraiment un langage désagréable pour programmer. Même si j'ai codé ce script à l'arrache, je trouve que les erreurs pourraient être un peu mieux expliquées, que concaténer et additionner avec le même opérateur dans un langage où les types sont aussi mous qu'en javascript, c'est une mauvaise idée, bref que python est quand même beaucoup plus sympa.

[^1]: sauf si c'était un serveur que j'administre auquel cas je pourrais faire du [CORS](https://en.wikipedia.org/wiki/Cross-Origin_Resource_Sharing), ce qui n'est pas le cas pour <http://www.vendeeglobe.org/>.
