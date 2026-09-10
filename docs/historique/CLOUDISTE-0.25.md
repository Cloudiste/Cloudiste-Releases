# Cloudiste 0.25.0 — Animations des gestes

Cette version rend les deux gestes principaux de l’accueil plus faciles à comprendre : l’appui prolongé montre sa progression et la tuile déplacée reste visuellement attachée au doigt.

## Appui prolongé

Sur une tuile, un appui prolongé ouvre toujours la personnalisation du service. Pendant l’attente :

- la carte se resserre légèrement ;
- un cercle coloré se remplit au centre ;
- le relâchement avant la fin annule simplement l’appui prolongé ;
- une fois le cercle rempli, la personnalisation s’ouvre une seule fois.

Cette animation fonctionne au doigt et lorsque le bouton **A** de la manette est maintenu. Le bouton **Y** reste le raccourci immédiat vers la même personnalisation.

## Déplacement des tuiles

Après le début d’un glissement, la tuile :

- grandit légèrement et passe au-dessus des autres ;
- suit le doigt avec une petite inclinaison liée au déplacement horizontal ;
- conserve un contour accentué pendant tout le geste.

La tuile visée pulse et reçoit un contour plus fort. Au relâchement, les deux positions sont échangées et le nouvel ordre est enregistré dans DataStore. Il reste donc identique après un redémarrage de Cloudiste.

Ces états possèdent également une description d’accessibilité afin qu’Android puisse annoncer le service déplacé et sa cible.

## Essai sur appareil réel

1. Sur une tuile, appuie brièvement avec le doigt : le service doit s’ouvrir sans afficher durablement le cercle.
2. Maintiens le doigt : observe le cercle, puis vérifie l’ouverture de la personnalisation.
3. Reviens et maintiens **A** sur une tuile : le même retour visuel doit apparaître.
4. Appuie sur **Y** : la personnalisation doit s’ouvrir immédiatement.
5. Fais glisser une tuile vers une autre : vérifie la surélévation de la carte et l’indication de la cible.
6. Relâche, ferme puis rouvre Cloudiste : le nouvel ordre doit être conservé.
7. Refais un parcours de l’accueil uniquement à la manette, puis uniquement au toucher.

