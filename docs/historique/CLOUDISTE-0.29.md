# Cloudiste 0.29.0 — Sauvegarde et récupération

Cette version prépare les essais bêta en permettant de conserver puis de restaurer toute la personnalisation de Cloudiste. Les fichiers restent sur l’appareil ou dans l’emplacement choisi avec le sélecteur Android. Cloudiste ne les envoie vers aucun serveur.

## Ce que contient une sauvegarde

Le fichier `.cloudiste` contient :

- les services ajoutés manuellement, leur visibilité et leur ordre ;
- les services ajoutés depuis Découvrir et les modes de lancement choisis ;
- les applications épinglées au dock ;
- le thème, le mode d’affichage de l’accueil et le choix du logo Cloudiste ;
- les fonds personnalisés des tuiles et du mode plein écran, avec leurs images.

Les applications Android elles-mêmes ne sont pas copiées. Après restauration sur un autre appareil, elles doivent toujours être installées séparément.

## Exporter

1. Ouvre **Réglages** depuis le dock de l’accueil.
2. Dans **Sauvegarde et récupération**, sélectionne **Exporter une sauvegarde** au doigt ou à la manette.
3. Choisis le dossier et le nom du fichier dans le sélecteur Android, puis valide.
4. Cloudiste confirme le nombre d’images sauvegardées.

## Importer

1. Ouvre **Réglages > Sauvegarde et récupération > Importer une sauvegarde**.
2. Sélectionne un fichier `.cloudiste` précédemment exporté.
3. La configuration importée remplace la configuration courante. Cloudiste contrôle le format et les images avant d’appliquer le changement.
4. Reviens à l’accueil pour vérifier l’ordre, le thème, le dock et les fonds.

Une archive inconnue, incomplète ou trop volumineuse est refusée sans être appliquée.

## Réinitialiser

**Réinitialiser Cloudiste** ouvre une confirmation. **Annuler** reçoit le focus initial afin d’éviter un effacement involontaire. La validation efface les préférences, services manuels et images personnalisées, puis restaure la configuration initiale. Il est conseillé d’exporter une sauvegarde avant ce test.

## Retrait du launcher Android par défaut

Cloudiste 0.29 est de nouveau une application Android classique. Sa déclaration ne contient plus la catégorie `HOME` et ses réglages ne proposent plus de devenir l’accueil principal. Cette fonction expérimentale reviendra après publication et validation sur un ensemble plus large d’appareils. La mise à jour depuis la 0.27 conserve les préférences existantes.

## Validation sur appareil réel

1. Installe l’APK 0.29 par-dessus la version précédente et vérifie que tes réglages sont conservés.
2. Exporte une sauvegarde dans Téléchargements.
3. Modifie un élément visible, par exemple le thème, l’ordre d’une tuile ou un fond.
4. Importe la sauvegarde et vérifie que l’état précédent revient.
5. Ouvre de nouveau l’import puis annule le sélecteur Android : l’application doit rester utilisable.
6. Ouvre la confirmation de réinitialisation et appuie sur **B** : aucune donnée ne doit changer.
7. Après avoir conservé la sauvegarde, confirme une réinitialisation et vérifie le retour à l’état initial.
8. Vérifie chaque action une fois à la manette et une fois au doigt.

Arrête-toi après ces essais et signale tout écart avant la prochaine version.
