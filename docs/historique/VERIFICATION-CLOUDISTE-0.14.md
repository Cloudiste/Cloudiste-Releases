# Vérification — Cloudiste 0.14.0

Contrôles effectués le 5 septembre 2026 sur l’émulateur tablette Android API 35, en paysage 2560 × 1600.

## Compilation et intégration

- Application et APK de test : **BUILD SUCCESSFUL**.
- Lint : **0 erreur et 22 avertissements**, sans nouvelle erreur liée à cette évolution.
- Version 0.14.0, versionCode 14, minSdk 29 et targetSdk 37.
- Aucune nouvelle dépendance, permission ou déclaration de package.
- **120 contrôles d’intégration réussis** : 8 détection, 21 lancement, 24 WebView, 29 réglages, 29 personnalisation et 9 gestes de l’accueil.
- Cinq nouveaux contrôles vérifient les trajets entre Quitter, les services et le dock.

## Géométrie et parcours d’interface

Le script `checks/verify_home_dock_ui.py` a réussi **11 contrôles d’interface** :

- les quatre actions sont dans le quart inférieur de l’écran ;
- le dock occupe environ 22 % de la largeur, donc reste compact ;
- son centre est aligné avec celui de l’écran ;
- Quitter est placé dans la zone supérieure droite ;
- le focus initial reste sur le premier service ;
- Haut rejoint Quitter et Bas revient vers les services ;
- Bas rejoint ensuite le dock ;
- Droite parcourt Réglages, Applications, Ajouter un service et Réglages Android.

La capture 2560 × 1600 a été inspectée : le dock est détaché des bords, ses quatre icônes sont lisibles et Quitter est aligné avec le titre. La bordure du focus ne touche ni le dock extérieur ni les barres système.

## Reproduire

```sh
./gradlew :app:assembleDebug :app:assembleDebugAndroidTest :app:lintDebug
adb -s emulator-5554 install -r app/build/outputs/apk/debug/app-debug.apk
adb -s emulator-5554 install -r app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk
adb -s emulator-5554 shell am instrument -w com.example.cloudgaminglauncher.test/com.example.cloudgaminglauncher.DetectionChecks
python3 checks/verify_home_dock_ui.py --serial emulator-5554 --output work/home-dock
```

La validation sur appareil réel doit confirmer la taille confortable du dock et de Quitter selon la densité d’écran de la console. Suis le [guide Cloudiste 0.14](CLOUDISTE-0.14.md).
