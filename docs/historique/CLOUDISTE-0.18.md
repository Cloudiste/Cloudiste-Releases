# Cloudiste 0.18.0 — Découvrir et composer son accueil

Cette version relie enfin le catalogue **Découvrir** à l’accueil. Une fiche ne sert plus seulement à consulter un service : elle indique sa disponibilité sur l’appareil et permet de l’ajouter à Cloudiste.

**Version validée par l’utilisateur sur appareil réel.**

## Ce qui change

Les onze services de Découvrir possèdent maintenant une définition lançable. Les quatre services historiques restent présents au premier démarrage : GeForce NOW, Boosteroid, Xbox Cloud Gaming et PlayStation Plus Premium. Amazon Luna, Shadow PC, Moonlight, Steam Link, Parsec, Antstream Arcade et Blacknut peuvent être ajoutés individuellement.

Dans la liste Découvrir, chaque ligne indique :

- si l’application Android est installée, absente, désactivée ou impossible à vérifier ;
- si le service passe principalement par le Web ;
- si le service est déjà présent sur l’accueil.

La fiche propose une action principale adaptée à la situation : ouvrir l’application installée, rejoindre Google Play, ouvrir le lecteur Web intégré ou consulter le site officiel. Le bouton voisin ajoute le service à l’accueil ou l’en retire. Les quatre services initiaux peuvent toujours être masqués dans Réglages, mais ne sont pas supprimés de la sélection initiale.

Un service ajouté depuis Découvrir devient une tuile normale. Il utilise le même logo dans Découvrir et sur l’accueil, peut recevoir ses propres images, être déplacé par glissement, masqué et réordonné. Le retrait depuis sa fiche ou depuis Réglages conserve ses images et son mode de lancement : si tu le réajoutes, sa personnalisation revient.

## Pourquoi deux catalogues sont conservés

`DiscoverCatalog` contient les textes éditoriaux : présentation, accès, site et lien Google Play. `StaticServiceCatalog` contient les données qui servent réellement au lancement : package Android, repli Web et domaines autorisés. Ils partagent les mêmes identifiants stables définis dans `ServiceIds`.

Cette séparation évite de mélanger le contenu d’une fiche avec le comportement de lancement. Une vérification automatisée garantit maintenant que chaque fiche correspond bien à un service lançable.

## Persistance

`LauncherPreferences.addedCatalogIds` mémorise seulement les identifiants choisis. DataStore les conserve dans `added_catalog_services`. Il n’est donc pas nécessaire de recopier les onze services dans les préférences.

Quand Compose observe ce nouvel état, le ViewModel recalcule la liste de l’accueil. La tuile apparaît ou disparaît sans redémarrer l’application. La version 0.18 utilise toujours l’identifiant `fr.cloudiste.launcher` : une installation par-dessus la 0.17 conserve les préférences existantes.

## Recherche des applications

Les écrans Applications et Ajouter un service préparent maintenant une seule chaîne de recherche normalisée par application. Le filtrage ne refait plus la normalisation du nom et du package à chaque frappe. Si une application installée correspond à l’un des services de Découvrir, Cloudiste ajoute sa tuile officielle au lieu de créer un doublon manuel.

## Essai sur appareil réel

1. Installe la nouvelle version depuis Android Studio avec **Run ▶**. Vérifie dans les informations de l’application que la version affichée est `0.18.0`.
2. Ouvre **Découvrir** depuis le dock. Parcours la liste au doigt, à la croix puis au stick gauche. Les onze lignes doivent rester accessibles.
3. Ouvre la fiche de Blacknut ou de Shadow PC. Vérifie l’état d’installation, puis choisis **Ajouter à l’accueil**.
4. Reviens avec B ou **Retour**. L’accueil doit annoncer cinq services et afficher la nouvelle tuile.
5. Ouvre la tuile. Sans application installée, Cloudiste doit proposer Google Play pour un service natif, ou le lecteur intégré pour Amazon Luna.
6. Fais un appui long sur la tuile et ajoute des images. Déplace-la ensuite au doigt : ces fonctions doivent se comporter comme pour les quatre services initiaux.
7. Retourne dans la fiche et choisis **Retirer de l’accueil**. Le compteur doit revenir à quatre. Tu peux aussi effectuer ce retrait dans **Réglages**.
8. Réajoute le service et vérifie que ses images personnalisées sont conservées.

Teste chaque action une fois à la manette et une fois au toucher. Les packages tiers restent centralisés dans `config/service-packages.properties` et doivent être vérifiés sur les appareils cibles avant publication.
