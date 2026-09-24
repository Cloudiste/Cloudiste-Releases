# Cloudiste 0.59.0 — Disponibilité des jeux

Cette version ajoute un catalogue local permettant de rechercher sur quels services un jeu est disponible : GeForce NOW, Xbox Cloud Gaming, Boosteroid et PlayStation Plus Premium.

## Fonctionnement

- un seul catalogue est téléchargé au maximum toutes les 24 heures ;
- le fichier est conservé sur l’appareil et les recherches restent locales ;
- ETag et réponse `304` évitent les téléchargements inutiles ;
- un échec réseau ou Cloudflare Access conserve le dernier catalogue valide ;
- la mise à jour manuelle est limitée à une tentative par heure ;
- le cache est remplacé seulement après téléchargement et validation complète du JSON ;
- les redirections, fichiers supérieurs à 20 Mo et versions de format inconnues sont refusés.

## Interface

- loupe **Disponibilité des jeux** placée au centre du dock de l’accueil ;
- la recherche n’apparaît plus dans Découvrir ;
- rubrique **Catalogue des jeux** dans Réglages ;
- recherche insensible aux accents, symboles et variations de casse ;
- jaquettes verticales chargées à la demande depuis SteamGridDB, puis mises en cache sur l’appareil ;
- recherche par AppID Steam, avec repli par titre pour les jeux sans identifiant Steam ;
- clé SteamGridDB conservée exclusivement dans les secrets du Worker Cloudflare ;
- cache Cloudflare de 30 jours et cache local Android pour limiter les appels ;
- CDN Steam conservé comme dernier repli si SteamGridDB ne trouve aucun visuel ;
- visuel de repli lorsqu’aucune jaquette compatible n’est disponible ;
- distinction Xbox **Game Pass** / **Si possédé** ;
- boutiques compatibles affichées pour GeForce NOW lorsqu’elles sont fournies par le catalogue ;
- noms de boutiques directement cliquables dans la ligne existante pour Steam, Epic Games Store, GOG, Ubisoft, EA, Battle.net et Xbox ;
- ouverture de la fiche Steam exacte lorsque l’AppID est disponible, avec recherche officielle par titre dans les autres cas ;
- tous les liens commerciaux s’ouvrent dans le navigateur externe, sans afficher ni collecter d’identifiants dans Cloudiste ;
- message explicite lorsque la source ne fournit pas les boutiques d’un jeu GeForce NOW ;
- liens vers les services ouverts dans le navigateur externe ;
- date du catalogue et attribution cliquable Cloud Dosage ;
- interface traduite en français, anglais et espagnol.

La version reste locale pour validation avant toute publication GitHub.
