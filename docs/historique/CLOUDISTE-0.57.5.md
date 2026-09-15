# Cloudiste 0.57.5 — Gestes indépendants du logo et du dock

Cette version corrige le comportement du bandeau supérieur et du dock sur l’accueil. Le swipe vers le haut réduit et remonte le logo Cloudiste ; le dock reste à sa taille normale. Le swipe vers le bas restaure le logo et réduit la capsule du dock, ses espacements et ses pictogrammes. Chaque changement s’anime doucement et les boutons conservent une zone tactile d’au moins 48 dp.

Sur smartphone en paysage, le logo réduit davantage qu’auparavant. Le dock se compacte sur tous les formats. Les services, dossiers, fonds, réglages et commandes à la manette sont conservés.

La 0.57.4 a servi de version locale de test. La 0.57.5 est la première publication GitHub de ce changement, après correction de la direction des gestes et validation.

## Vérification

- APK et AAB signés : compilation réussie.
- Android Lint : aucune erreur.
- Sur émulateur en paysage : swipe vers le haut avec logo réduit et dock normal ; swipe vers le bas avec logo normal et dock compact.
- Identité Android : `fr.cloudiste.launcher`, version `0.57.5`, code `84`.
