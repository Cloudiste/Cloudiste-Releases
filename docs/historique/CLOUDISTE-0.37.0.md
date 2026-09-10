# Cloudiste 0.37.0 — Accueil et applications plus directs

Cette version rend les flèches gauche et droite du mode plein écran tactiles. Elles conservent la navigation à la manette avec LB et RB ainsi que le glissement horizontal.

Le bouton **Ajouter un service** a été retiré du Dock de l’accueil. Dans **Applications**, Y ou un appui long sur une application ouvre maintenant un panneau avec deux choix : l’ajouter ou la retirer du Dock, et l’ajouter comme service sur l’accueil. Si le service existe déjà, l’action réaffiche sa tuile.

La liste des applications conserve son dernier résultat en mémoire. Lors des ouvertures suivantes, cette liste apparaît immédiatement pendant qu’Android vérifie silencieusement les installations et désinstallations. Le bouton **Actualiser** reste disponible.

Le contenu du commutateur Sombre/OLED/Clair est centré et sa zone tactile reste limitée au bouton visible.

La version Android passe à `versionName 0.37.0` et `versionCode 45`.

## Tester

1. Passe en mode plein écran et touche les flèches gauche et droite.
2. Vérifie que le Dock de l’accueil ne contient plus le bouton **+**.
3. Ouvre **Applications**, maintiens une application, puis teste **Ajouter au Dock** et **Ajouter comme service**.
4. Reviens à l’accueil puis rouvre **Applications** : la dernière liste doit apparaître sans écran de chargement.
5. Installe ou désinstalle une application, reviens dans **Applications** et vérifie que la liste se met à jour automatiquement.
6. Vérifie le centrage de l’icône et du texte dans le bouton de thème, au doigt et à la manette.
