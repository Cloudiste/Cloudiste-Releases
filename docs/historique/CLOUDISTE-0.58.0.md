# Cloudiste 0.58.0 — Deux ambiances musicales

Cette version retire l’ancienne musique d’ambiance et intègre **Interface Ambience** et **Infinite Digital Space**. Le choix s’effectue dans Réglages, section Apparence, et prend effet immédiatement. Cloudiste mémorise le morceau sélectionné ainsi que le niveau sonore.

Les niveaux **Très légère**, **Douce** et **Présente** sont conservés. Les deux morceaux ont été mesurés à un niveau moyen identique de −14,8 LUFS afin d’éviter un saut de volume lors du changement. La lecture conserve le comportement existant : elle se met en pause lorsque Cloudiste quitte le premier plan et respecte le focus audio Android.

Le choix musical rejoint les données sauvegardées et restaurées. Les sauvegardes créées avant cette version restent compatibles et utilisent Interface Ambience lorsque le champ musical est absent.

## Vérification

- APK et AAB signés : compilation réussie.
- Android Lint : aucune erreur.
- 377 contrôles Android réussis, dont la persistance du morceau et la compatibilité des anciennes sauvegardes.
- Mise à jour de la 0.57.5 vers la 0.58.0 vérifiée avec le certificat Cloudiste historique.
- Les deux fichiers audio ont été décodés intégralement sans erreur avant intégration.
