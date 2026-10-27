# Inkyo View — Notes du projet

> Fichier vivant : à chaque ajout, on met à jour la section « Journal » et la « Feuille de route ».
> Début d'une nouvelle discussion : joindre ce fichier + `index.html`.

## Vision
Passer d'une simple visionneuse de planches à une **boîte à outils du mangaka + site de lecture**, 100 % dans le navigateur (téléphone d'abord), hébergée sur GitHub Pages (https://minouemmanuel72-dot.github.io/Inkyo-view2/).

## État actuel (v3 — vert lumineux, clair/sombre)
- Importer ses planches (images), réordonner, supprimer.
- 3 vues : **Lire** (2D), **3D** (livre avec épaisseur, rotation, pages courbes), **Maquette** (dos + 4e de couverture, largeur du dos calculée).
- Sens de lecture japonais / occidental.
- Enregistrement vidéo (+ son de pages), plein écran immersif.
- Sauvegarde locale (IndexedDB), installable (PWA), thème auto / clair / sombre.

## Technique
- Un seul fichier `index.html` (CSS + JS inclus) + `sw.js`, `manifest.webmanifest`, 3 icônes.
- Moteur WebGL maison (pas de bibliothèque externe).
- Cache hors-ligne : nom `inkyo-view-vN` dans `sw.js` → **augmenter N à chaque mise à jour**.

## Mettre à jour sur GitHub (téléphone)
1. Supprimer les anciens téléchargements du téléphone (éviter `index(1).html`).
2. Dans le dépôt : supprimer l'ancien fichier, puis Add file → Upload files avec le nouveau (nom exact).
3. Ne jamais éditer dans l'éditeur GitHub (risque de caractères parasites).
4. Attendre la coche verte dans Actions, puis ouvrir le site avec `?v=N`.

## Feuille de route
### Atelier de création
- [ ] Générateur de trames (screentones) : points, lignes, dégradés, densité/angle/taille, export PNG transparent
- [ ] Gabarits de planche : cases, marges, zone de coupe/fond perdu, repères d'impression
- [ ] Vérification d'impression : dimensions, résolution (DPI), marges de sécurité
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
- v3 : netteté des images, vert lumineux, thèmes clair/sombre, nouvelles icônes.
