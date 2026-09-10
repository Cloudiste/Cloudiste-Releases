# Cloudiste 0.32.0 — Navigation Web exclusivement externe

Cloudiste ne contient plus de navigateur intégré. Toute destination Web est transmise à Android, qui l’ouvre dans le navigateur installé ou affiche son sélecteur d’applications.

Cette règle s’applique :

- aux services exclusivement Web, dont Xbox Cloud Gaming et Amazon Luna ;
- au mode Web de GeForce NOW et Boosteroid ;
- au repli Web utilisé lorsqu’une application native est absente ou indisponible ;
- aux sites de la rubrique Découvrir ;
- aux fiches Google Play ouvertes par HTTPS lorsqu’aucune boutique compatible n’est installée.

## Confidentialité et conformité

- Les pages de connexion ne sont jamais dessinées dans une fenêtre appartenant à Cloudiste.
- Les identifiants, mots de passe, cookies et redirections restent sous la responsabilité du navigateur et du service choisi.
- Cloudiste transmet uniquement l’adresse HTTPS initiale du catalogue.
- Les adresses HTTP, locales, `file:`, `content:`, `javascript:`, `intent:` ou contenant un identifiant dans l’URL sont refusées.
- Aucun navigateur précis n’est imposé : Android respecte le choix de l’utilisateur.
- La permission Android `INTERNET` a été retirée, puisque Cloudiste n’effectue plus de chargement réseau.
- L’Activity Web, la WebView, son stockage de session, son menu et le diagnostic JavaScript ont été supprimés du projet.

Le rapport de diagnostic 0.31 conserve la version du composant WebView à titre d’information sur l’appareil, mais précise désormais que Cloudiste ne l’utilise pas.

## Test sur appareil réel

1. Installe la version 0.32.0 par-dessus la 0.31.0.
2. Ouvre Xbox Cloud Gaming : le navigateur externe doit devenir l’application visible.
3. Reviens avec le bouton Retour d’Android : Cloudiste doit réapparaître selon le comportement normal du navigateur.
4. Ouvre Amazon Luna et vérifie le même comportement.
5. Si GeForce NOW ou Boosteroid n’est pas installé, ouvre sa tuile : le repli doit également arriver dans le navigateur externe.
6. Dans **Réglages > Service de l’accueil**, sélectionne le mode Web pour un service compatible et vérifie l’ouverture externe.
7. Depuis **Découvrir**, ouvre un site Internet et vérifie qu’il utilise le même mécanisme externe.
8. Sur une page de connexion, contrôle visuellement que l’application affichée est bien ton navigateur et que Cloudiste n’apparaît pas dans son interface.
9. Refais les ouvertures avec la manette. Une fois dans le navigateur, les commandes et le bouton Retour dépendent du navigateur et d’Android.

Si aucun navigateur n’est installé ou activé, Cloudiste affiche un message d’échec sans se fermer.
