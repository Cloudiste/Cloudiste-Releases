# Cloudiste 0.48.0 — Centre de mises à jour

Cette version permet de vérifier les nouvelles versions de Cloudiste directement dans l’application, tout en conservant l’installation sous le contrôle d’Android et de l’utilisateur.

## Centre de mises à jour

Une nouvelle rubrique **Centre de mises à jour** est disponible dans la navigation latérale des Réglages. Elle affiche :

- la version installée ;
- la dernière version publiée sur le dépôt GitHub officiel ;
- les notes de la release ;
- le canal d’installation détecté : **Google Play** ou **GitHub / Obtainium** ;
- un bouton d’actualisation manuelle ;
- un bouton ouvrant la release dans le navigateur externe.

Cloudiste vérifie la dernière release GitHub au démarrage et conserve le résultat pendant six heures. Si le réseau est momentanément indisponible, les dernières informations enregistrées peuvent encore être consultées.

## Alerte sur l’accueil

Lorsqu’une version plus récente existe, un petit point apparaît sur le pictogramme **Réglages** du Dock. Cette alerte reste volontairement discrète et ne demande aucune permission de notification Android.

## Confidentialité et sécurité

- La vérification interroge uniquement l’API publique du dépôt `Cloudiste/Cloudiste-Releases`.
- Aucun identifiant, réglage personnel ou contenu de l’appareil n’est envoyé.
- Cloudiste ne télécharge et n’installe jamais une mise à jour automatiquement.
- La page de release s’ouvre toujours dans le navigateur externe.

## Test conseillé

1. Ouvre **Réglages**, puis **Centre de mises à jour**.
2. Vérifie la version installée et le canal affiché.
3. Sélectionne **Actualiser** avec la manette puis au doigt.
4. Ouvre la release GitHub et vérifie qu’elle apparaît dans le navigateur externe.
5. Coupe temporairement le réseau et vérifie que les dernières informations enregistrées restent lisibles.

Version : `0.48.0` — code : `67`.
