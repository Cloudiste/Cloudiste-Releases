# Cloudiste 0.50.0 — Packs de thèmes partageables

Cette version permet d’exporter l’apparence de Cloudiste dans un fichier `.cloudiste-theme`, de le partager puis de l’importer sur un autre appareil.

## Contenu d’un pack

- thème Sombre, OLED ou Clair ;
- mode d’affichage de l’accueil et logo d’accueil ;
- Clean mode et choix du fond général ou par service ;
- images, GIF animés, vidéos et logos personnalisés des services du catalogue ;
- cadrage, position et luminosité des visuels ;
- ordre des services du catalogue, lorsque l’utilisateur choisit de l’importer.

Les packs sont accessibles depuis **Réglages → Apparence → Packs de thèmes**.

## Import sélectif

Cloudiste affiche un aperçu avant toute modification. L’utilisateur choisit séparément :

1. l’apparence générale ;
2. les visuels des services ;
3. l’ordre des tuiles.

Les catégories non sélectionnées conservent leurs réglages actuels.

## Confidentialité et sécurité

Le format est distinct des sauvegardes personnelles. Il exclut les applications installées ou ajoutées manuellement, les dossiers, le dock, la langue, les comptes et les réglages de lancement.

À l’import, Cloudiste contrôle la structure de l’archive, le manifeste, les noms de fichiers, le nombre d’entrées et la taille totale. Les images, GIF et vidéos passent ensuite par les mêmes validations que les médias choisis localement.

## Test conseillé

1. Personnalise plusieurs services avec une image, un GIF ou une courte vidéo.
2. Ouvre **Réglages → Apparence → Packs de thèmes** et exporte le thème.
3. Modifie l’apparence de l’accueil.
4. Importe le pack et vérifie son aperçu.
5. Applique seulement l’apparence, puis recommence avec les visuels et l’ordre.
6. Vérifie que le dock, les dossiers, la langue et les modes de lancement n’ont pas changé.

Version : `0.50.0` — code : `69`.
