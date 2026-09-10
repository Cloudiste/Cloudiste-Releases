# Vérification — Cloudiste 0.16.0

Contrôles effectués le 5 septembre 2026 sur l’émulateur tablette Android API 35, en paysage 2560 × 1600.

## Compilation et intégration

- Application et APK de test : **BUILD SUCCESSFUL**.
- Lint : **0 erreur, 25 avertissements et 1 suggestion**.
- Version 0.16.0, versionCode 16, minSdk 29 et targetSdk 37.
- Aucune nouvelle dépendance ni permission Android.
- **135 contrôles d’intégration réussis** : 8 détection, 21 lancement, 24 WebView, 29 réglages, 29 personnalisation, 11 gestes de l’accueil et 13 contrôles de Découvrir.
- Le catalogue contient exactement onze identifiants uniques et onze adresses HTTPS.
- Chaque service possède une présentation et une information sur son mode d’accès.
- Le package Blacknut vérifié est `com.blacknut.app`.

## Contrôles de l’interface

Le scénario de l’accueil a réussi **12 contrôles** : le dock reste compact et centré, ses cinq actions sont accessibles et Quitter reste en haut à droite.

Le nouveau scénario Découvrir a réussi **11 contrôles** :

- ouverture de Découvrir depuis le dock ;
- présence des onze services ;
- affichage des premières lignes et de leurs logos ;
- défilement tactile jusqu’à Blacknut ;
- présence du logo Blacknut ;
- ouverture tactile de la fiche Blacknut ;
- présence des informations, de Retour, du site et de Google Play ;
- focus initial sur Retour ;
- navigation à la manette vers Site internet puis Google Play ;
- retour à la liste avec B.

Les captures 2560 × 1600 ont été inspectées. Les lignes restent lisibles, les logos ont une taille cohérente et la fiche réserve son bas d’écran aux deux destinations.

## Ouvertures externes

Depuis la fiche Blacknut :

- **Site internet** a ouvert Chrome ;
- **Google Play** a ouvert l’application Play Store sur l’émulateur.

## Reproduire

```sh
./gradlew :app:assembleDebug :app:assembleDebugAndroidTest :app:lintDebug
adb -s emulator-5554 install -r app/build/outputs/apk/debug/app-debug.apk
adb -s emulator-5554 install -r app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk
adb -s emulator-5554 shell am instrument -w com.example.cloudgaminglauncher.test/com.example.cloudgaminglauncher.DetectionChecks
python3 checks/verify_home_dock_ui.py --serial emulator-5554 --output work/home-dock-016
python3 checks/verify_discover_ui.py --serial emulator-5554 --output work/discover-016
```

La validation sur appareil réel doit confirmer le rendu selon la densité de l’écran, le comportement de la manette physique et la disponibilité régionale des fiches Google Play. Suis le [guide Cloudiste 0.16](CLOUDISTE-0.16.md).
