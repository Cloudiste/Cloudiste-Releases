# Cloudiste 0.17.0 — Solidification et base Google Play

Cette version consolide les éléments relevés par l'audit avant d'ajouter de nouveaux parcours.

**Version validée par l'utilisateur sur appareil réel.**

## Navigation à la manette

Le stick gauche produit maintenant la même navigation que la croix directionnelle dans l'accueil, Applications, Ajouter un service, Découvrir, les fiches, Réglages et Personnaliser. Une zone morte empêche les déplacements causés par un stick légèrement décentré. Le maintien attend brièvement avant de répéter le déplacement.

Le lecteur Web conserve son comportement spécifique : les mouvements analogiques bruts restent transmis au jeu dans la page.

## Lecteur Web

Le domaine courant est affiché en haut à gauche. Chaque service possède une liste locale de domaines autorisés, sous-domaines inclus. Les liens HTTP, les URL contenant des identifiants et les domaines inattendus restent bloqués dans le lecteur.

Lorsqu'une connexion tente d'ouvrir un domaine encore inconnu, le menu explique le blocage et propose de continuer dans le navigateur externe. Ce mécanisme devra être testé avec un compte réel pour GeForce NOW, Boosteroid et Xbox avant une publication.

## Préférences et images

Deux niveaux de récupération protègent les réglages :

- DataStore remplace un fichier Preferences devenu illisible par un état vide cohérent ;
- les JSON des services personnalisés et des fonds ignorent désormais un contenu invalide au lieu d'arrêter l'application.

Les fonds et miniatures récemment utilisés sont conservés dans un cache mémoire limité. Lors d'un changement de focus, l'image précédente reste affichée pendant le premier décodage afin d'éviter un flash noir.

## États et focus

L'état d'une application ne reprend plus la couleur décorative du service. Installé est vert et rond, les situations à vérifier sont jaunes et carrées, et les erreurs ou désactivations sont rouges. Le libellé reste présent pour ne jamais dépendre uniquement de la couleur.

La cible d'un glisser-déposer utilise une bordure jaune plus épaisse et un agrandissement distinct. Dans une fiche Découvrir, le focus commence sur **Site internet**, l'action principale, plutôt que sur Retour. Une fiche demandée avec un identifiant invalide affiche un écran d'erreur utilisable au doigt et à la manette.

## Identité Android et release

L'identifiant définitif est `fr.cloudiste.launcher`. La version est `0.17.0`, avec `versionCode 17`. Android considère ce nouvel identifiant comme une autre application : la version 0.16 peut donc rester installée séparément et ses préférences ne sont pas transférées.

Le build `release` active R8 et la réduction des ressources. Un APK release et un AAB peuvent être générés, mais la clé privée de publication n'est volontairement pas stockée dans le projet.

## Essai sur appareil réel

1. Installe `app/build/outputs/apk/debug/app-debug.apk` depuis Android Studio.
2. Vérifie que l'icône ouvre la nouvelle application `fr.cloudiste.launcher`.
3. Parcours chaque écran avec la croix, puis avec le stick gauche. Le focus doit avancer d'une cible et se répéter sans accélération excessive lors du maintien.
4. Alterne immédiatement entre stick et toucher.
5. Fais glisser une tuile au doigt : la cible doit avoir une bordure jaune, puis l'ordre doit être conservé après redémarrage.
6. Ajoute un fond, parcours plusieurs tuiles et reviens dessus : aucun flash noir durable ne doit apparaître.
7. Ouvre Découvrir puis une fiche : Site internet doit recevoir le focus initial.
8. Lance les trois services Web. Vérifie le domaine affiché et termine chaque connexion. Note tout domaine bloqué afin de l'ajouter seulement après vérification.

La signature Play, la politique de confidentialité publique et la fiche Google Play seront finalisées avant la première soumission.
