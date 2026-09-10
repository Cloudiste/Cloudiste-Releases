# Cloudiste 0.39.4 — Passage de l’image d’attente à la vidéo

Cette version corrige l’image de fond qui restait fixe dans la 0.39.3.

- L’image d’attente et la vidéo sont gérées dans un composant unique.
- L’image reste affichée pendant la préparation du décodeur.
- Elle disparaît seulement lorsque la première trame vidéo est effectivement rendue.
- En cas d’erreur ou de retour depuis un autre écran, l’image d’attente réapparaît jusqu’à la reprise de la vidéo.
- Le cadrage Remplir ou Image entière reste appliqué aux deux rendus.

La version Android passe à `versionName 0.39.4` et `versionCode 51`.
