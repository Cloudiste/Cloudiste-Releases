# Cloudiste 0.55.1 — Sons d’interface

Cette version ajoute une identité sonore originale aux interactions de Cloudiste, sans reprendre de sons propriétaires.

## Nouveautés

- son court lors d’un déplacement au clavier, à la croix ou au stick ;
- sons distincts pour valider, revenir, changer de mode et terminer un appui long ;
- retour sonore commun aux boutons tactiles et à la navigation manette ;
- limitation des répétitions rapides pour conserver un rendu discret ;
- activation générale et volume Discret, Normal ou Prononcé dans `Réglages > Apparence` ;
- respect du mode silencieux de l’appareil ;
- sauvegarde et restauration des préférences sonores ;
- textes français, anglais et espagnols.

## Technique

Les cinq sons sont des créations synthétiques stéréo intégrées à l’application. Leur palette feutrée utilise des attaques arrondies, de légères harmoniques et très peu de résonance. `SoundPool` les précharge en mémoire avec l’usage Android `USAGE_ASSISTANCE_SONIFICATION`, adapté aux retours d’interface courts.

## Version

- Nom : `0.55.1`
- Code : `76`
