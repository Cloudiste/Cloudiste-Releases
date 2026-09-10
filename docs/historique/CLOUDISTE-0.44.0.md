# Cloudiste 0.44.0 — Stabilisation de la bêta fermée

Cette version prépare les retours des premiers testeurs et fiabilise le passage depuis les versions précédentes.

## Nouveautés après une mise à jour

Après l’installation de la 0.44.0, Cloudiste présente une fiche « Nouveautés » une seule fois. La version déjà lue est enregistrée localement dans DataStore. Les services, dossiers, fonds, langues et réglages existants sont conservés.

La fiche reste accessible dans **Réglages > Informations > Nouveautés de cette version**.

## Signaler un problème

La rubrique **Réglages > Diagnostic et retour bêta** contient désormais **Signaler un problème**. Deux choix distincts sont proposés :

- partager le message avec le rapport technique affiché ;
- partager le message sans joindre le rapport.

Le rapport n’est jamais ajouté sans une action explicite. Il contient la version, le modèle d’appareil, Android, la manette détectée, l’état des services, les arrêts techniques fournis par Android, le dernier diagnostic réseau et la durée du dernier démarrage. Il ne contient ni compte, adresse IP, nom de réseau, identifiant matériel, mot de passe ou contenu de connexion.

## Fonds vidéo

Si Android refuse ou perd la lecture d’un fond vidéo, Cloudiste abandonne proprement ce lecteur et affiche le visuel par défaut disponible. Cela évite de conserver un fond noir. Les vidéos valides continuent de boucler sans son et reprennent après un retour dans l’application.

## Langues dans le bundle Google Play

Le bundle garde le français, l’anglais et l’espagnol dans chaque installation. Le changement de langue interne reste ainsi disponible immédiatement, même hors ligne.

## Test conseillé

1. Installe l’APK 0.44.0 par-dessus la version validée, sans désinstaller Cloudiste.
2. Vérifie que la fiche Nouveautés apparaît, puis que ton accueil et tes personnalisations sont conservés.
3. Ferme et relance Cloudiste : la fiche ne doit pas réapparaître.
4. Ouvre-la manuellement depuis **Réglages > Informations**.
5. Dans **Diagnostic et retour bêta > Signaler un problème**, teste le partage sans rapport puis avec rapport et compare les deux textes.
6. Essaie un fond vidéo, quitte l’écran puis reviens sur l’accueil. La vidéo doit reprendre ; si le fichier devient illisible, un visuel de secours doit remplacer le noir.
7. Vérifie ces parcours au doigt, puis à la manette avec la croix, A et B.

Version : `0.44.0` — code : `60`.
