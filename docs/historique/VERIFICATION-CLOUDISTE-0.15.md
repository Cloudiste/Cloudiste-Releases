# Vérification — Cloudiste 0.15.0

Contrôles effectués le 5 septembre 2026 sur l’émulateur tablette Android API 35, en paysage 2560 × 1600.

## Compilation et intégration

- Application et APK de test : **BUILD SUCCESSFUL**.
- Lint : **0 erreur, 24 avertissements et 1 suggestion**.
- Version 0.15.0, versionCode 15, minSdk 29 et targetSdk 37.
- Aucune nouvelle dépendance ni permission Android.
- **132 contrôles d’intégration réussis** : 8 détection, 21 lancement, 24 WebView, 29 réglages, 29 personnalisation, 11 gestes de l’accueil et 10 contrôles du catalogue Découvrir.
- Le catalogue contient exactement dix identifiants uniques et dix adresses HTTPS.
- Les packages de Shadow PC, Moonlight, Steam Link, Parsec et Antstream Arcade correspondent aux fiches Google Play vérifiées.
- Amazon Luna et Xbox Cloud Gaming restent volontairement sans bouton Google Play dans le catalogue.

## Contrôles d’interface

Le scénario du dock a réussi **12 contrôles** : les cinq pictogrammes restent dans un dock compact centré, Quitter reste en haut à droite et la navigation directionnelle atteint Découvrir.

Le scénario Découvrir a réussi **5 contrôles de parcours** :

1. Découvrir est atteint depuis le dock à la manette.
2. L’écran et son titre s’ouvrent correctement.
3. Les premiers services sont immédiatement visibles.
4. Un glissement vertical atteint la fin de la liste au doigt.
5. Après ce glissement, la manette reprend le focus et atteint Antstream Arcade en le gardant visible.

Un essai d’ouverture réelle a également confirmé que l’action GeForce NOW ouvre le navigateur et que son action Google Play ouvre l’application Play Store de l’émulateur.

## Points à valider sur la console

- La taille et la lisibilité du dock avec ses cinq pictogrammes.
- Le défilement régulier avec la manette physique utilisée par la console.
- Le navigateur et le magasin réellement installés sur l’appareil.
- La cohérence des fiches Google Play selon le pays et la compatibilité matérielle.

## Reproduire les contrôles

```sh
./gradlew :app:assembleDebug :app:assembleDebugAndroidTest :app:lintDebug
adb -s emulator-5554 install -r app/build/outputs/apk/debug/app-debug.apk
adb -s emulator-5554 install -r app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk
adb -s emulator-5554 shell am instrument -w com.example.cloudgaminglauncher.test/com.example.cloudgaminglauncher.DetectionChecks
python3 checks/verify_home_dock_ui.py --serial emulator-5554 --output work/home-dock-015
python3 checks/verify_discover_ui.py --serial emulator-5554 --output work/discover-015
```

Suis le [guide Cloudiste 0.15](CLOUDISTE-0.15.md) pour le test sur appareil réel.
