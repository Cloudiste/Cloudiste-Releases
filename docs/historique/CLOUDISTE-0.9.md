# Cloudiste — Version 0.9.0

Version historique validée par l’utilisateur. Pour les nouvelles commandes de suppression et les images distinctes, voir [Cloudiste 0.10.0](CLOUDISTE-0.10.md).

Cette version réunit les cinq évolutions demandées. Les huit étapes précédentes restent la base validée ; ces nouveautés attendent tes essais sur console.

## Les nouveautés

| Demande | Fonctionnement |
| --- | --- |
| Nouveau nom | L'accueil, le nom Android et le projet Android Studio s'appellent **Cloudiste**. L'icône reprend le nuage du projet. |
| Ajouter un service | **Ajouter un service** ouvre la liste des applications ouvrables installées. Recherche une application et sélectionne-la pour créer sa tuile. |
| Tiroir d'applications | **Applications** permet de rechercher et lancer une application sans l'ajouter aux services cloud. |
| Réglages système | **Réglages Android**, directement sur l'accueil, ouvre les paramètres du système. |
| Fonds par service | **Réglages → Personnaliser** permet de choisir une image, son cadrage, sa position et son assombrissement. |

Le nom visible change, mais l'identifiant Android reste `com.example.cloudgaminglauncher`. Cet identifiant est celui de notre application, pas celui d'un service cloud. Le conserver permet de mettre à jour l'APK existant avec la même signature, en gardant tes préférences et les données du lecteur web. Le dossier source existant conserve son chemin ; le ZIP contient un dossier nommé `Cloudiste`.

## Ajouter une application comme service

1. Depuis l'accueil, sélectionne **Ajouter un service**.
2. Parcours les applications à la croix ou au toucher. La liste est alphabétique, avec douze applications par page.
3. Utilise **Rechercher** pour filtrer par nom ou identifiant Android. La recherche ignore la casse et les accents.
4. Le clavier intégré se parcourt à la croix ; **A** saisit la touche sélectionnée. **Effacer un caractère**, **Tout effacer** et **Espace** sont également des boutons accessibles au toucher. Un clavier physique peut aussi saisir le texte.
5. Choisis **Afficher les résultats**, ou appuie sur **B**, pour fermer le clavier en conservant la recherche.
6. Sélectionne l'application. Le message confirme son ajout. **B** revient à l'accueil, où sa nouvelle tuile est disponible.

Le nom et le package viennent du système Android. Il n'y a aucune saisie de package approximatif. Si cette application correspond déjà à un service présent, sa tuile est réaffichée au lieu de créer un doublon. Si elle a été désinstallée entre la recherche et la sélection, l'ajout est refusé avec un message.

Un service personnel utilise son application native ; cette version ne lui invente pas d'URL web. Il participe aux réglages existants : visibilité, ordre et fond personnel. Si son application disparaît plus tard, seule sa tuile devient indisponible et le lancement échoue proprement.

Pour retirer un ajout, ouvre **Réglages → Personnaliser → Retirer ce service de Cloudiste**, puis confirme. Cela retire sa tuile et son fond, sans désinstaller l'application Android. Les quatre services fournis n'ont pas ce bouton de suppression ; tu peux toujours les masquer.

## Utiliser le tiroir et les réglages Android

Le bouton **Applications** ouvre le même navigateur, cette fois pour lancer directement une application. Une recherche ou un lancement depuis ce tiroir ne crée aucune tuile cloud. **Actualiser** relit les applications installées, et **Page précédente / Page suivante** parcourent les résultats. Le tiroir se rafraîchit également à son retour au premier plan.

Le tiroir présente les applications qui ont une entrée Android `MAIN` / `LAUNCHER` accessible dans le profil courant. Il ne liste pas les composants système sans interface ni les applications d'un autre profil Android. Cloudiste ne s'affiche pas dans son propre tiroir.

