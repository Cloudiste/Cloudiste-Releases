# Cloudiste 0.20.0 — Accueil plein écran

Cloudiste propose désormais deux présentations de l’accueil : la grille de tuiles existante et un mode qui met un seul service en avant. Le bouton placé en bas à droite alterne entre les deux. Son pictogramme indique la présentation qui sera ouverte : un cadre pour passer en plein écran, puis une grille pour revenir aux tuiles.

## Mode plein écran

Le logo du service actif est centré dans une grande zone sombre et lisible. Son nom, son état d’installation et sa position dans la liste apparaissent juste en dessous. Les services suivent le même ordre que les tuiles et les services masqués ne sont pas présentés.

Le fond utilise l’image personnalisée du service lorsqu’elle existe. Sans image, Cloudiste compose un halo discret à partir de la couleur du service et du thème actif. Un appui long sur la grande zone ouvre directement la personnalisation de ce service : l’image choisie pour le fond de l’accueil devient donc aussi son décor plein écran.

Le logo Cloudiste, Quitter, le bouton d’apparence et le dock restent disponibles. Le mode choisi est enregistré dans DataStore et revient après une fermeture complète de l’application.

## Commandes

Au toucher :

- touche le service pour l’ouvrir ;
- glisse vers la gauche ou la droite pour changer de service ;
- reste appuyé pour personnaliser son fond ;
- touche le pictogramme en bas à droite pour changer de présentation.

À la manette :

- gauche et droite parcourent les services lorsque la grande zone a le focus ;
- A ouvre le service ; un appui long sur A ouvre sa personnalisation ;
- haut rejoint Quitter et bas rejoint les commandes inférieures ;
- le bouton d’affichage est accessible après Réglages Android dans la rangée du bas.

Les deux sens bouclent : aller à gauche depuis le premier service affiche le dernier, et aller à droite depuis le dernier revient au premier.

## Fonctionnement du code

`HomeDisplayMode` est une `enum class` avec deux valeurs, `TILES` et `FULLSCREEN`. `LauncherPreferences` conserve cette valeur, et `DataStoreSettingsRepository` l’enregistre sous la clé `home_display_mode`. Une valeur inconnue revient prudemment aux tuiles.

Le même `HomeViewModel` pilote les deux présentations. Le composant plein écran réutilise le catalogue, les états d’installation, les fonds et les actions déjà employés par les tuiles. Aucun second catalogue ni réglage de personnalisation parallèle n’a été créé.

Le glissement accumule uniquement le déplacement horizontal. Une distance minimale évite qu’un petit mouvement du doigt change de service. Le geste consommé ne déclenche pas ensuite l’ouverture du service.

Aucune dépendance ni permission Android supplémentaire n’a été ajoutée.

## Essai sur appareil réel

1. Installe la 0.20.0 par-dessus la 0.19. Tes services, leur ordre, les fonds et le thème doivent être conservés.
2. Sur l’accueil en tuiles, touche le nouveau bouton en bas à droite. Le premier service visible doit occuper le centre et le pictogramme doit devenir une grille.
3. Glisse plusieurs fois horizontalement. Vérifie le nom, le logo, le compteur et le changement de fond. Le geste ne doit lancer aucune application.
4. Touche brièvement le service actif pour vérifier son lancement, puis reviens dans Cloudiste.
5. Reste appuyé sur le service : la personnalisation correspondante doit s’ouvrir. Choisis un fond, reviens et vérifie qu’il remplit le mode plein écran.
6. Recommence uniquement avec la manette : gauche, droite, A, appui long sur A, haut et bas.
7. Parcours la rangée inférieure jusqu’au bouton en bas à droite et active-le avec A. La grille doit revenir.
8. Repasse en plein écran, ferme complètement Cloudiste et relance-le. Le mode plein écran doit être restauré.
9. Vérifie enfin Sombre, OLED et Clair. Le contenu central doit rester lisible et OLED doit conserver du noir pur hors des images personnalisées.

