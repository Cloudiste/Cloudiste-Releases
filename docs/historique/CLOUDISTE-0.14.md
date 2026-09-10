# Cloudiste 0.14.0 — Dock de l’accueil

L’accueil possède maintenant deux zones de commandes plus discrètes :

- **Quitter** est placé en haut à droite, sur la même ligne que le nom Cloudiste ;
- **Réglages**, **Applications**, **Ajouter un service** et **Réglages Android** sont regroupés dans un dock compact, centré en bas.

Les cinq actions gardent leurs pictogrammes, leur nom accessible et leur fonctionnement au toucher et à la manette.

## Comment la disposition Compose fonctionne

L’écran utilise une grande `Column`, c’est-à-dire un conteneur qui place ses enfants verticalement. Elle contient désormais :

1. une `Row` pour mettre Cloudiste à gauche et Quitter à droite ;
2. le sous-titre avec le nombre de services ;
3. la zone défilante des tuiles, qui reçoit l’espace restant avec `weight(1f)` ;
4. le dock centré en bas.

Le dock est une `Surface` arrondie contenant une `Row` de quatre boutons. La `Surface` prend uniquement la largeur nécessaire à son contenu. Un `Box` plus large la centre, sans étirer son fond sur tout l’écran.

Les boutons du dock mesurent 58 dp et leurs pictogrammes 32 dp. Le bouton Quitter mesure 56 dp. Ils sont visuellement plus petits que les anciennes grandes commandes, tout en restant au-dessus de la cible tactile minimale courante de 48 dp.

Seule la zone des services défile. Le titre, Quitter et le dock restent donc toujours à leur place, même lorsque beaucoup de services sont ajoutés.

## Navigation à la manette

La liste logique de navigation suit la nouvelle position des éléments :

- depuis une tuile, **Haut** rejoint Quitter ;
- depuis Quitter, **Bas** revient vers les services ;
- depuis la dernière ligne de services, **Bas** rejoint le dock ;
- dans le dock, **Gauche** et **Droite** parcourent les quatre actions ;
- depuis le dock, **Haut** revient vers la tuile située dans la même colonne.

Le bouton Y ou Start continue d’ouvrir directement les réglages de Cloudiste. Les appuis tactiles appellent les mêmes fonctions que le bouton A.

## Installer et tester sur l’appareil réel

Installe **Cloudiste-0.14.0-debug.apk** par-dessus la version précédente. L’identifiant Android et la signature restent identiques, donc les services, images, modes de lancement et ordres enregistrés sont conservés.

1. Vérifie que Quitter se trouve en haut à droite, face au nom Cloudiste.
2. Vérifie que le dock des quatre pictogrammes est centré en bas et que son fond ne prend pas toute la largeur.
3. Touche chaque pictogramme du dock et reviens à l’accueil après chaque ouverture.
4. Touche Quitter et vérifie que Cloudiste se ferme.
5. Relance Cloudiste. Avec la manette, pars de la première tuile et appuie sur Haut : Quitter doit recevoir la bordure blanche.
6. Appuie sur Bas pour revenir à la tuile, puis encore sur Bas jusqu’au dock.
7. Parcours les quatre commandes du dock avec Gauche et Droite, puis ouvre chacune avec A.
8. Si plusieurs lignes de services sont présentes, vérifie que les tuiles défilent tandis que le dock reste en bas.
9. Vérifie enfin qu’un toucher court, un appui long et un glissement sur une tuile conservent leurs comportements précédents.

Le [rapport de vérification](VERIFICATION-CLOUDISTE-0.14.md) décrit les contrôles effectués sur l’émulateur. Cette version attend ta validation sur la console réelle.
