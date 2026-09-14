# Cloudiste 0.53.0 — Launcher Android facultatif

Cloudiste peut de nouveau être choisi comme écran d’accueil Android. La fonction reste facultative : installer ou mettre à jour l’application ne remplace jamais automatiquement le launcher constructeur.

## Sélection sécurisée

- L’activité principale déclare `MAIN`, `HOME` et `DEFAULT` dans un filtre séparé de son entrée d’application classique.
- La demande utilise le rôle officiel `RoleManager.ROLE_HOME`, disponible depuis Android 10.
- Android affiche sa propre confirmation avant tout changement.
- Si le gestionnaire de rôles n’est pas disponible sur une surcouche constructeur, Cloudiste ouvre successivement les réglages HOME, les applications par défaut puis les réglages généraux.
- La rubrique **Réglages › Launcher Android** affiche l’état réel, permet de gérer le choix et de tester immédiatement le bouton Accueil.

## Démarrage renforcé

Un appel système `HOME` suit désormais un parcours court et déterministe : Cloudiste charge les préférences puis affiche directement l’accueil. Il n’ouvre pas l’assistant de démarrage ni la fiche des nouveautés pendant cette entrée système.

`MainActivity` utilise une tâche unique et ne dépend pas de la restauration d’un ancien état d’Activity. Appuyer plusieurs fois sur Accueil ne crée donc pas plusieurs instances du launcher.

## Revenir au launcher constructeur

Ouvre **Réglages › Launcher Android › Gérer le launcher par défaut**, puis sélectionne l’accueil du constructeur. Le bouton **Réglages Android** du dock reste également disponible.

## Test demandé sur tablette

1. Installe la 0.53.0 par-dessus la version actuelle.
2. Ouvre **Réglages › Launcher Android** et choisis Cloudiste.
3. Lance une autre application puis appuie sur le bouton Accueil.
4. Redémarre la tablette et déverrouille-la.
5. Vérifie que Cloudiste revient directement, avec tes tuiles et ton fond.
6. Recommence un second redémarrage.
7. Restaure temporairement le launcher constructeur, puis sélectionne de nouveau Cloudiste.

Cette version a été validée sur l’appareil cible avant sa publication GitHub.
