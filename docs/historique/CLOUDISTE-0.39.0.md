# Cloudiste 0.39.0 — Tuiles épurées et fond général

La personnalisation de chaque service propose désormais trois réglages indépendants : afficher ou masquer le logo, le nom et les informations de la tuile. Les informations regroupent notamment l’état d’installation, le type d’accès et la priorité de lancement. Ces éléments restent présents pour l’accessibilité même lorsqu’ils ne sont plus dessinés.

La rubrique **Apparence** des réglages permet de choisir entre deux comportements :

- **Fond général** : une seule illustration reste derrière tout l’accueil. Les personnalisations propres aux services restent à l’intérieur de leurs tuiles.
- **Fond selon le service** : le fond change avec la tuile sélectionnée, comme dans les versions précédentes.

Le bouton **Personnaliser le fond général** ouvre un écran de choix et d’aperçu. Les médias acceptés sont les images, les GIF animés, les vidéos MP4 et WebM. Les vidéos sont silencieuses et lues en boucle.

Les réglages existants utilisent automatiquement **Fond selon le service** après la mise à jour afin de conserver l’apparence actuelle. Le mode, le média général et les options de visibilité sont inclus dans les sauvegardes `.cloudiste`.

Les vidéos sont limitées à 50 Mo, 60 secondes et 4096 × 4096 pixels. Une vidéo courte en 720p est recommandée pour préserver la fluidité et l’autonomie.

La version Android passe à `versionName 0.39.0` et `versionCode 47`.

## Tester

1. Maintiens une tuile puis masque séparément son logo, son nom et ses informations.
2. Vérifie le résultat dans les modes détaillé et compact.
3. Dans **Réglages → Apparence**, choisis **Fond général**, puis **Personnaliser le fond général**.
4. Teste une image, un GIF et une courte vidéo MP4 ou WebM.
5. Vérifie que le fond reste fixe lorsque tu changes de service et que les images personnalisées restent dans les tuiles.
6. Repasse sur **Fond selon le service** et vérifie le changement de fond avec la sélection.
7. Redémarre Cloudiste, puis teste une sauvegarde et une restauration.
