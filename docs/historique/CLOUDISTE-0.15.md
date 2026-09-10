# Cloudiste 0.15.0 — Découvrir des services

Le dock de l’accueil comporte maintenant un cinquième pictogramme : **Découvrir**. Il ouvre une liste verticale de dix services : GeForce NOW, Boosteroid, Xbox Cloud Gaming, PlayStation Plus Premium avec Asobi, Amazon Luna, Shadow PC, Moonlight, Steam Link, Parsec et Antstream Arcade.

Chaque service possède une grande action vers son site officiel. Une seconde action **Google Play** apparaît uniquement lorsqu’un package Android a été confirmé. Amazon Luna et Xbox Cloud Gaming sont donc proposés par leur site web dans cette version.

## Pourquoi créer un écran séparé

Android appelle une `Activity` une fenêtre de l’application. `DiscoverActivity` représente la fenêtre Découvrir et possède son propre `DiscoverViewModel`, conformément au principe « un ViewModel par écran » du projet.

Le ViewModel expose le catalogue et reçoit les actions de l’utilisateur. L’écran Compose se contente de dessiner la liste. Cette séparation rend le code plus lisible : l’affichage ne décide pas lui-même comment ouvrir un navigateur ou Google Play.

Le catalogue est local dans `DiscoverCatalog.kt`. L’écran s’affiche donc immédiatement, même sans connexion. Internet n’est utilisé qu’après avoir choisi un lien externe.

## Sites et applications Android

Les noms de packages restent regroupés dans `config/service-packages.properties`. Gradle les transforme en constantes à la compilation. Ce fichier unique évite de disperser des identifiants sensibles aux changements dans plusieurs écrans.

Pour Google Play, Cloudiste essaie d’abord l’adresse `market://details?id=…`, comprise par l’application Play Store. Si elle est indisponible, l’application ouvre la même fiche sur `https://play.google.com`. Les sites officiels s’ouvrent avec l’application choisie par Android, généralement le navigateur.

Moonlight et Steam Link diffusent un ordinateur appartenant à l’utilisateur ; ils ne fournissent pas eux-mêmes un catalogue cloud comparable à GeForce NOW. Ils apparaissent néanmoins dans Découvrir car ils répondent au besoin de jeu à distance demandé.

## Utilisation au doigt et à la manette

- Au doigt, touche une carte pour l’ouvrir et glisse verticalement pour parcourir la liste.
- À la manette, utilise la croix directionnelle ou le stick pour déplacer la bordure de focus.
- Appuie sur **A** pour ouvrir l’action sélectionnée.
- Appuie sur **B** pour revenir à l’accueil.
- Tu peux faire défiler au doigt puis reprendre immédiatement la manette : le premier déplacement rétablit le focus sur un élément visible.

La liste utilise le même composant `ActionPage` que les autres pages. Ce composant demande automatiquement à Compose de faire défiler l’élément sélectionné afin qu’il reste visible.

## Installer et tester sur un appareil réel

Installe `Cloudiste-0.15.0-debug.apk` par-dessus la version précédente. L’identifiant Android et la signature de développement restent les mêmes : tes services, images, préférences et ordre de tuiles sont conservés.

1. Ouvre Cloudiste et vérifie que le dock compact possède cinq pictogrammes.
2. Touche **Découvrir**. Vérifie que le titre indique dix services.
3. Fais défiler toute la liste au doigt jusqu’à Antstream Arcade.
4. Reviens en haut, ouvre le site d’un service, puis utilise Retour Android pour revenir à Cloudiste.
5. Touche une action **Google Play**. Vérifie que la fiche correspond bien au service choisi.
6. Vérifie qu’Amazon Luna et Xbox Cloud Gaming n’affichent qu’une action vers leur site.
7. Recommence sans toucher l’écran : parcours le dock jusqu’à Découvrir, ouvre-le avec A, descends jusqu’à Antstream Arcade et reviens avec B.
8. Alterne enfin un glissement tactile et une pression directionnelle pour confirmer que le focus réapparaît correctement.

Le [rapport de vérification](VERIFICATION-CLOUDISTE-0.15.md) décrit les contrôles déjà réalisés sur l’émulateur. Cette version attend ensuite ta validation sur ta console réelle.

## Références utilisées

- GeForce NOW : https://www.nvidia.com/geforce-now/
- Boosteroid : https://boosteroid.com/
- Xbox Cloud Gaming : https://www.xbox.com/play
- Asobi : https://asobiapp.com/
- Amazon Luna : https://luna.amazon.com/
- Shadow PC : https://shadow.tech/
- Moonlight : https://moonlight-stream.org/
- Steam Remote Play : https://store.steampowered.com/remoteplay/
- Parsec : https://parsec.app/
- Antstream Arcade : https://www.antstream.com/

