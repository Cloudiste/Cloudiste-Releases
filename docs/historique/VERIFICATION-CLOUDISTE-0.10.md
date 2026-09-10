# Vérification — Cloudiste 0.10.0

Essais du 4 septembre 2026, sur émulateur tablette Android API 35. Les nouvelles fonctions attendent leur validation sur console réelle.

## Compilation

Application, APK de test et Lint : **BUILD SUCCESSFUL**. Lint signale **0 erreur, 22 avertissements et 1 suggestion**, sans baseline. Les avertissements restent ceux des versions d’outils existantes, des orientations fixes, de la sauvegarde Android, de ressources et de suggestions Kotlin/WebView.

La vérification du fichier unique de packages réussit. Aucun package de fournisseur supplémentaire ni aucune dépendance n’est ajouté. Le numéro de version est 0.10.0, versionCode 10 ; l’identifiant Android reste identique.

## Intégration — 109 contrôles réussis

Le runner exécute 8 contrôles de détection, 21 de lancement, 24 du lecteur web, 27 des réglages et 29 de personnalisation.

Les neuf contrôles supplémentaires couvrent :

- la lecture d’un fond au format 0.9.0 comme image commune ;
- la protection des services fournis contre une suppression par le dépôt ;
- la sélection de fichiers distincts pour le fond et la tuile ;
- le refus d’un chemin de tuile invalide ;
- le passage au mode commun et la conservation de l’image distincte inactive ;
- le retrait du fond sans perdre l’image de tuile, avec nettoyage de l’ancien fichier ;
- la suppression du service personnel avec nettoyage de son image de tuile.

Les vérifications existantes de relecture depuis une nouvelle instance DataStore couvrent maintenant les deux fichiers et le mode. Les essais du ViewModel emploient un dépôt DataStore temporaire et des copies d’images de test : les données réelles de l’utilisateur restent intactes. L’application Android choisie reste installée après suppression du service.

## Parcours d’interface

Le script `checks/verify_cloudiste_010_ui.py` sauvegarde les préférences de l’émulateur, utilise un service de test « Clock » et deux images synthétiques, puis restaure les données et l’affichage. Aucune alarme ni aucun réglage de l’application Clock n’est modifié.

**39 contrôles d’interface réussis : 33 pour le profil complet et 6 en format compact.** Avec l’intégration, cela représente **148 contrôles réussis**. Les captures compactes ont été inspectées : boutons lisibles, focus entièrement visible et défilement fonctionnel. Les journaux et captures retenus sont dans `verification/cloudiste-0.10/`. Les captures confirment un fond rouge et une tuile bleue, puis deux aperçus rouges en mode commun. La séparation des images reste visible après arrêt et relance du processus.

Le profil complet importe un fond rouge et une tuile bleue, alterne entre les deux modes à la manette et au toucher, revient à l’accueil et relance le processus. Il vérifie l’annulation du sélecteur de fichiers, l’accès direct à la suppression, l’annulation de cette confirmation, puis la suppression d’un service masqué. Les quatre services fournis et l’application Android sont conservés ; les deux copies privées sont nettoyées.

Le profil compact vérifie le nouveau sélecteur de mode, l’accès à l’image de tuile, le défilement jusqu’au retrait du fond et le retour au bon bouton. Il utilise 1280 × 800, une densité de 240 et une police à 130 %.

Les essais de manette et de toucher utilisent des événements Android injectés. Ils ne remplacent pas une vraie manette, le sélecteur Android du constructeur ni un redémarrage de la console. Le guide décrit les essais matériels à effectuer.

## Reproduire

```sh
./gradlew :app:assembleDebug :app:assembleDebugAndroidTest :app:lintDebug
python3 checks/verify_package_config.py
adb -s emulator-5554 install -r app/build/outputs/apk/debug/app-debug.apk
adb -s emulator-5554 install -r app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk
adb -s emulator-5554 shell am force-stop com.example.cloudgaminglauncher
adb -s emulator-5554 shell am instrument -w com.example.cloudgaminglauncher.test/com.example.cloudgaminglauncher.DetectionChecks
python3 checks/verify_cloudiste_010_ui.py --serial emulator-5554 --profile full --output work/ui-010
python3 checks/verify_cloudiste_010_ui.py --serial emulator-5554 --profile compact --output work/ui-010-compact
```

Exécuter les profils successivement. Le profil complet attend Clock et le sélecteur Android en anglais de l’émulateur de référence. Si le script est interrompu brutalement, restaurer la copie `cache/cloudiste-010-ui-backup.preferences_pb` vers `files/datastore/launcher_settings.preferences_pb` dans les données de l’application après avoir arrêté son processus. Le script refuse de démarrer tant que cette sauvegarde existe.

Les scripts et rapports 0.9 restent historiques ; leurs anciens libellés ne correspondent plus à cette version. Le lecteur cloud et les abonnements ne font pas l’objet de nouvelles parties réelles dans ces essais.
