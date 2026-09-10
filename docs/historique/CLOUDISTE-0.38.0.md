# Cloudiste 0.38.0 — Dock, recherche et GIF animés

Cette version permet de retirer une application directement depuis le Dock. Place le focus sur son icône puis appuie sur **Y**, ou maintiens l’icône au doigt. Cloudiste demande une confirmation avant de retirer le raccourci. L’application Android reste installée.

Le clavier de recherche de la page **Applications** possède maintenant un fond opaque utilisant la couleur du thème. Les touches restent lisibles en Sombre, OLED et Clair.

Les images personnalisées acceptent maintenant les **GIF animés**, en plus des PNG et JPG. Un GIF peut être utilisé comme image commune, fond plein écran ou image de tuile. Cloudiste conserve le fichier animé dans ses données et l’inclut dans les sauvegardes `.cloudiste`. L’animation est arrêtée lorsque l’illustration n’est plus affichée.

Les GIF sont limités à 20 Mo et à 4096 × 4096 pixels pour éviter les fichiers excessifs. Pour préserver la fluidité et l’autonomie, privilégie des animations courtes, en 720p ou moins.

La version Android passe à `versionName 0.38.0` et `versionCode 46`.

## Tester

1. Ajoute une application au Dock depuis **Applications**.
2. Sur l’accueil, place-toi sur cette application et appuie sur **Y** ; refais le test avec un appui long au doigt.
3. Annule une première fois, puis confirme : l’application doit disparaître du Dock et rester installée.
4. Dans **Applications**, ouvre **Rechercher** et contrôle la lisibilité du clavier dans les trois thèmes.
5. Dans la personnalisation d’un service, choisis un GIF animé pour la tuile puis pour le fond.
6. Vérifie l’animation dans les trois modes d’affichage et après un retour à l’accueil.
7. Exporte puis restaure une sauvegarde contenant un GIF.
