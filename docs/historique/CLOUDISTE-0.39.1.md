# Cloudiste 0.39.1 — Vidéos 4K et cadrage plein écran

Cette mise à jour corrige l’import et l’affichage des fonds vidéo sur les appareils compatibles.

## Changements

- La taille maximale d’une vidéo passe de 50 Mo à 250 Mo afin d’accepter les exports 4K courants.
- Le lecteur vidéo natif utilise désormais un rendu qui conserve les proportions de la vidéo.
- Le cadrage **Remplir** agrandit et recadre la vidéo au centre pour couvrir tout l’écran, y compris en 4:3, 16:10 et sur les formats très larges.
- Le cadrage **Image entière** reste disponible pour afficher toute la vidéo, avec des bandes éventuelles si les proportions diffèrent.
- Les limites des sauvegardes ont été adaptées pour inclure les fonds vidéo 4K.

La lecture 4K dépend toujours des formats vidéo pris en charge matériellement par l’appareil. Pour une compatibilité maximale, utilise une vidéo MP4 encodée en H.264 ou HEVC, d’une durée maximale d’une minute.

La version Android passe à `versionName 0.39.1` et `versionCode 48`.

## Vérification sur appareil

1. Installe l’APK 0.39.1 par-dessus la version précédente.
2. Dans **Réglages > Apparence**, choisis **Utiliser le fond général**, puis **Personnaliser le fond général**.
3. Importe la vidéo 4K qui échouait avec la version précédente.
4. Vérifie que **Cadrage : remplir** couvre tout l’écran sans déformer l’image.
5. Essaie le mode portrait large, 4:3 ou 16:10 disponible sur ton appareil et vérifie l’absence de bandes noires.
6. Passe sur **Cadrage : image entière** pour confirmer que ce choix affiche volontairement toute la vidéo.
