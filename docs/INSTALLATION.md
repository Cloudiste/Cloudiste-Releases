# Installation et mises à jour

## Installation manuelle

1. Ouvre la [dernière Release de Cloudiste](https://github.com/Cloudiste/Cloudiste-Releases/releases/latest).
2. Télécharge uniquement le fichier `Cloudiste-…-release.apk`.
3. Si Android le demande, autorise temporairement ton navigateur ou ton gestionnaire de fichiers à installer cette application.
4. Ouvre l’APK, puis choisis **Installer**.

Une mise à jour installée par-dessus Cloudiste conserve normalement les réglages lorsque l’identifiant de l’application et sa signature correspondent. Il est néanmoins conseillé d’exporter régulièrement une sauvegarde.

## Utiliser Cloudiste comme launcher Android

Cette fonction est facultative et ne s’active jamais automatiquement :

1. ouvre **Réglages › Launcher Android** dans Cloudiste ;
2. choisis **Choisir Cloudiste comme launcher** ;
3. confirme le choix dans l’écran officiel d’Android ;
4. teste le bouton Accueil avant de redémarrer l’appareil.

Pour revenir au launcher constructeur, ouvre **Réglages › Launcher Android › Gérer le launcher par défaut**. Selon le fabricant, le même choix se trouve dans **Applications par défaut › Application d’accueil** dans les réglages Android.

## Mises à jour avec Obtainium

1. Installe [Obtainium](https://github.com/ImranR98/Obtainium/releases).
2. Choisis **Ajouter une application**.
3. Colle cette adresse :

   `https://github.com/Cloudiste/Cloudiste-Releases`

4. Si Obtainium demande un filtre de fichier, utilise :

   `^Cloudiste-.*-release\.apk$`

5. Active la vérification des nouvelles versions et les notifications.

Lorsqu’une Release est publiée, Obtainium la détecte et propose son APK. Android peut encore afficher sa propre confirmation avant l’installation.

## Vérifier l’APK

Chaque Release contient un fichier `.sha256`. Sous macOS ou Linux :

```bash
shasum -a 256 Cloudiste-version-release.apk
```

Compare le résultat avec le fichier `.sha256` de la même Release. Le certificat officiel de la bêta possède cette empreinte SHA-256 :

```text
0A:92:D9:A3:0B:FB:E1:0A:E8:4E:D6:8A:A7:B3:18:CB:9A:62:5C:48:C4:27:77:2B:CD:2A:4E:CF:F2:32:7F:FD
```

## Passage futur au Play Store

Les modalités de migration seront communiquées lors de la publication Google Play. Conserve auparavant une sauvegarde `.cloudiste`, car une réinstallation pourrait être nécessaire selon la clé utilisée par Play App Signing.
