# Cloudiste 0.30.2 — Défilement tactile et réglages Android

Cette correction traite les deux problèmes observés sur l’accueil.

## Défilement et déplacement des tuiles

Une tuile n’est plus saisie dès que le doigt commence à bouger. Le geste dépend maintenant de sa durée :

- un glissement vertical immédiat fait défiler l’accueil ;
- un maintien d’environ un quart de seconde, suivi d’un glissement, déplace la tuile ;
- un toucher simple continue d’ouvrir le service ;
- un appui long sans déplacement continue d’ouvrir sa personnalisation.

Le délai choisi est de 220 ms. Il reste assez court pour réorganiser rapidement l’accueil, tout en laissant Android reconnaître naturellement l’intention de faire défiler la liste.

## Ouverture des réglages Android

Le bouton du dock essaie désormais plusieurs destinations système compatibles, dans cet ordre : réglages généraux associés au package système, activité principale explicite, réglages généraux Android, réglages des applications, puis fiche système de Cloudiste. Si une destination n’existe pas sur l’appareil, la suivante est utilisée automatiquement.

Cette stratégie vise notamment l’Alldocube iPlay Mini 80 Ultra, dont l’application Réglages peut réagir différemment de l’Android standard.

## Test sur l’appareil réel

Installe l’APK 0.30.2 par-dessus la version précédente afin de conserver tes réglages.

1. Ajoute assez de services pour que l’accueil puisse défiler verticalement.
2. Pose le doigt sur une tuile et glisse immédiatement vers le haut ou le bas : la page doit défiler et l’ordre des tuiles ne doit pas changer.
3. Maintiens une tuile environ un quart de seconde, puis déplace le doigt : la tuile doit se soulever et pouvoir changer de position.
4. Vérifie qu’un toucher simple ouvre toujours le service et qu’un appui long immobile ouvre sa personnalisation.
5. Appuie sur le pictogramme **Réglages Android** du dock : les réglages système doivent s’ouvrir.
6. Reviens avec le bouton Retour d’Android et vérifie que Cloudiste reste utilisable.

La vérification sur l’Alldocube est nécessaire pour confirmer le second correctif, car l’émulateur utilise l’application Réglages Android standard.
