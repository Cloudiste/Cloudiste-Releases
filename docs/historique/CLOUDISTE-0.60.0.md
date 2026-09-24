# Cloudiste 0.60.0 — Cohérence UI et navigation manette

Cette version applique les premières corrections de la revue UI/UX sans retirer les raccourcis et choix d’accueil déjà validés.

## Recherche de jeux

- résultats rendus avec `FocusableSurface`, comme les tuiles de l’accueil ;
- navigation à la croix entre l’en-tête, la recherche, les résultats et la fiche ;
- défilement automatique lorsque le focus atteint un résultat ou une action hors écran ;
- services, boutiques et attribution accessibles à la manette ;
- noms de boutiques directement cliquables, sans ligne « Acheter sur… » ;
- sons, halo, animation et contraste de focus communs au reste de Cloudiste.

## Thèmes et lisibilité

- définition explicite de `primaryContainer`, `secondaryContainer`, `tertiaryContainer`, `outlineVariant` et des couleurs de contenu associées ;
- palettes distinctes pour Sombre, OLED et Clair ;
- disparition des couleurs violettes héritées de Material 3 ;
- texte d’aide `bodySmall` porté à 14 sp avec une hauteur de ligne de 20 sp.

## Navigation

- Découvrir place maintenant le focus initial sur le premier service ;
- lorsque Cloudiste détient le rôle HOME, le bouton Quitter est masqué ;
- dans ce même mode, B ne ferme plus l’accueil et Quitter disparaît du parcours de focus ;
- le comportement classique reste inchangé lorsque Cloudiste est lancé comme une application.

Cette version reste locale jusqu’à validation sur appareil réel.
