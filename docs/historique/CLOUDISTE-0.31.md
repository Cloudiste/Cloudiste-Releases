# Cloudiste 0.31.0 — Diagnostic et retour bêta

## Rubrique Informations

La colonne des réglages contient maintenant une rubrique **Informations** avec :

- la version exacte de Cloudiste ;
- « Vibecoder par Rodolphe CHOUTEAU » ;
- la chaîne `@Cloudgamingfrance` ;
- le contact affiché sous la forme `rodolphe.c.pro [at] gmail [dot] com` ;
- un bouton pour préparer un e-mail ;
- un bouton ouvrant le diagnostic.

L’adresse est séparée dans le code et reconstruite uniquement lors de l’ouverture de l’application e-mail. Elle n’apparaît donc jamais en clair dans l’interface ou dans une ressource de texte facilement collectable.

## Rapport de diagnostic

La page produit automatiquement un rapport en texte brut contenant :

- la version de Cloudiste ;
- le constructeur et le modèle de l’appareil ;
- la version Android et le niveau d’API ;
- la version du composant Android System WebView ;
- le nom des manettes actuellement détectées ;
- l’état de chaque service connu ou ajouté : Web, application installée, absente, désactivée, suspendue ou non configurée, ainsi que sa présence sur l’accueil ;
- le launcher Android actuellement sélectionné ;
- jusqu’aux trois derniers crashs, blocages ou arrêts techniques de Cloudiste connus du système.

Le rapport exclut les comptes, identifiants matériels, numéros de série, adresses réseau et contenus de connexion. Sur Android 10, l’historique détaillé des arrêts n’est pas fourni par le système ; les autres rubriques restent disponibles.

Les boutons **Partager le rapport**, **Actualiser** et **Retour** sont utilisables au toucher et à la manette. Le rapport est sélectionnable au doigt pour permettre une copie manuelle.

## Test sur appareil réel

1. Installe l’APK 0.31.0 par-dessus la version précédente.
2. Ouvre **Réglages > Informations** et contrôle la version, la signature, la chaîne et le contact masqué.
3. Active **Écrire au contact** et vérifie que ton application e-mail prépare un message à l’adresse attendue, sans envoyer automatiquement le message.
4. Ouvre **Diagnostic et retour bêta**.
5. Vérifie le modèle de l’appareil, Android, WebView et le launcher actif.
6. Branche puis débranche une manette et utilise **Actualiser** : la ligne Manette doit suivre son état.
7. Compare les services installés, absents, désactivés et masqués avec leur état réel.
8. Active **Partager le rapport** et choisis une application cible. Vérifie que seul le texte affiché est transmis.
9. Refais le parcours uniquement avec la croix ou le stick, A et B.
