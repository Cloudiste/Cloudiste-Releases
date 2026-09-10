# Cloudiste 0.12.0 — Pictogrammes de l’accueil

Les cinq commandes placées au-dessus des services utilisent maintenant des pictogrammes :

| Pictogramme | Action |
| --- | --- |
| Roue dentée | Réglages de Cloudiste |
| Grille de neuf carrés | Applications |
| Plus dans un cercle | Ajouter un service |
| Robot Android vert | Réglages Android |
| Bouton marche/arrêt rouge | Quitter |

Les zones de sélection gardent la même largeur et mesurent au moins 64 dp de haut. La bordure blanche indique toujours le focus de la manette. Les couleurs verte et rouge permettent de distinguer les deux commandes système.

Le texte n’est plus dessiné dans ces cinq boutons. Chaque image conserve toutefois son nom avec `contentDescription`. Android peut ainsi l’annoncer avec un service d’accessibilité, et Cloudiste peut identifier précisément le bouton sélectionné. La même cible gère A et le toucher : seule sa présentation visuelle change.

Les pictogrammes sont cinq ressources vectorielles XML dans `app/src/main/res/drawable`. Un dessin vectoriel reste net quelle que soit la définition de la console et évite une nouvelle bibliothèque d’icônes. `HomeScreen` associe chaque cible à son libellé accessible et à sa ressource, puis `HeaderAction` centre l’image dans la surface existante.

## Installer et tester

Installe **Cloudiste-0.12.0-debug.apk** par-dessus la version précédente avec la même signature. Les préférences et images existantes sont conservées.

1. Vérifie que les cinq textes ont été remplacés par les cinq pictogrammes décrits ci-dessus.
2. Parcours-les à la croix : chaque cadre doit rester entièrement visible.
3. Ouvre Réglages, Applications, Ajouter un service et Réglages Android avec A, puis reviens avec B.
4. Ouvre Applications en touchant directement sa grille.
5. Sélectionne le bouton rouge et vérifie qu’il ferme Cloudiste.
6. Si tu utilises une fonction d’accessibilité Android, vérifie qu’elle annonce le nom des cinq actions.

Les essais automatisés sont détaillés dans [le rapport de vérification](VERIFICATION-CLOUDISTE-0.12.md). Cette version attend ta validation sur console réelle.
