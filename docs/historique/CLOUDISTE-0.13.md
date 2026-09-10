# Cloudiste 0.13.0 — Listes continues et déplacement tactile

Cette version apporte deux changements de navigation :

- **Applications** et **Ajouter un service** affichent toutes les applications trouvées dans une seule liste qui défile verticalement. Les boutons Page précédente et Page suivante ont disparu.
- Sur l’accueil, une tuile de service peut être déplacée directement avec le doigt. L’ordre est enregistré automatiquement et reste identique au prochain démarrage.

## Pourquoi la liste défile sans pagination

`AppsViewModel` conserve toujours la liste des applications et le texte recherché. Il n’a maintenant plus de numéro de page : `matches` contient tous les résultats qui correspondent à la recherche.

`ActionPage` place les lignes dans une `Column` munie de `verticalScroll`. En Compose, le `Modifier` complète un élément d’interface avec un comportement. Ici, `verticalScroll` permet le glissement vertical au doigt. Quand la croix de la manette déplace le focus vers un élément hors de l’écran, le mécanisme `BringIntoViewRequester` déjà utilisé fait défiler la même colonne pour le rendre visible.

Une seule liste sert donc au tactile et à la manette. La grille garde plusieurs colonnes selon la largeur de l’appareil, mais son déplacement se fait verticalement et sans rupture entre des pages.

## Comment fonctionne le glissement d’une tuile

Le composant `FocusableSurface`, commun aux tuiles tactiles et sélectionnables à la manette, reconnaît maintenant un geste de déplacement :

1. le doigt touche une tuile ;
2. un mouvement dépassant la petite tolérance d’Android démarre le glissement ;
3. la tuile déplacée devient légèrement transparente et la destination reçoit une bordure blanche ;
4. au relâchement, `HomeViewModel.moveService` calcule le nouvel ordre ;
5. `DataStore` enregistre cet ordre.

Cette tolérance permet de distinguer les trois gestes : un toucher court ouvre le service, un maintien immobile ouvre la personnalisation et un maintien accompagné d’un mouvement déplace la tuile.

Les services masqués ne sont pas perdus pendant le calcul. Leur position est conservée dans l’ordre complet, même s’ils ne sont pas dessinés sur l’accueil. Le réglage **Monter / Descendre** reste disponible pour réordonner les services à la manette.

## Installer et tester sur l’appareil réel

Installe **Cloudiste-0.13.0-debug.apk** par-dessus la version précédente. L’identifiant Android et la signature de développement sont inchangés, donc les services, images et réglages déjà enregistrés sont conservés.

1. Ouvre **Applications**, puis glisse la liste vers le haut et vers le bas. Vérifie qu’il n’existe plus de boutons Page précédente ou Page suivante.
2. Recommence dans **Ajouter un service**. Touche une application visible seulement après le défilement et vérifie qu’elle s’ajoute normalement.
3. Dans chacune de ces pages, utilise uniquement la croix de la manette. Descends au-delà du premier écran : la liste doit défiler automatiquement et la bordure blanche doit rester visible.
4. Reviens à l’accueil et glisse une tuile sur une autre. La tuile déplacée doit devenir transparente et la destination doit être entourée de blanc.
5. Relâche le doigt : les tuiles doivent prendre immédiatement leur nouvel ordre et aucun service ne doit s’ouvrir.
6. Ferme complètement Cloudiste, puis relance-le. Vérifie que l’ordre est conservé.
7. Touche brièvement une tuile pour vérifier son ouverture.
8. Maintiens le doigt sur une tuile sans le déplacer : sa page de personnalisation doit toujours s’ouvrir.
9. Avec la manette, ouvre **Réglages** et utilise **Monter / Descendre** pour confirmer que le changement d’ordre reste possible sans tactile.

Le [rapport de vérification](VERIFICATION-CLOUDISTE-0.13.md) décrit les contrôles déjà effectués sur l’émulateur. Cette version attend ta validation sur la console réelle.
