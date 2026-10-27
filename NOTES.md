# Inkyo View — Notes du projet

> Fichier vivant : à chaque ajout, on met à jour la section « Journal » et la « Feuille de route ».
> Début d'une nouvelle discussion : joindre ce fichier + `index.html`.

## Vision
Passer d'une simple visionneuse de planches à une **boîte à outils du mangaka + site de lecture**, 100 % dans le navigateur (téléphone d'abord), hébergée sur GitHub Pages (https://minouemmanuel72-dot.github.io/Inkyo-view2/).

## État actuel (v5)
- Importer ses planches (images), réordonner, supprimer.
- 3 vues : **Lire** (2D), **3D** (livre avec épaisseur, rotation, pages courbes), **Maquette** (dos + 4e de couverture, largeur du dos calculée).
- Sens de lecture japonais / occidental.
- Enregistrement vidéo (+ son de pages), plein écran immersif.
- Sauvegarde locale (IndexedDB), installable (PWA), thème auto / clair / sombre.
- Onglet **Trames** : points, dégradé, ciel, grain, lignes de vitesse ; motifs points/lignes/croisé/carrés ; « Mes trames » ; export PNG transparent.
- Onglet **Planche** : gabarit (format, fond perdu, coupe, sécurité, découpages de cases) en PNG ; vérification DPI d'une planche.

## Technique
- Trois pages : `index.html` (Livre), `trames.html`, `planche.html`, reliées par les onglets en haut. Un seul fichier chacune (CSS + JS inclus) + `sw.js`, `manifest.webmanifest`, 3 icônes.
- Moteur WebGL maison (pas de bibliothèque externe).
- Cache hors-ligne : nom `inkyo-view-vN` dans `sw.js` → **augmenter N à chaque mise à jour**.

## Mettre à jour sur GitHub (téléphone)
1. Supprimer les anciens téléchargements du téléphone (éviter `index(1).html`).
2. Dans le dépôt : supprimer l'ancien fichier, puis Add file → Upload files avec le nouveau (nom exact).
3. Ne jamais éditer dans l'éditeur GitHub (risque de caractères parasites).
4. Attendre la coche verte dans Actions, puis ouvrir le site avec `?v=N`.

## Feuille de route
### Atelier de création
- [x] Générateur de trames (v4) : points, lignes, croisé ; dégradé linéaire/radial ; ciel (nuages, étoiles) ; export PNG transparent
- [x] Trames v5 : grain, lignes de vitesse (concentration/parallèles), carrés, « Mes trames »
- [ ] Trames : éclairs, fond de ville/hachures, trames de tissu
- [x] Gabarits de planche (v5) : cases, marges, coupe, fond perdu
- [x] Vérification d'impression (v5) : résolution (DPI) et proportions d'une planche
- [ ] Export PDF du livre complet pour l'imprimeur
- [ ] Bulles et texte : bibliothèque de bulles, onomatopées
- [ ] Storyboard / chemin de fer : vue d'ensemble des pages, rythme (doubles pages, tournées de page)
- [ ] Calques de repères : grille, règle, points de fuite

### Site de lecture (Inkyo)
- [ ] Liste de séries / chapitres, couvertures
- [ ] Lecteur vertical (webtoon) et page par page
- [ ] Lien de partage d'un chapitre
- [ ] Pas de compte au début : lecture libre ; comptes/stockage plus tard

## Journal
- v1 : visionneuse 2D, import.
- v2 : 3D, maquette, vidéo, PWA, sauvegarde.
- v5 : grain, vitesse, carrés, Mes trames ; onglet Planche (gabarit + vérification) ; cache `inkyo-view-v5`.
- v4 : onglet Trames (générateur points / dégradé / ciel), `trames.html`.
- v3 : netteté des images, vert lumineux, thèmes clair/sombre, nouvelles icônes.
