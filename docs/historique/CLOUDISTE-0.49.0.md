# Cloudiste 0.49.0 — Accessibilité avancée

Cette version enrichit **Réglages → Écran et accessibilité** avec des options destinées aux personnes sensibles aux mouvements, ayant besoin de textes plus grands ou distinguant difficilement certains contrastes.

## Nouveaux réglages

- **Taille du texte** indépendante : normale, grande ou très grande.
- **Focus à contraste renforcé** : le contour de l’élément sélectionné à la manette devient plus épais et utilise la couleur principale du thème.
- **Réduire les animations** : supprime les agrandissements du focus, les transitions glissées entre services et le fondu long des fonds plein écran.
- Les marges de sécurité TV et les trois tailles générales d’interface restent disponibles dans la même rubrique.

L’indicateur progressif d’appui long est conservé même lorsque les animations sont réduites, car il informe directement l’utilisateur du déclenchement de l’action.

## Repères accessibles

Les statuts visibles des services utilisent maintenant un symbole en plus de la couleur :

- `✓` pour une application installée ;
- `↗` pour un service ouvert dans le navigateur ;
- `!` pour une application absente ou à installer ;
- `×` pour une indisponibilité ;
- `◆` pour un dossier.

Les textes et états restent exposés aux services d’accessibilité Android comme TalkBack.

## Sauvegarde

La taille du texte, le contraste du focus et la réduction des animations sont enregistrés dans DataStore. Ils sont également inclus dans les sauvegardes Cloudiste et restaurés sur un autre appareil.

## Test conseillé

1. Ouvre **Réglages → Écran et accessibilité**.
2. Essaie les trois tailles de texte et vérifie le défilement complet de la page.
3. Active le focus renforcé puis navigue avec la croix directionnelle.
4. Active la réduction des animations et change de service en mode plein écran.
5. Vérifie les symboles d’état dans les modes tuiles détaillées et compactes.
6. Exporte puis restaure une sauvegarde contenant ces options.

Version : `0.49.0` — code : `68`.
