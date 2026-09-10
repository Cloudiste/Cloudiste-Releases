# Cloudiste 0.26.0 — Transition du mode plein écran

Cette version anime le passage d’un service au suivant lorsque l’accueil utilise le mode plein écran.

## Animation

- Le logo, le nom, l’état et les indications du service glissent ensemble.
- Une navigation vers la droite fait entrer le nouveau service depuis la droite ; la navigation inverse utilise la direction opposée.
- Le fond précédent se fond progressivement dans le nouveau en 520 ms.
- Le contenu central termine son mouvement en 420 ms afin que la transition reste vive à la manette.
- Le passage du dernier service au premier conserve la direction demandée.

La transition se déclenche avec **LB/RB**, la gauche et la droite de la croix lorsque le service est sélectionné, ainsi qu’avec un glissement horizontal au doigt. Le focus reste sur une seule zone interactive pendant l’animation : **A**, **Y** et l’appui prolongé gardent donc leur comportement habituel.

## Dépendance Compose

Le module `androidx.compose.animation:animation` a été ajouté. Il appartient à Jetpack Compose et fournit ici `AnimatedContent` pour le mouvement du contenu et `Crossfade` pour le fond. Sa version reste alignée avec les autres composants Compose par la BOM déjà présente dans le projet.

## Essai sur appareil réel

1. Passe en plein écran avec **Select** ou le bouton inférieur droit.
2. Place le focus sur le service et appuie plusieurs fois sur **RB**, puis sur **LB**.
3. Vérifie que le mouvement suit la direction et que le fond change sans coupure.
4. Utilise ensuite gauche et droite sur la croix.
5. Fais glisser le panneau au doigt dans les deux directions.
6. Pendant et juste après une transition, vérifie **A** pour ouvrir et **Y** pour personnaliser.
7. Parcours le passage du quatrième service au premier, puis le retour du premier au quatrième.

