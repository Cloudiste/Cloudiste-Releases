# Cloudiste 0.41.1

Cette version complète le diagnostic réseau avec les caractéristiques de la connexion Wi-Fi utilisée.

## Bande Wi-Fi

- Le résultat indique **2,4 GHz**, **5 GHz** ou **6 GHz**.
- La fréquence précise en MHz est affichée à côté de la bande.
- L’information est enregistrée dans le dernier résultat et ajoutée aux rapports partageables.
- Cloudiste ne lit ni le nom du réseau, ni son adresse matérielle, ni son adresse IP.
- Si le constructeur masque la fréquence, la ligne affiche **Indisponible sur cet appareil** et le reste du diagnostic continue normalement.
- Cette lecture utilise une autorisation Wi-Fi simple, sans fenêtre d’autorisation et sans accès à la position.

## Vérifications sur appareil

1. Connecte la tablette à un réseau 2,4 GHz et lance le test rapide.
2. Vérifie que la ligne **Bande Wi-Fi** affiche 2,4 GHz et une fréquence proche de 2 400 MHz.
3. Recommence avec un réseau 5 GHz : la fréquence doit généralement être proche de 5 000 MHz.
4. Si ton routeur et ton appareil utilisent le Wi-Fi 6E ou 7 sur la bande 6 GHz, vérifie également cette valeur.
5. Partage le résultat et vérifie que la bande est présente, sans nom de réseau ni adresse IP.

Version : `0.41.1` — code : `56`.
