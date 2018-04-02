---
layout: posts
title: "Authentification à deux facteurs : andOTP"
categories:
- fr
---

# 2FA qu'est-ce que c'est ?

Les mots de passe, même longs et de sécurité élevée, ne sont pas parfaitement sûrs.
Ils peuvent par exemple apparaître suite à un piratage, une faille technique (heartbleed) ou humaine (il m'est arrivé de taper un mot de passe dans un moteur de recherche au lieu de la fenêtre voisine), ou être contournés.
Donc, la possibilité de s'identifier à l'aide d'un deuxième élément en plus du mot de passe a été introduite.
On dit en général que le mot de passe est *quelque chose que l'on sait*, et le second facteur *quelque chose que l'on possède*.
Ce second facteur, c'est par exemple un code envoyé par SMS (par exemple lors d'un paiement par carte bancaire), une clef physique 2FA ([yubikey](https://fr.wikipedia.org/wiki/YubiKey)) ou un code généré par un programme.

Le SMS ne résoud pas tous les problèmes de sécurité, par exemple, rien ne garantit la délivrance rapide du SMS, ils peuvent être interceptés et il existe des zones blanches.

L'objet physique a l'inconvénient de ne pas être compatible avec tous les services/matériels.

La troisième option est donc problabement la meilleure : faire tourner le programme sur le smartphone, objet que presque tout le monde a presque toujours sur soi ; les codes sont valables 30 secondes et en intercepter un ne donne pas les suivants. L'algorithme utilisé est standardisé : [TOTP](https://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm).

# Quel outil

Il existe plusieurs applications pour remplir ce rôle sur les smartphones : il suffit de chercher OTP (one time password) dans le magasin d'application pour trouver ces logiciels. Néanmoins, comme pour un gestionnaire de mot de passe, c'est un programme en lequel il faut avoir parfaitement confiance.

Les plus utilisés semblent être [Google Authenticator](https://itunes.apple.com/us/app/google-authenticator/id388497605?mt=8) et [Authy](https://play.google.com/store/apps/details?id=com.authy.authy).

J'ai commencé à utiliser authy comme application de second facteur d'authentification.
L'application est jolie, pratique et propose une sauvegarde sécurisée des données ce qui évite le casse tête du changement de smartphone.
Et aussi, c'est l'application que conseille [HumbleBundle](https://support.humblebundle.com/hc/en-us/articles/202421374-Humble-Bundle-Two-Step-Verification).

Mais parfois, les choses se passent mal.

> Anecdote : j'ajoute un second facteur pour un site important. Tout se passe bien.
> Deux heures plus tard j'essaie de me connecter.
> Je lance authy, il restaure une sauvegarde et le nouveau site n'est plus là...

En conséquence, je sauvegarde maintenant tous les jetons d'authentification avant de valider le second facteur dans un fichier latex qui génère les QR codes (les liens sont de la forme ``otpauth://totp/Example:robert?secret=1234567890ABCDEF``), et j'ai changé d'application : j'utilise [andOTP](https://github.com/andOTP/andOTP).
Moins joli mais j'ai plus confiance et je ne suis pas obligé d'utiliser leur solution de sauvegarde.
Surtout le code est libre (visible et modifiable sur github), l'application est disponible sur [F-Droid](https://f-droid.org/packages/org.shadowice.flocke.andotp/).

Il reste un problème : le second facteur d'HumbleBundle est uniquement compatible avec Authy !
Pourquoi ne veulent-ils pas utiliser l'algorithme TOTP ?

# Sauvegarde et migration

Pour sauvegarder mes secrets, je les conserve comme dit précédemment dans un fichier tex (chiffré).
Mais pour les récupérer, j'ai utilisé [ce script de Guillaume Boudreau](https://www.pommepause.com/2014/10/how-to-extract-your-totp-secrets-from-authy/).

# Mise à jour (2 avril 2018)

Humble Bundle est passé à l'algorithme standard ! Je ne sais pas depuis quand, mais plus besoin d'authy.

