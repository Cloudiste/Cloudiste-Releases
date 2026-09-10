# Vérification — Cloudiste 0.11.0

Contrôles effectués le 4 septembre 2026 sur l’émulateur tablette Android API 35. Cette version attend sa validation sur console réelle.

## Compilation

- Application et APK de test : **BUILD SUCCESSFUL**.
- Lint : **0 erreur, 22 avertissements et 1 suggestion**, sans baseline. Les avertissements restent ceux des versions précédentes.
- Version 0.11.0, versionCode 11, minSdk 29 et targetSdk 37.
- Aucune nouvelle dépendance, permission ou déclaration de package.

## Intégration — 113 contrôles réussis

Le runner exécute 8 contrôles de détection, 21 de lancement, 24 du lecteur WebView, 27 des réglages, 29 de personnalisation et 4 du nouvel appui long.

Les nouveaux contrôles couvrent A court, une seule personnalisation lorsque A se répète, le repli par durée pour une manette sans répétition et la conservation du comportement normal sur un écran sans action longue.

## Interface — 13 contrôles réussis

Le parcours `checks/verify_long_press_ui.py` vérifie le lancement normal avec A court, l’ouverture de la personnalisation PlayStation avec A maintenu pendant 800 ms, le retour du focus, puis l’ouverture de la personnalisation Xbox par un appui tactile de 800 ms. Il contrôle aussi l’absence de lancement tactile parasite et la présence de la nouvelle aide.

Les captures ont été inspectées : chaque geste ouvre l’écran portant le nom du bon service. Le script sauvegarde les préférences avant l’essai et les restaure dans un `finally`.

**Total : 126 contrôles réussis**, en plus de la compilation et de Lint.

## Limites et reproduction

Les événements sont injectés par Android. Le test couvre une manette simulée sans répétition ; l’intégration couvre aussi la répétition. Cela ne remplace pas le ressenti d’une manette physique.

```sh
./gradlew :app:assembleDebug :app:assembleDebugAndroidTest :app:lintDebug
adb -s emulator-5554 install -r app/build/outputs/apk/debug/app-debug.apk
adb -s emulator-5554 install -r app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk
adb -s emulator-5554 shell am instrument -w com.example.cloudgaminglauncher.test/com.example.cloudgaminglauncher.DetectionChecks
python3 checks/verify_long_press_ui.py --serial emulator-5554 --output work/long-press
```

Le script refuse un appareil réel. En cas d’interruption avant restauration, remettre `cache/cloudiste-011-ui-backup.preferences_pb` à la place de `files/datastore/launcher_settings.preferences_pb` après avoir arrêté Cloudiste.

Suis ensuite les sept essais du [guide Cloudiste 0.11](CLOUDISTE-0.11.md) sur ta console.
