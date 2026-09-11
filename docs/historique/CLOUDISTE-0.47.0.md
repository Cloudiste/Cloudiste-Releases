# Cloudiste 0.47.0 — Logos personnalisables et nouveaux services

Cette version permet de choisir le logo affiché sur chaque tuile et ajoute OpenNOW ainsi que Better xCloud au catalogue **Découvrir**.

## Logos

Un appui long sur une tuile ouvre sa personnalisation. La nouvelle rubrique **Logo de la tuile** propose :

- le logo fixe d’origine ;
- l’animation Cloudiste propre au service ;
- une image personnelle PNG, JPG ou WebP ;
- un GIF personnel conservé avec son animation ;
- le masquage du logo et la suppression du fichier personnel.

Le choix s’applique aux tuiles détaillées, aux tuiles réduites et au mode plein écran. Les anciens réglages de logos animés sont repris automatiquement. Les logos personnels sont inclus dans la sauvegarde ZIP et restaurés avec les autres médias.

## Nouveaux services

- **OpenNOW** : détection du package `com.opencloudgaming.opennow`, fiche Découvrir, accès Google Play, logo officiel, fond embarqué et animation de 3,3 secondes.
- **Better xCloud** : détection du package `com.redphx.betterxc` vérifié dans l’APK officiel 0.24.2, fiche Découvrir pointant vers la release GitHub, logo officiel, fond embarqué et animation de 4,7 secondes.

Ces services restent facultatifs : ils peuvent être ajoutés à l’accueil depuis leur fiche Découvrir.

## Test conseillé

1. Ouvre **Découvrir**, puis les fiches OpenNOW et Better xCloud.
2. Ajoute chaque service à l’accueil et vérifie la détection de son application.
3. Fais un appui long sur une tuile, puis ouvre **Logo de la tuile**.
4. Essaie successivement le logo fixe, l’animation Cloudiste et un GIF personnel.
5. Contrôle les trois modes d’affichage, ferme Cloudiste puis vérifie que le choix est conservé.
6. Exporte et restaure une sauvegarde contenant un logo personnel.

Version : `0.47.0` — code : `66`.
