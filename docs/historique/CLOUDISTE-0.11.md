# Cloudiste 0.11.0 — Personnalisation par appui long

Version historique validée par l’utilisateur. Les pictogrammes de l’accueil sont décrits dans [Cloudiste 0.12.0](CLOUDISTE-0.12.md).

Cette version ajoute un raccourci vers la personnalisation depuis chaque tuile de l’accueil. Il fonctionne à la manette et au toucher.

## Utiliser le raccourci

- **Manette :** sélectionne une tuile, puis maintiens **A** environ une demi-seconde. Relâche le bouton si ta manette n’envoie pas de répétition.
- **Tactile :** garde le doigt posé sur la tuile environ une demi-seconde.

Cloudiste ouvre directement la personnalisation du service sélectionné. **B** ou **Retour** ramène à l’accueil et restaure le focus sur cette même tuile.

Un appui court conserve son fonctionnement : il ouvre le service. L’action longue annule ce lancement afin de ne pas ouvrir les deux écrans. Le raccourci s’applique aux quatre services fournis et aux services ajoutés manuellement.

Les raccourcis situés en haut de l’accueil ne changent pas. Un service masqué n’a plus de tuile ; sa personnalisation reste accessible depuis Réglages. L’aide sous les tuiles indique désormais **A maintenu : personnaliser**.

## Comprendre le code

`FocusableSurface` représentait déjà une cible commune au tactile, à l’accessibilité et à la manette. Elle accepte maintenant une action longue facultative. Compose utilise `detectTapGestures` pour distinguer le toucher court de l’appui long. La sémantique `onLongClick` expose également le geste aux services d’accessibilité compatibles.

`LauncherKeys` mémorise les touches maintenues. Certaines manettes répètent A pendant l’appui ; d’autres envoient seulement un événement au début et un autre au relâchement. Cloudiste gère les deux cas. Une répétition peut déclencher le raccourci immédiatement ; la durée au relâchement sert de repli. L’action longue n’est exécutée qu’une fois et supprime l’action courte.

Le délai vient de `ViewConfiguration.getLongPressTimeout()`, la valeur standard d’Android. Aucune nouvelle bibliothèque n’est ajoutée.

`HomeScreen` transmet l’identifiant de la tuile à `MainActivity`, qui ouvre `PersonalizeActivity`. Cela réutilise le même écran et le même ViewModel que le bouton Personnaliser des réglages.

## Installer et tester

Installe **Cloudiste-0.11.0-debug.apk** par-dessus la version précédente avec la même signature, ou ouvre le projet dans Android Studio. L’identifiant Android ne change pas ; services personnels, ordre, visibilité et images sont conservés.

1. Appuie brièvement sur A et vérifie le lancement habituel.
2. Reviens, puis maintiens A sur la même tuile. Sa personnalisation doit s’ouvrir sans lancer le service.
3. Reviens avec B et vérifie que le focus retrouve la tuile.
4. Recommence sur un autre service et vérifie le titre de l’écran.
5. Effectue un appui long avec le doigt, puis reprends à la manette.
6. Vérifie le raccourci sur un service ajouté manuellement.
7. Essaie une pression légèrement trop courte : elle doit agir comme un appui normal.

Les résultats automatisés sont détaillés dans [le rapport de vérification](VERIFICATION-CLOUDISTE-0.11.md). Cette version attend ta validation sur console réelle, car le ressenti du bouton A peut varier selon la manette.
