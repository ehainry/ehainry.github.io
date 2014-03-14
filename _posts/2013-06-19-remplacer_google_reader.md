---
layout: posts
title: "Remplacer Google Reader"
date: 2013-06-19 19:00
categories:
- fr
---

Le RSS[^1] (Really Simple Syndication) est un format de données (comme html)
qui permet de rassembler un ensemble d'articles comme un magazine le ferait. Ce
format est particulièrement intéressant pour les blogs puisqu'il permet de
s'abonner et ainsi de suivre quand de nouveaux articles sont publiés. L'intérêt
par rapport à la page d'accueil du site est que l'on peut agréger plusieurs
flux rss et donc surveiller de nombreux blogs, magazines à la fois. [RSS c'est
aussi beaucoup
plus](http://inessential.com/2013/03/14/why_i_love_rss_and_you_do_too). Un gros avantage (et inconvénient si on se place de l'autre côté) est que l'on peut ainsi lire le contenu d'un site sans le visiter, donc sans subir de publicités intrusives.

Google, avec *Google Reader* propose un service en ligne permettant de
s'abonner et de lire des flux dans une interface pratique (on peut regrouper
des flux par thème ou par importance, marquer des articles pour les lire plus
tard ou les partager). Mais Google a décidé de fermer *Google Reader*. Et oui, quand on a pour business de vendre de la publicité ciblée, l'avantage du RSS est un terrible obstacle (et n'est sans doute pas contrebalancé par la quantité d'information qu'on acquiert en connaissant ce que lit le client). Comme je
l'utilisais assidûment (un des rares services google dont j'étais dépendant),
il me faut un remplaçant. Et des remplaçants, beaucoup se sont déclarés : voici
par exemple une [liste non exhaustive](http://getgini.com/google-reader-alternatives).

Parmi ces possibilités, un choix doit être fait entre une solution hébergée,
auto-hébergé et un client natif. L'avantage de l'hébergé étant que la gestion
du service est déléguée, l'avantage de l'auto-hébergé que l'on n'est pas
dépendant du bon vouloir du fournisseur de service (donc pas de fermeture du
service comme avec Google Reader. L'avantage du client natif est qu'il n'y a ni
gestion ni dépendance, mais il manque a priori la possibilité de lire sur
plusieurs appareils sans retomber sur les articles déjà lus. Les solutions
hébergées ou auto-hébergées doivent bien entendu être accessibles par un
navigateur web et lisibles sur smartphone.

Sous linux, j'apprécie [liferea] et [newsbeuter] comme clients natifs. Mais
j'ai finalement opté pour [Feedhq](https://feedhq.org/), c'est-à-dire une
solution hébergée mais open-source donc que je peux auto-héberger si l'envie
m'en prend.

En réalité j'utilise une solution mixte, une sorte de meilleur des deux mondes : un service hébergé et synchronisation depuis un client natif.
En l'occurence, j'ai choisi newsbeuter (le mutt des lecteurs RSS) qui pouvait se synchroniser avec google reader
(c'est-à-dire récupérer les flux et le statut lu ou non) et peut le faire aussi
avec tiny tiny rss. Liferea a les mêmes capacités de synchronisation, sous iOS ou Android, pléthore de lecteurs RSS sont aussi conçu pour se synchroniser avec *google reader* ou *tiny tiny rss*.
[FeedHQ implémente la même API que google reader](https://feedhq.org/blog/3-supporting-google-reader-api), d'autres services font de même, par exemple, feedly ou feedbin et potentiellement seront bien supportés par les clients natifs (ou le sont déjà).


En parallèle, j'utilise rawdog et rss2email pour quelques flux. En gros, pour
des flux riches en images et pas trop fréquents, j'utilise rawdog qui produit
une page web (et j'ai bidouillé la configuration pour avoir une page
"responsive" c'est-à-dire qui s'adapte joliment aux téléphones avec la
plate-forme [skeleton](http://www.getskeleton.com/) : mes fichiers de
configuration sont [disponibles](https://bitbucket.org/manu/rawdog/src)). Et
pour des flux de textes longs, j'utilise rss2email qui comme son nom l'indique
m'envoie des mails contenant les nouveaux articles.


[liferea]: http://lzone.de/liferea/
[newsbeuter]: http://newsbeuter.org/
[^1]: Je confonds RSS et ATOM qui ont le même but et sont en général également supportés par les logiciels de RSS.
