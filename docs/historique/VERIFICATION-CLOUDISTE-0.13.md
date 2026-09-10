# Vérification — Cloudiste 0.13.0

Contrôles effectués le 5 septembre 2026 sur l’émulateur tablette Android API 35.

## Compilation et contrôles automatiques

- Application et APK de test : **BUILD SUCCESSFUL**.
- Lint : **0 erreur et 22 avertissements**, tous déjà connus et sans erreur liée à cette évolution.
- Version 0.13.0, versionCode 13, minSdk 29 et targetSdk 37.
- Aucune nouvelle dépendance, permission ou déclaration de package.
- **115 contrôles d’intégration réussis** : 8 détection, 21 lancement, 24 WebView, 29 réglages, 29 personnalisation et 4 appui long.
- Le nouveau contrôle de réglages vérifie que le glissement réordonne les services, enregistre l’ordre et préserve la position d’un service masqué.

## Parcours d’interface

Les parcours réels suivants ont été effectués avec les gestes Android et les événements de manette :

- l’écran Applications affiche 22 résultats dans une liste continue, sans commande de pagination ;
- un glissement vertical remplace les premières applications visibles par les suivantes ;
- le même résultat est obtenu dans Ajouter un service ;
- huit déplacements vers le bas à la manette font défiler Ajouter un service jusqu’à YT Kids, avec son cadre de focus entièrement visible ;
- GeForce NOW a été glissé de la première à la troisième position sans ouvrir le service ;
- l’ordre `Boosteroid, Xbox Cloud Gaming, GeForce NOW, PlayStation Plus Premium` a été retrouvé après l’arrêt et le redémarrage de l’application ;
- un maintien immobile de 800 ms sur Boosteroid ouvre toujours son écran de personnalisation.

Les données de l’émulateur ont été remises à zéro avant ces essais. La validation sur appareil réel doit surtout confirmer le confort du geste selon la taille physique de l’écran et la sensibilité tactile du constructeur.

## Reproduire les contrôles automatiques

```sh
./gradlew :app:assembleDebug :app:assembleDebugAndroidTest :app:lintDebug
adb -s emulator-5554 install -r app/build/outputs/apk/debug/app-debug.apk
adb -s emulator-5554 install -r app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk
adb -s emulator-5554 shell am instrument -w com.example.cloudgaminglauncher.test/com.example.cloudgaminglauncher.DetectionChecks
```

Suis ensuite les neuf essais du [guide Cloudiste 0.13](CLOUDISTE-0.13.md) sur la console réelle.