**Réglages Android** utilise l'action système prévue à cet effet. Cloudiste ouvre l'écran ; il ne change aucun réglage à ta place. Si le système ne peut pas fournir cet écran, un message permet de revenir à l'accueil.

Dans une autre application ou dans les paramètres Android, les commandes appartiennent à cette application et au système. Utilise leur retour habituel pour revenir à Cloudiste. Ce tiroir est intégré à une application classique : aucune déclaration de launcher système `CATEGORY_HOME` n'est ajoutée.

## Choisir et personnaliser un fond

Depuis **Réglages**, chaque service possède un bouton **Personnaliser**, y compris les services personnels et les services masqués.

- **Choisir une image** ouvre le sélecteur de fichiers Android, filtré sur les images. Annuler le sélecteur conserve le fond précédent.
- **Cadrage : remplir** remplit la zone, en coupant les bords qui dépassent. **Image entière** conserve toute l'image, avec des zones libres si les proportions diffèrent.
- **Position** alterne entre centre, haut, bas, gauche et droite. Son effet dépend du cadrage et des proportions de l'image.
- **Assombrissement** alterne entre 40 %, 60 % et 80 %. Une valeur élevée rend les textes plus lisibles sur une image claire.
- **Retirer le fond** restaure le fond normal de ce service et ses valeurs de cadrage initiales.

Un aperçu permet de voir les réglages. Sur l'accueil, le fond suit le service sélectionné ; son image habille aussi le haut de sa tuile. Lorsque tu sélectionnes un raccourci de l'accueil, le dernier service sélectionné conserve son fond.

L'image est copiée dans le stockage privé de Cloudiste. Déplacer ou supprimer l'original ne supprime donc pas le fond importé. Le fichier original n'est jamais modifié. La copie est réduite, si nécessaire, pour tenir dans 1920 × 1080 pixels en conservant ses proportions et son orientation. Les tuiles utilisent une miniature pour limiter leur consommation de mémoire. L'import est statique : il ne crée pas de fond vidéo ou animé.

Chaque modification est enregistrée automatiquement. Attends la fin de l'enregistrement avant de fermer l'écran. Un remplacement ou un retrait nettoie l'ancienne copie privée lorsqu'elle n'est plus référencée. Désinstaller Cloudiste ou effacer ses données supprime ses copies et ses préférences.

## Comprendre les choix Android et Kotlin

Aucune bibliothèque supplémentaire n'est ajoutée. Les nouvelles fonctions utilisent Android, Compose et DataStore déjà présents.

