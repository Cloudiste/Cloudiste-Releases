# Cloudiste 0.46.3 — Cadrage indépendant des tuiles

Cette version corrige le cadrage des images personnalisées des dossiers **Émulateurs** et **Jeux Android**.

## Changements

- Le fond plein écran et l’image de la tuile disposent maintenant de réglages de cadrage distincts.
- Les images personnalisées des dossiers sont affichées entièrement par défaut dans leur tuile ; cela évite de couper les personnages ou les éléments placés près des bords.
- Une image commune peut toujours être utilisée aux deux emplacements sans imposer le même recadrage.
- La position et l’assombrissement sont également réglables séparément pour le fond et la tuile.
- Les services conservent leur ancien rendu ; les anciens dossiers reçoivent automatiquement le cadrage corrigé pour leur tuile.
- La correction est disponible pour les dossiers comme pour les services cloud et les applications ajoutées.

## Test conseillé

1. Fais un appui long sur le dossier **Émulateurs**, puis ouvre **Cadrage et luminosité**.
2. Règle **Tuile — cadrage** et **Tuile — position** jusqu’à afficher correctement le sujet de l’image.
3. Vérifie que le fond plein écran n’a pas changé.
4. Recommence avec **Jeux Android**.
5. Ferme puis relance Cloudiste pour vérifier que les deux cadrages sont conservés.

Version : `0.46.3` — code : `65`.
