# Cloudiste 0.41.0

Cette version ajoute un diagnostic réseau conçu pour évaluer rapidement si la connexion convient au cloud gaming.

## Diagnostic réseau

- Accessible depuis **Réglages > Diagnostic et retour bêta > Diagnostic réseau**.
- **Test rapide** : mesure la disponibilité de la connexion, la latence, la gigue et les requêtes perdues en utilisant très peu de données.
- **Test complet** : ajoute les débits descendant et montant. Cloudiste demande une confirmation car le test consomme environ 10 Mo.
- Résultat classé en **Excellent**, **Bon**, **Limité** ou **Faible**, avec un conseil adapté.
- Identification du type de connexion : Wi-Fi, Ethernet, réseau mobile, VPN ou autre.
- Le dernier résultat est enregistré localement et peut être partagé volontairement.
- Le dernier diagnostic peut aussi être joint au rapport bêta existant.

Les boutons et le contenu restent utilisables au doigt et à la manette. Le test n’envoie ni compte Cloudiste, ni identifiant matériel, ni nom du réseau Wi-Fi, ni identifiants de connexion.

## Vérifications sur appareil

1. Ouvre **Réglages > Diagnostic et retour bêta > Diagnostic réseau**.
2. Lance **Test rapide** en Wi-Fi puis vérifie la latence, la gigue et la recommandation.
3. Désactive la connexion, relance le test et vérifie que le message d’absence de réseau est clair.
4. Réactive la connexion puis lance **Test complet**. Confirme l’avertissement de consommation.
5. Partage le résultat et vérifie que le texte ne contient ni adresse IP, ni nom de réseau, ni identifiant personnel.
6. Ferme puis rouvre la page : le dernier résultat doit rester affiché.
7. Refais les actions au doigt puis à la manette.

Version : `0.41.0` — code : `55`.
