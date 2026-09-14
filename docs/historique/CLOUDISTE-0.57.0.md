# Cloudiste 0.57.0 — Gestion avancée de l’accueil

Cette version permet d’organiser un accueil chargé sans modifier les tuiles une par une. Le nouveau gestionnaire se trouve dans `Réglages > Accueil > Gérer l’accueil en groupe` et reste utilisable au tactile comme à la manette.

## Nouveautés

- sélection d’une ou de plusieurs tuiles ;
- déplacement groupé des applications sélectionnées vers un nouveau dossier ou un dossier existant ;
- duplication de la configuration visuelle de la première tuile personnalisée vers les autres tuiles sélectionnées ;
- tri manuel, alphabétique, par type ou selon l’utilisation récente ;
- trois tailles globales de tuiles : petite, standard et grande ;
- verrouillage de l’organisation pour empêcher un déplacement accidentel sur l’accueil ;
- pages d’accueil facultatives Cloud, Android, Émulation et Multimédia ;
- affectation groupée des tuiles à une page ;
- navigation entre les pages avec LB et RB ou par toucher ;
- sauvegarde, restauration et compatibilité avec les préférences créées par les versions antérieures ;
- textes français, anglais et espagnols.

## Comportement

Sans page activée, Cloudiste conserve l’accueil unique des versions précédentes. L’utilisateur choisit lui-même les pages à afficher. Les tuiles sans affectation explicite rejoignent automatiquement la page correspondant à leur nature.

Le tri manuel autorise toujours le glisser-déposer. Les tris automatiques et le verrouillage désactivent ce déplacement afin que l’ordre choisi reste stable. Chaque lancement met à jour localement la date d’utilisation servant au tri récent.

Lors d’un déplacement groupé vers un dossier, seules les tuiles associées à une application Android sont déplacées. Un service web sélectionné reste visible sur l’accueil.

## Version

- Nom : `0.57.0`
- Code : `79`
