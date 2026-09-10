# Cloudiste 0.46.1 — Rendu animé et tuiles réduites

Cette version corrige l’intégration visuelle des logos animés et l’alignement du mode tuiles réduites.

## Changements

- Le fond animé a été séparé du logo : Cloudiste affiche désormais le fond fixe avec son cadrage habituel, puis superpose uniquement le logo animé.
- Le logo animé conserve la même échelle que le logo statique et ne reçoit plus le voile d’assombrissement du fond.
- Les onze animations restent différentes et conservent leurs durées propres.
- En mode tuiles réduites, les lignes sont centrées verticalement lorsqu’elles tiennent dans la zone disponible.
- Si le nombre de tuiles dépasse la hauteur disponible, le défilement vertical reste actif.

## Test conseillé

1. Active **Visuel animé** sur une tuile et compare son fond, la taille de son logo et sa luminosité avec une tuile statique.
2. Passe en mode tuiles réduites et vérifie que la rangée se trouve au milieu de l’espace entre l’en-tête et le Dock.
3. Affiche assez de services pour créer plusieurs lignes et vérifie que le défilement reste possible.
4. Contrôle le résultat au doigt et à la manette.

Version : `0.46.1` — code : `63`.
