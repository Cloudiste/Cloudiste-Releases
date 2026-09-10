# Cloudiste 0.19.0 — Thèmes Sombre, OLED et Clair

Cloudiste propose maintenant trois apparences globales. Un bouton permanent en bas à gauche de l’accueil permet de les faire défiler immédiatement. Le même choix reste aussi disponible au début de **Réglages > Apparence**.

Le nom en texte de l’accueil est remplacé par le nouveau logo Cloudiste, centré en haut de l’écran. Sa ressource possède un fond transparent. En thème Clair, elle repose directement sur le fond ; en Sombre et OLED, une capsule claire et arrondie préserve les couleurs originales et le contraste. Le bouton Quitter reste indépendant, en haut à droite.

## Les trois modes

- **Sombre** conserve l’apparence gris anthracite des versions précédentes. Un semis très discret de micro-points lui donne maintenant un peu de matière. Il reste le réglage initial lors d’une première installation.
- **OLED** utilise un arrière-plan noir pur (`#000000`). Les cartes gardent une nuance presque noire afin de rester séparées visuellement sans illuminer toute la dalle.
- **Clair** utilise un fond blanc légèrement bleuté, lui aussi légèrement texturé, des surfaces gris clair et des textes sombres.

Le mode Clair ne se contente pas d’inverser le texte. Les couleurs de succès, d’avertissement et d’erreur ont une variante assez foncée pour rester lisibles. Les logos blancs, notamment Boosteroid, Xbox et PlayStation, sont placés sur un support sombre dans l’accueil, Découvrir et les fiches.

## Utilisation

Sur l’accueil, le bouton affiche le mode actif à côté d’un pictogramme moitié clair, moitié sombre. Chaque activation suit le cycle **Sombre → OLED → Clair → Sombre**. Avec la manette, Bas depuis la première tuile place le focus sur ce bouton ; Droite rejoint ensuite le dock central.

Dans Réglages, les trois boutons **Sombre**, **OLED** et **Clair** restent des cibles ordinaires de Cloudiste. Ils fonctionnent au toucher, à la croix directionnelle et au stick gauche. Le focus reste entouré d’une bordure contrastée et le bouton actif porte le texte « Sélectionné ».

Le changement recolore l’écran sans le fermer. Il adapte également les pictogrammes du dock ainsi que les icônes et la barre de navigation Android. Le mode Clair utilise des icônes système sombres ; les deux modes foncés utilisent des icônes claires.

## Fonctionnement du code

`ThemeMode` est une `enum class` Kotlin. Elle limite les valeurs possibles à `DARK`, `OLED` et `LIGHT`. `LauncherPreferences` conserve la valeur courante et DataStore l’enregistre sous la clé `theme_mode`.

Une valeur inconnue, par exemple après une évolution future, revient au thème Sombre au lieu de provoquer une erreur. Tous les écrans observent le même flux DataStore dans `CloudGamingLauncherTheme`. Compose redessine seulement les éléments dont les couleurs ont changé.

Les trois palettes sont regroupées dans `ui/theme/Theme.kt`. Les composants utilisent les rôles Material tels que `background`, `surfaceVariant`, `onSurface`, `primary`, `secondary`, `tertiary` et `error`. Cela évite de coder une couleur de texte différente dans chaque écran.

La texture est dessinée par un `Canvas` Compose placé derrière tous les écrans. Ses points alternent légèrement en taille et en couleur, avec une opacité très faible. Cette couche n’est pas interactive : elle ne peut donc intercepter ni les touchers ni les commandes de la manette. Elle est désactivée en mode OLED pour conserver de vrais pixels noirs.

Aucune dépendance supplémentaire n’a été ajoutée.

## Essai sur appareil réel

1. Installe la version 0.19.0 par-dessus la 0.18. Tes services, leur ordre et leurs images doivent être conservés.
2. Sur l’accueil, touche le bouton **Sombre** en bas à gauche. Il doit afficher **OLED** et le fond doit devenir complètement noir.
3. Reviens à l’accueil. Vérifie que le logo Cloudiste est centré, complet et lisible, puis contrôle les tuiles, les états, le dock et le bouton Quitter. Le fond Sombre doit présenter un grain fin et discret.
4. Depuis la première tuile, appuie sur Bas pour rejoindre le bouton d’apparence, puis sur A pour passer à **Clair**. Vérifie que les icônes des barres Android deviennent sombres.
5. En mode Clair, vérifie que le logo apparaît sans capsule visible. Parcours ensuite Applications, Ajouter un service, Découvrir, une fiche et Personnaliser. Aucun texte ni pictogramme ne doit disparaître ; la même texture légère doit rester visible dans les zones libres.
6. Ferme complètement Cloudiste puis relance-le. Le dernier thème choisi doit être conservé.
7. Reviens au mode Sombre avec le bouton de l’accueil, puis ouvre Réglages : **Sombre · Sélectionné** doit aussi y être indiqué.

Sur une console OLED, observe le fond autour des cartes dans une pièce sombre : il doit être noir, sans halo gris général. La personnalisation d’un service reste indépendante du thème choisi.