**Découverte des applications.** `InstalledApps` demande à `PackageManager` les applications capables de répondre à l'intent d'ouverture `MAIN` / `LAUNCHER`. Le manifeste autorise explicitement cette recherche par signature d'intent. Les requêtes ciblées des quatre services restent générées depuis `config/service-packages.properties` ; la permission globale `QUERY_ALL_PACKAGES` n'est pas utilisée. [Documentation des requêtes de visibilité](https://developer.android.com/guide/topics/manifest/queries-element).

**Services personnels.** `CustomService` regroupe un nom et le package fourni par Android. Son identifiant stable dérive de ce package. `LauncherPreferences.withCustomServices(...)` fusionne tes ajouts avec le catalogue existant, puis l'ordre et la visibilité sont appliqués. L'interface `ServiceCatalog` reste intacte pour la future API Cloudflare.

**Sauvegarde.** Les clés existantes de DataStore restent identiques. Deux nouvelles valeurs stockent les services personnels et les fonds sous forme de JSON, avec les classes `JSONObject` et `JSONArray` intégrées à Android. Aucun mot de passe ni image binaire n'est placé dans DataStore : il contient seulement les petits réglages et les noms des copies privées.

Les packages des services fournis restent dans le fichier de configuration unique. Les packages de tes ajouts sont des données choisies sur l'appareil et enregistrées dans DataStore ; ils ne sont pas recopiés dans les sources Kotlin ou ajoutés individuellement au manifeste.

**Choix d'image.** `ActivityResultContracts.OpenDocument` ouvre le sélecteur système et renvoie l'adresse de l'image choisie. L'application lit cette image pour en créer une copie privée. Elle ne demande donc ni accès global aux photos ni permission de stockage générale. [Documentation du sélecteur de documents](https://developer.android.com/training/data-storage/shared/documents-files).

**Ouverture des paramètres.** `Settings.ACTION_SETTINGS` est une action Android standard ; aucun package de paramètres propre à un constructeur n'est codé en dur. [Référence officielle](https://developer.android.com/reference/android/provider/Settings#ACTION_SETTINGS).

**Interface.** `ActionPage` partage les règles de focus entre le tiroir, le clavier et la personnalisation. Les commandes sont de vraies cibles de focus, avec bordure, agrandissement et défilement automatique. Chaque écran conserve son ViewModel ; le clavier est une partie de l'écran des applications. L'assemblage reste manuel, sans injection de dépendances.

## Fichiers principaux

Les chemins Kotlin partent de `app/src/main/java/com/example/cloudgaminglauncher/`.

| Fichier | Rôle |
| --- | --- |
| `data/device/InstalledApps.kt` | Découverte et recherche des applications réellement présentes. |
| `data/settings/Customization.kt` | Modèles des services personnels et fonds, conversion JSON. |
| `data/settings/SettingsRepository.kt` | Sauvegarde des ajouts et de leur personnalisation. |
| `data/wallpaper/WallpaperStore.kt` | Import, réduction, lecture et suppression des copies privées. |
| `ui/apps/AppsActivity.kt`, `AppsViewModel.kt` | Tiroir, ajout, pagination et clavier de recherche. |
| `ui/personalize/PersonalizeActivity.kt`, `PersonalizeViewModel.kt` | Fond par service et retrait des services personnels. |
| `ui/personalize/WallpaperView.kt` | Affichage du fond selon le cadrage et l'assombrissement. |
| `ui/common/ActionPage.kt`, `AppIcon.kt` | Commandes communes et icônes réelles des applications. |

## Installer et valider sur ta console

Installe l'APK 0.9.0 par-dessus la version précédente, avec la même signature de développement, ou ouvre le projet et lance **Run ▶** depuis Android Studio. La version minimale reste Android 10 / API 29.

1. Vérifie que le nom **Cloudiste** et son icône apparaissent dans Android. Tes anciens choix de visibilité, d'ordre et de priorité doivent être conservés.
2. À la manette, ouvre Ajouter un service. Recherche une application installée, ajoute-la, reviens à l'accueil et lance-la. Recommence son ajout : aucune seconde tuile ne doit apparaître.
3. Depuis Applications, ouvre une application non ajoutée aux services. Teste les deux pages, une recherche sans résultat et Actualiser. Reviens à l'accueil.
4. Ouvre Réglages Android directement depuis l'accueil, puis reviens sans modifier de paramètre.
5. Choisis un fond pour deux services différents. Vérifie le changement de fond en passant de l'un à l'autre à la croix, ainsi que le cadrage, la position et l'assombrissement.
6. Ferme complètement Cloudiste, puis redémarre la console. Retrouve les services ajoutés et leurs fonds.
7. Refais un ajout et un changement de fond au toucher. Passe ensuite à la manette sans changer de mode.
8. Retire un service personnel : son application doit rester installée et les autres services doivent rester intacts.

L'écran de choix de fichier et les réglages système sont fournis par Android : leur navigation à la manette dépend aussi de la version et du constructeur. Vérifie ce parcours sur ta console. Les écrans propres à Cloudiste proposent les commandes à la manette et au toucher.

Le rapport `VERIFICATION-CLOUDISTE-0.9.md` distingue les contrôles automatisés des essais matériels qui restent à confirmer. Arrêt après cette livraison pour attendre ta validation.
