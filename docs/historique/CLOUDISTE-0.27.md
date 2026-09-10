# Cloudiste 0.27.0 — Launcher Android par défaut

Cloudiste peut maintenant être choisi comme écran d’accueil Android. Cette fonction transforme l’application en véritable launcher tout en conservant son icône dans le tiroir d’applications.

## Ce qui change

L’activité principale déclare désormais les catégories Android `HOME` et `DEFAULT`. Android reconnaît ainsi Cloudiste comme candidat au rôle de launcher. La catégorie `LAUNCHER` reste présente dans un filtre séparé : Cloudiste peut toujours être ouvert comme une application classique.

Le mode `singleTask` évite de créer plusieurs accueils Cloudiste chaque fois que le bouton système **Accueil** est pressé.

## Choisir Cloudiste

1. Ouvre **Réglages** dans le dock de Cloudiste.
2. Dans la nouvelle rubrique **Launcher Android**, sélectionne **Choisir Cloudiste comme launcher par défaut**.
3. Dans la fenêtre Android, sélectionne **Cloudiste**, puis confirme avec **Définir par défaut**.
4. Appuie sur le bouton système **Accueil** : Cloudiste doit apparaître directement.

Le bouton est accessible au toucher, à la croix et avec **A**. Une fois Cloudiste sélectionné, son libellé devient **Cloudiste est le launcher par défaut · Gérer** et ouvre la page Android permettant de changer à nouveau ce choix.

Le texte de la fenêtre de confirmation dépend de la langue d’Android. Certains constructeurs utilisent un chemin différent, par exemple **Paramètres > Applications > Applications par défaut > Application d’accueil**. Cloudiste utilise d’abord le dialogue officiel du rôle `HOME`, puis la page des applications par défaut comme solution de repli.

## Revenir au launcher précédent

Dans **Réglages > Launcher Android**, choisis **Gérer**, puis sélectionne le launcher du constructeur. Tu peux aussi passer directement par les paramètres Android des applications par défaut.

## Essai conseillé

1. Effectue la sélection uniquement avec la manette, puis reviens avec **B** sans confirmer.
2. Recommence au toucher et confirme Cloudiste.
3. Lance une autre application, puis presse le bouton système **Accueil**.
4. Vérifie l’ouverture du tiroir d’applications et des réglages Android depuis Cloudiste.
5. Redémarre l’appareil et vérifie que Cloudiste reste l’accueil choisi.
6. Rouvre la rubrique Launcher Android et restaure temporairement le launcher constructeur afin de valider le chemin de retour.

