# Inkyo View — Notes du projet

> Fichier vivant : à chaque ajout, on met à jour la section « Journal » et la « Feuille de route ».
> Début d'une nouvelle discussion : joindre ce fichier + `index.html`.

## Vision
Passer d'une simple visionneuse de planches à une **boîte à outils du mangaka + site de lecture**, 100 % dans le navigateur (téléphone d'abord), hébergée sur GitHub Pages (https://minouemmanuel72-dot.github.io/Inkyo-view2/).

## État actuel (v7)
- Importer ses planches (images), réordonner, supprimer.
- 3 vues : **Lire** (2D), **3D** (livre avec épaisseur, rotation, pages courbes), **Maquette** (dos + 4e de couverture, largeur du dos calculée).
- Sens de lecture japonais / occidental.
- Enregistrement vidéo (+ son de pages), plein écran immersif.
- **Projets multiples** (v7) : autant de projets que voulu, chacun avec ses planches et sa maquette ; barre de projets en haut du Livre ; renommer / dupliquer / supprimer. Stockage IndexedDB : `projects`, `current`, `p:<id>:imgs|settings|meta`.
- Vidéo (v7) : tour complet (tout le livre, puis dos et 4e de couverture), tour rapide, vitesse réglable, enregistrement à la main jusqu'à 5 min, écran gardé allumé.
- Sauvegarde locale (IndexedDB), installable (PWA), thème auto / clair / sombre.
- Onglet **Trames** : points, dégradé, ciel, grain, lignes de vitesse ; motifs points/lignes/croisé/carrés ; « Mes trames » ; export PNG transparent.
- Onglet **Lire** : site de lecture (bibliothèque, séries, chapitres, lecteur page par page ou défilement, reprise de lecture, partage de lien `lire.html#/r/<serie>/<chapitre>`).
- Onglet **Publier** : reprend les planches d'un projet du Livre (`publier.html?projet=<id>`), série publique ou privée (lien non listé, `prive:true` dans le catalogue ; pas un vrai mot de passe), couverture = 1re planche ; ajoute un chapitre en un bouton (images optimisées, 1 commit GitHub via un jeton) ; repli ZIP ; retirer un chapitre.
- Onglet **Planche** : gabarit (format, fond perdu, coupe, sécurité, découpages de cases) en PNG ; vérification DPI d'une planche.

## Technique
- Cinq pages : `index.html` (Livre), `trames.html`, `planche.html`, `lire.html`, `publier.html`, reliées par les onglets en haut. Un seul fichier chacune (CSS + JS inclus) + `sw.js`, `manifest.webmanifest`, 3 icônes.
- Moteur WebGL maison (pas de bibliothèque externe).
- Cache hors-ligne : nom `inkyo-view-vN` dans `sw.js` → **augmenter N à chaque mise à jour**.

## Contenu du site de lecture
- `catalogue.json` à la racine du dépôt : séries et chapitres (champs : id, titre, auteur, resume, sens rtl/ltr, lecture page/scroll, couverture, chapitres[n, titre, dossier, pages, ext, date]).
- Images : `serie/<id>/ch001/001.jpg`… et `serie/<id>/cover.jpg`. Écrits par l'onglet Publier (jeton GitHub fine-grained, Contents read/write, stocké seulement dans le navigateur).
- `sw.js` ne met pas en cache `/serie/` et lit `catalogue.json` en priorité sur le réseau.

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
- [x] Liste de séries / chapitres, couvertures (v6)
- [x] Lecteur vertical (webtoon) et page par page (v6)
- [x] Lien de partage d'un chapitre (v6)
- [x] Pas de compte : lecture libre
- [ ] Plus tard : double page en paysage, recherche, genres, mise en avant, commentaires/likes (nécessite une base de données), comptes lecteurs, statistiques

## Journal
- v1 : visionneuse 2D, import.
- v2 : 3D, maquette, vidéo, PWA, sauvegarde.
- v7 : projets multiples, tour vidéo complet, Publier depuis un projet, séries privées (lien non listé), cache `inkyo-view-v7`.
- v6 : onglets Lire et Publier, `catalogue.json`, cache `inkyo-view-v6`.
- v5 : grain, vitesse, carrés, Mes trames ; onglet Planche (gabarit + vérification) ; cache `inkyo-view-v5`.
- v4 : onglet Trames (générateur points / dégradé / ciel), `trames.html`.
- v3 : netteté des images, vert lumineux, thèmes clair/sombre, nouvelles icônes.
