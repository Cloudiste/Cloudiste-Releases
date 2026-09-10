# Cloudiste 0.21.0 — Services web et nouvelle icône

Cette version corrige les premiers éléments de la feuille de route vers Google Play. Elle ne change ni les services enregistrés, ni leur ordre, ni les fonds personnalisés.

## Découvrir

La fiche d’un service non installé ne présente plus deux chemins vers la même page Google Play. Le bouton principal « Installer depuis Google Play » suffit ; la rangée inférieure conserve uniquement le site internet. Lorsque l’application est déjà installée, le bouton principal l’ouvre et la fiche Google Play reste disponible séparément pour consulter sa page ou ses mises à jour.

Le site associé à Boosteroid utilise désormais le lien affilié demandé : `https://boosteroid.com/go/b/m624z`.

## Services web

Le catalogue distingue explicitement trois cas : application uniquement, navigateur uniquement, ou application et navigateur. Cette information commune pilote l’accueil, les réglages, Découvrir et le lancement.

Xbox Cloud Gaming et Amazon Luna sont configurés comme services web. Leur tuile affiche « Via navigateur web », « Navigateur » et « Lancement par navigateur ». Les mentions « Application à vérifier » et « Priorité » ont disparu. Ils ouvrent directement le lecteur web et ne tentent jamais de lancer une application inconnue.

GeForce NOW et Boosteroid conservent le choix entre application et web. Les autres services actuellement référencés utilisent leur application Android.

## Retour depuis un jeu web

Cloudiste ne détourne plus B, même lorsqu’il est maintenu. B reste transmis à la page de jeu. Start maintenu ouvre toujours le menu du lecteur.

Pour quitter le lecteur, utilise le retour Android : geste Retour, bouton de navigation du système ou touche Retour Android. Ce retour ferme le lecteur et revient à la fiche ou à l’accueil précédent.

## Nouvelle icône

Le logo carré fourni est utilisé comme icône adaptative et ronde. Son dessin a été conservé sans génération ni réinterprétation ; seule sa taille a été adaptée aux ressources Android. L’icône apparaît aussi sur l’écran de lancement du système.

Aucune dépendance ni permission Android supplémentaire n’a été ajoutée.

## Essai sur appareil réel

1. Installe la 0.21.0 par-dessus la version précédente et vérifie que tes services, leur ordre, le thème et les fonds sont conservés.
2. Vérifie la nouvelle icône Cloudiste dans le tiroir d’applications et sur l’écran de lancement.
3. Sur l’accueil, contrôle les tuiles Xbox et Luna : elles doivent afficher « Navigateur » et aucune mention de priorité.
4. Ouvre Réglages : Xbox et Luna ne doivent pas proposer de choix application/web. GeForce NOW et Boosteroid doivent conserver ce choix.
5. Ouvre Découvrir puis la fiche Boosteroid. Si l’application n’est pas installée, tu dois voir un seul bouton Google Play et un bouton Site internet.
6. Active le site internet de Boosteroid et vérifie que le navigateur ouvre l’adresse affiliée.
7. Lance Xbox ou Luna, puis maintiens B pendant plusieurs secondes : le lecteur doit rester ouvert et le jeu doit continuer à recevoir la commande.
8. Utilise ensuite le retour Android : Cloudiste doit revenir à l’écran précédent.
9. Recommence les parcours Découvrir et accueil au toucher, puis uniquement à la manette.
