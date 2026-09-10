# Cloudiste 0.39.3 — Reprise fiable des fonds vidéo

Cette version corrige le fond noir intermittent avec une vidéo utilisée comme fond général.

- Le lecteur libère son décodeur lorsque Cloudiste passe en arrière-plan.
- La vidéo est préparée à nouveau au retour sur la page d’accueil.
- La lecture reprend automatiquement lorsque l’écran redevient actif.
- Une image extraite du début de la vidéo s’affiche pendant la préparation du lecteur.
- Le cadrage Remplir ou Image entière est appliqué à cette image d’attente comme à la vidéo.

La version Android passe à `versionName 0.39.3` et `versionCode 50`.

## Vérification sur appareil

1. Choisis une vidéo comme fond général.
2. Reviens plusieurs fois entre la page de personnalisation, les réglages et l’accueil.
3. Mets Cloudiste en arrière-plan puis ouvre-le de nouveau.
4. Vérifie qu’une image apparaît immédiatement, puis que l’animation démarre.
