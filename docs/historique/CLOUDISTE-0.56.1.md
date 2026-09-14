# Cloudiste 0.56.1 — Musique d’ambiance

Cette version ajoute une composition originale, légère et aérienne aux écrans de Cloudiste. Elle évoque la sérénité des interfaces de consoles portables sans reprendre de mélodie ou d’élément sonore propriétaire.

## Nouveautés

- ambiance stéréo originale de 35 secondes jouée en boucle ;
- lecture continue pendant la navigation entre les écrans de Cloudiste ;
- pause automatique lorsqu’un jeu, un service ou une autre application passe au premier plan ;
- gestion du focus audio Android et atténuation temporaire à la demande du système ;
- activation générale dans `Réglages > Apparence` ;
- trois niveaux audibles : Très légère, Douce et Présente ;
- sauvegarde et restauration des préférences musicales ;
- textes français, anglais et espagnols.

## Technique

La musique est intégrée localement au format Opus. Elle ne nécessite ni connexion réseau ni service tiers. Un lecteur partagé évite les redémarrages entre les activités de Cloudiste et libère le focus audio dès que l’application quitte le premier plan.

## Version

- Nom : `0.56.1`
- Code : `78`
