# Cloudiste 0.54.0 — Animations de l’accueil

Cette version introduit un premier langage de mouvement commun aux interactions tactiles et à la manette. Les animations restent courtes afin de donner du relief à l’interface sans ralentir l’ouverture des services.

## Tuiles et focus

- Une tuile sélectionnée se soulève légèrement, grandit et reçoit un halo associé à la couleur du service.
- Le passage d’une sélection à l’autre utilise un ressort amorti plutôt qu’une variation linéaire.
- Une pression tactile comprime immédiatement la cible, puis produit un petit rebond au relâchement.
- L’épaisseur et la couleur de la bordure ainsi que l’ombre évoluent progressivement.
- Les mêmes règles s’appliquent aux services, aux dossiers, au Dock et aux actions placées dans les angles de l’accueil.

## Appui long et déplacement

- La progression de l’appui long reste visible au centre de la cible.
- Une tuile saisie se soulève davantage et conserve son mouvement d’inclinaison pendant le déplacement.
- La cible de dépôt s’élève pour indiquer clairement la future position.
- Le délai de saisie existant est conservé afin que le défilement vertical au doigt reste prioritaire.

## Mode plein écran

Les flèches tactiles gauche et droite se compriment sous le doigt et rebondissent au relâchement. La transition horizontale existante entre les services est conservée.

## Accessibilité et performances

Le réglage **Réglages › Accessibilité › Animations réduites** désactive les changements d’échelle, les élévations et les mouvements élastiques. Les états de focus, les bordures et les actions restent disponibles immédiatement.

Les calques de halo épousent la taille déjà calculée de chaque bouton. Ils ne peuvent donc pas étirer les commandes des réglages, de l’assistant ou des autres pages qui réutilisent le même composant de focus.

Cette première phase concerne uniquement l’accueil. Elle doit être validée sur tablette, smartphone et manette avant d’étendre le langage de mouvement aux autres menus.
