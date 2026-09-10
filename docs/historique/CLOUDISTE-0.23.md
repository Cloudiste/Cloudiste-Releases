# Cloudiste 0.23.0 — Dock personnalisable

Cette version transforme le dock inférieur en accès rapide aux outils de Cloudiste et aux applications choisies sur l’appareil.

## YouTube Cloud Gaming France

Le pictogramme YouTube ouvre directement `https://www.youtube.com/@cloudgamingfrance`. Android utilise l’application YouTube lorsqu’elle accepte ce lien et conserve le navigateur comme solution de repli.

## Ajouter une application au Dock

1. Ouvre **Applications** depuis le dock.
2. Place la surbrillance sur une application.
3. Appuie sur **Y**, maintiens **A**, ou effectue un appui long avec le doigt.
4. Dans le menu volant, choisis **Ajouter au Dock**.

L’icône réelle de l’application apparaît à droite des outils fixes. Une pression sur A ou un toucher l’ouvre directement.

Le même menu propose **Retirer du Dock** lorsqu’une application y figure déjà. Cela retire seulement le raccourci et ne désinstalle jamais l’application.

## Persistance et applications supprimées

Les identifiants des applications épinglées et leur ordre sont enregistrés avec DataStore. À chaque retour sur l’accueil, Cloudiste relit les applications réellement installées. Un raccourci dont l’application a été désinstallée est retiré automatiquement.

Le dock conserve une largeur limitée et centrée. Lorsqu’il contient davantage d’icônes, il défile horizontalement au doigt et suit automatiquement la sélection à la manette.

## Essai sur appareil réel

1. Vérifie que le pictogramme YouTube ouvre la chaîne Cloud Gaming France dans l’application YouTube ou le navigateur.
2. Dans Applications, ajoute deux applications au Dock avec Y puis avec un appui long tactile.
3. Reviens à l’accueil et ouvre chacune d’elles depuis son icône.
4. Ajoute assez d’applications pour faire défiler le dock horizontalement, au doigt puis à la croix.
5. Retire une application depuis son menu volant et vérifie qu’elle reste installée.
6. Redémarre Cloudiste et confirme que les autres raccourcis et leur ordre sont conservés.
