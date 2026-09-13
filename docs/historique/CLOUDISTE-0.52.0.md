# Cloudiste 0.52.0 — Stabilisation et conformité

Cette version ouvre le chantier issu de l’audit 0.51.1 sans ajouter de nouvelle fonction majeure.

## Changements

- Google Play devient le seul canal de mise à jour pour une installation provenant de Play ; aucune requête GitHub n’est alors lancée.
- Les installations directes et Obtainium conservent la vérification GitHub mise en cache six heures.
- Les tags GitHub qui ne sont pas des versions `x.y.z` sont refusés.
- La navigation lit `AXIS_HAT_X/Y` en plus des touches DPAD et adapte la zone morte aux informations de la manette.
- Les vidéos respectent leur assombrissement personnalisé.
- Le dock suit les couleurs Sombre, OLED ou Clair.
- Un indicateur apparaît immédiatement pendant l’initialisation.
- Après récupération d’un DataStore corrompu, Cloudiste prévient l’utilisateur et conserve une copie privée pour diagnostic.
- Le focus initial des pages d’actions vise la première action utile plutôt que Retour.
- Le mode épuré reçoit un libellé français correct.
- Les langues prises en charge et les règles de sauvegarde système sont déclarées à Android.
- L’icône adaptative possède un calque monochrome pour les icônes thématiques.
- La dépendance AndroidX Core utilisée directement est déclarée explicitement.

## À tester sur appareil

1. Démarrage à froid : l’indicateur doit apparaître sans écran noir prolongé.
2. Modes Sombre, OLED et Clair : le dock reste lisible.
3. Vidéo personnalisée : sa luminosité suit la valeur choisie.
4. Croix et stick de la manette : navigation stable sans dérive.
5. Réglages › Mises à jour : canal cohérent avec la méthode d’installation.
6. Toutes les pages secondaires : le premier appui sur A ne doit plus fermer immédiatement la page.
