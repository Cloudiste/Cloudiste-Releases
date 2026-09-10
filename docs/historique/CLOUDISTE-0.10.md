# Cloudiste 0.10.0 — Suppression et images distinctes

Version historique validée par l’utilisateur. Le raccourci par appui long est décrit dans [Cloudiste 0.11.0](CLOUDISTE-0.11.md).

Cette version ajoute un accès direct à la suppression des services personnels et un choix d’images par service. Les fonctions précédentes restent disponibles à la manette et au toucher.

## Supprimer un service ajouté

1. Depuis l’accueil, ouvre **Réglages** avec le bouton ou **Y / Start**.
2. Dans le service ajouté, sélectionne **Supprimer le service**, juste après **Afficher**.
3. Une confirmation affiche le nom du service. **Annuler** est sélectionné au départ ; **B** annule également. À la manette, **Haut**, puis **A**, confirme la suppression.

Le service disparaît de Cloudiste, y compris s’il était masqué. Son ordre, sa visibilité, sa priorité et ses images personnelles sont nettoyés. L’application Android reste installée et accessible depuis **Applications**. Tu peux la réajouter ultérieurement.

Le bouton reste également disponible dans **Personnaliser**. Les quatre services fournis ne proposent pas cette suppression ; ils peuvent toujours être masqués.

## Une image commune ou deux images différentes

Ouvre **Réglages → Personnaliser** pour le service choisi. Deux aperçus identifient le **Fond de l’accueil** et l’**Image de la tuile**.

| Choix | Résultat |
| --- | --- |
| **Images : image commune** | **Choisir l’image commune** change à la fois le fond et l’image de la tuile. |
| **Images : images différentes** | **Choisir l’image du fond** et **Choisir l’image de la tuile** importent chacun leur propre fichier. |

Active le bouton **Images** avec A ou au toucher pour changer de mode. La tuile désigne la carte du service sur l’accueil ; le logo du service ou l’icône de son application reste superposé à cette image.

En revenant au mode commun, le fond devient aussi l’image de la tuile. L’image distincte choisie auparavant est conservée : repasser en mode différent la retrouve. Si tu n’en as pas encore choisi, la tuile utilise son apparence habituelle.

En mode différent, **Retirer le fond** conserve l’image de la tuile ; **Retirer l’image de la tuile** conserve le fond. En mode commun, **Retirer l’image commune** enlève l’image actuellement utilisée aux deux endroits. Le cadrage, la position et l’assombrissement restent des réglages communs aux deux emplacements ; retirer une image ne réinitialise pas ces réglages.

Annuler le sélecteur Android conserve les images précédentes. Les fichiers choisis sont copiés dans le stockage privé de Cloudiste, comme en 0.9.0 : déplacer leur original ne casse pas l’affichage.

## Comprendre le changement de code

`ServiceWallpaper` représente les réglages visuels d’un service. Il comporte désormais deux propriétés supplémentaires : `sameImage`, un booléen qui indique si les images sont communes, et `tileFileName`, le nom de la copie destinée à la tuile. `fileName` reste le fond. La fonction `forTile()` choisit le bon fichier selon le mode.

Les anciens enregistrements ne possèdent pas ces nouvelles valeurs. Leur lecture utilise donc `sameImage = true` : ton ancien fond continue d’habiller les deux emplacements. Les données sont toujours enregistrées dans DataStore, sans nouvelle bibliothèque.

`PersonalizeViewModel` gère les imports, le changement de mode et la suppression. Le nom d’un fichier n’est supprimé du stockage que lorsqu’aucun service ne le référence encore, y compris comme image distincte temporairement inactive. La suppression des préférences d’un service reste une opération DataStore unique.

`SettingsScreen` ajoute le bouton de suppression uniquement pour les ajouts personnels. Il ouvre la même confirmation et utilise le même ViewModel que l’écran de personnalisation : la logique de suppression reste centralisée. L’identifiant du service est vérifié avant de modifier les données.

Le choix « fond ou tuile » est conservé pendant le sélecteur Android, même si Android recrée l’écran. Le code sait ainsi à quel emplacement affecter le fichier reçu.

## Installer et tester sur ta console

Installe **Cloudiste-0.10.0-debug.apk** par-dessus la version précédente, avec la même signature de développement, ou ouvre le dossier **Cloudiste** extrait du ZIP dans Android Studio et lance **Run ▶**. L’identifiant Android reste identique pour conserver les données.

1. Retrouve tes anciens services, leur ordre et leurs fonds. Une ancienne image doit apparaître en mode commun.
2. Ajoute une application de test depuis **Ajouter un service**.
3. Dans ses réglages, ouvre **Supprimer le service**, puis annule avec B : le service doit rester présent et le focus revenir au bouton.
4. Dans **Personnaliser**, choisis une image commune et vérifie les deux aperçus.
5. Passe en mode différent et choisis une seconde image pour la tuile. Vérifie l’accueil et le changement de fond quand tu sélectionnes ce service.
6. Reviens au mode commun, puis au mode différent : la seconde image doit être retrouvée.
7. Ferme complètement Cloudiste, puis relance : les deux images et le mode doivent être conservés.
8. En mode différent, retire uniquement le fond : l’image de la tuile doit rester visible.
9. Masque le service personnel, puis supprime-le depuis Réglages. Vérifie sa disparition et la présence de l’application dans le tiroir.
10. Répète le changement de mode et une suppression au toucher, puis reprends à la manette.

Les écrans de sélection de fichiers appartiennent à Android ; leur prise en charge de la manette dépend de la console. Les contrôles effectués sur émulateur sont détaillés dans [le rapport de vérification](VERIFICATION-CLOUDISTE-0.10.md).

Cette livraison attend ta validation sur appareil réel.
