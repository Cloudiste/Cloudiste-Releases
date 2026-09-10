# Vérification — Cloudiste 0.12.0

Contrôles effectués le 4 septembre 2026 sur l’émulateur tablette Android API 35.

## Compilation et intégration

- Application et APK de test : **BUILD SUCCESSFUL**.
- Lint : **0 erreur, 22 avertissements et 1 suggestion**, sans baseline.
- Version 0.12.0, versionCode 12, minSdk 29 et targetSdk 37.
- Aucune nouvelle dépendance, permission ou déclaration de package.
- **113 contrôles d’intégration réussis** : détection, lancements, WebView, réglages, personnalisation et appui long.

Les cinq ressources vectorielles sont compilées dans l’APK. La configuration des packages reste inchangée et provient toujours du fichier unique prévu à cet effet.

## Parcours d’interface

**14 contrôles d’interface réussis. Total : 127 contrôles réussis**, en plus de la compilation et de Lint.

Le script `checks/verify_home_icons_ui.py` contrôle qu’il existe exactement un pictogramme accessible pour chacune des cinq actions et qu’aucun texte visible n’est placé dans leur nœud. Il ouvre réellement Réglages, Applications, Ajouter un service et les réglages système, puis vérifie Quitter. Applications est activé par un toucher injecté ; les autres parcours utilisent la manette.

La capture a été inspectée : roue dentée, grille, plus, robot Android et bouton marche/arrêt sont nets, centrés et suffisamment contrastés. La bordure de focus reste entièrement visible.

Le script sauvegarde les préférences avant le parcours et les restaure dans un `finally`. Il ne modifie aucun réglage système.

## Reproduire

```sh
./gradlew :app:assembleDebug :app:assembleDebugAndroidTest :app:lintDebug
adb -s emulator-5554 install -r app/build/outputs/apk/debug/app-debug.apk
adb -s emulator-5554 install -r app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk
adb -s emulator-5554 shell am instrument -w com.example.cloudgaminglauncher.test/com.example.cloudgaminglauncher.DetectionChecks
python3 checks/verify_home_icons_ui.py --serial emulator-5554 --output work/home-icons
```

Le script refuse un appareil réel. En cas d’interruption avant restauration, remettre `cache/cloudiste-012-ui-backup.preferences_pb` à la place de `files/datastore/launcher_settings.preferences_pb` après l’arrêt de Cloudiste.

La validation sur console doit confirmer le confort des pictogrammes avec une vraie manette, le toucher et, si utilisé, le service d’accessibilité Android. Suis le [guide Cloudiste 0.12](CLOUDISTE-0.12.md).
