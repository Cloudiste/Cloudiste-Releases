# Cloudiste 0.43.1 — Clean mode

Cette version ajoute un mode d’accueil épuré, accessible depuis **Réglages > Apparence > Clean mode**.

## Éléments masqués

Lorsque le Clean mode est activé, Cloudiste masque :

- le titre « Ton accueil » et le nombre d’éléments ;
- le nom des services et dossiers sur les tuiles ;
- leur état, par exemple application installée, navigateur ou non installée ;
- le type et la priorité de lancement ;
- les notices expliquant les commandes A, B, Y, Select, LB et RB ;
- les mêmes informations dans l’affichage plein écran.

Les fonds, vidéos, GIF, logos, animations de focus, flèches du plein écran et actions du dock restent disponibles. La navigation tactile et manette ne change pas.

Le réglage agit uniquement sur la présentation. Les choix **Afficher le logo**, **Afficher le nom** et **Afficher le statut** enregistrés pour chaque tuile ne sont pas supprimés. Ils sont de nouveau appliqués lorsque le Clean mode est désactivé.

Le réglage est enregistré dans DataStore et inclus dans les sauvegardes Cloudiste.

## Test conseillé

1. Ouvre **Réglages > Apparence** et active **Clean mode**.
2. Reviens sur l’accueil en mode tuiles détaillées : seuls les visuels et logos doivent rester dans les tuiles.
3. Passe aux tuiles compactes puis au plein écran avec Select.
4. Vérifie que les notices et informations restent masquées dans les trois affichages.
5. Vérifie que A ouvre toujours un service, Y sa personnalisation et que le toucher fonctionne.
6. Désactive le Clean mode : les informations autorisées dans la personnalisation de chaque tuile doivent revenir.
7. Redémarre Cloudiste pour confirmer la conservation du choix.

Version : `0.43.1` — code : `59`.
