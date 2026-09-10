# Cloudiste 0.16.0 — Liste et fiches Découvrir

La page **Découvrir** possède maintenant une structure en deux niveaux :

1. une liste verticale de onze services, avec une seule ligne et un logo par service ;
2. une fiche détaillée qui s’ouvre lorsque la ligne est sélectionnée.

Le service demandé sous le nom « Black Note » correspond à la marque officielle **Blacknut Cloud Gaming**. C’est ce nom qui est affiché, avec son site officiel et son application Android `com.blacknut.app`.

## Pourquoi utiliser deux pages

La liste sert à comparer et à choisir rapidement. Chaque ligne contient seulement le logo, le nom, une courte description et l’indication Ouvrir. Les destinations externes ne surchargent donc plus le catalogue.

La fiche apporte ensuite le contexte utile :

- une grande version du logo ;
- un résumé du service ;
- une section **À propos** ;
- une section **Accès** ;
- les actions disponibles en bas de l’écran ;
- un bouton **Retour** visible en haut à droite.

Android appelle une fenêtre de l’application une `Activity`. `DiscoverActivity` affiche la liste et `DiscoverDetailActivity` affiche la fiche. Chacune possède son ViewModel : `DiscoverViewModel` pour le catalogue et `DiscoverDetailViewModel` pour le service sélectionné et l’ouverture de ses liens.

La liste transmet seulement l’identifiant interne du service, par exemple `blacknut`. La fiche recherche ensuite cet identifiant dans `DiscoverCatalog`. Une adresse arbitraire reçue depuis l’extérieur ne peut donc pas être injectée dans l’écran.

## Logos locaux

Tous les logos sont inclus dans l’APK. Cloudiste n’a pas besoin de les télécharger à chaque ouverture et aucun outil externe de chargement d’images n’a été ajouté.

Les quatre logos déjà présents restent des fichiers vectoriels. Les nouvelles icônes proviennent des fiches Google Play et sont stockées comme images PNG de 512 × 512 pixels. `DiscoverLogo.kt` associe l’identifiant stable de chaque service à sa ressource graphique. Le fichier `ASSETS.md` consigne leur provenance.

## Blacknut

Blacknut est ajouté à la fin de la liste avec :

- le site officiel `https://www.blacknut.com/` ;
- le package Google Play `com.blacknut.app` ;
- une présentation courte de son catalogue sous abonnement, de ses profils familiaux et de son accès sur plusieurs appareils.

Le package est centralisé dans `config/service-packages.properties`, comme tous les autres packages tiers. Gradle l’utilise à la fois dans le code Kotlin et dans les déclarations Android nécessaires pour détecter une application.

## Utiliser la liste et une fiche

Au doigt :

1. ouvre Découvrir depuis le dock ;
2. glisse verticalement pour parcourir les lignes ;
3. touche une ligne pour ouvrir sa fiche ;
4. touche Site internet ou Google Play ;
5. touche Retour pour revenir à la liste.

À la manette :

1. utilise la croix ou le stick pour sélectionner une ligne ;
2. appuie sur **A** pour ouvrir la fiche ;
3. dans la fiche, appuie sur Bas pour rejoindre les actions ;
4. utilise Gauche et Droite lorsque Site internet et Google Play sont tous les deux disponibles ;
5. appuie sur **A** pour ouvrir l’action et sur **B** pour revenir.

Le focus conserve sa bordure blanche. Quand il descend dans la liste, Compose fait défiler automatiquement la ligne pour qu’elle reste visible. Le glissement tactile reste disponible et peut être suivi immédiatement d’une commande à la manette.

## Tester sur un appareil réel

Installe `Cloudiste-0.16.0-debug.apk` par-dessus ta version actuelle. Les préférences, services ajoutés, fonds et ordre des tuiles sont conservés.

1. Vérifie que Découvrir indique **11 services**.
2. Vérifie que chaque ligne possède un logo, un nom et une courte description.
3. Descends jusqu’à **Blacknut Cloud Gaming** au doigt, puis ouvre sa fiche.
4. Vérifie la grande image, les sections À propos et Accès, le bouton Retour et les deux actions du bas.
5. Ouvre le site internet de Blacknut, puis reviens dans Cloudiste.
6. Ouvre Google Play et vérifie que la fiche affichée correspond à Blacknut Cloud Gaming.
7. Recommence entièrement à la manette, y compris le retour avec B.
8. Ouvre ensuite Amazon Luna ou Xbox Cloud Gaming : leur fiche doit afficher le site internet sans bouton Google Play.
9. Vérifie enfin quelques autres services pour confirmer que leur logo et leurs informations correspondent.

Le [rapport de vérification](VERIFICATION-CLOUDISTE-0.16.md) décrit les essais déjà réussis sur l’émulateur.

## Sources principales

- Blacknut : https://www.blacknut.com/en
- Blacknut sur Android : https://play.google.com/store/apps/details?id=com.blacknut.app
- Téléchargement Android Blacknut : https://www.blacknut.com/en/download/androidtv

