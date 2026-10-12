# Marcenat — proposition de nouveau site pour la commune

Proposition de nouveau site pour la commune de Marcenat (Cantal, 15190), sur le modèle du site de
[Saint-Bonnet-de-Condat](https://saint-bonnet-de-condat.fr/), publiée avec GitHub Pages :
https://victorleblondd.github.io/marcenat/

Le site officiel actuel de la commune reste http://www.marcenat15.fr. Tant que la mairie n'a pas adopté
la proposition (`proposition: true` dans `_config.yml`), chaque page affiche un bandeau « Proposition de
nouveau site », le site n'est pas référencé par les moteurs de recherche et les mentions légales sont
au nom de l'auteur de la proposition.

GitHub construit le site automatiquement (Jekyll) à chaque modification de la branche `main`.
Aucune installation n'est nécessaire.

## Sources des contenus

- Le site actuel de la commune, http://www.marcenat15.fr (mairie, services, associations, commerces, gîtes,
  conseil municipal, affichage légal).
- Les avis de la mairie (affiches et textes, octobre 2026).
- *Marcenat Infos* n°1, été 2026 : le mot du maire et les articles du bulletin municipal.
- Wikipédia et l'Insee pour les chiffres clés (population légale 2023, superficie, altitudes).

## Ajouter un avis « Infos & Alertes »

1. Déposer le PDF dans le dossier `documents/infos-alertes/`, nommé `AAAA-MM-JJ-sujet-court.pdf`
   (sans accents ni espaces).
2. Ouvrir `_data/infos_alertes.yml` et copier le modèle (en tête du fichier) **tout en haut de la liste** :
   date, type (`alerte` ou `info`), thème, titre, résumé, nom du PDF.

L'avis apparaît alors sur la page Infos & Alertes et sur l'accueil ; son titre et son bouton ouvrent le PDF.
Une alerte récente s'affiche aussi en bandeau rouge sur l'accueil pendant 3 jours
(ou jusqu'à la date indiquée dans `bandeau_jusquau`).

**Affiche disponible en ligne (image ou PDF) :** au lieu de déposer le fichier, ajouter une ligne
`adresse  documents/infos-alertes/AAAA-MM-JJ-sujet.pdf` dans `outils/fichiers-a-recuperer.txt`.
GitHub télécharge le fichier, convertit une image en PDF A4 et l'ajoute au site
(`.github/workflows/recuperer-fichiers.yml`). Plusieurs images séparées par `|` donnent un PDF de plusieurs pages.

## Ajouter un document à l'affichage légal

1. Déposer le PDF dans le dossier `documents/affichage-legal/`, nommé `AAAA-MM-JJ-sujet-court.pdf`
   (ou ajouter son adresse dans `outils/fichiers-a-recuperer.txt`).
2. Ouvrir `_data/affichage_legal.yml` et copier le modèle **en tête de la liste `documents`** :
   date de publication, type (`compte-rendu`, `deliberation`, `proces-verbal`, `convocation`,
   `arrete-municipal`, `arrete-prefectoral` ou `divers`), numéro (facultatif), titre, nom du PDF.

Les années proposées dans le filtre se règlent dans le même fichier (`annees`). Le filtre « Année »
n'apparaît qu'à partir de deux années.

## Publier une version (Release)

Pour marquer une version importante, ajouter un fichier `outils/versions/vX.Y.Z.md`
(par exemple `v1.0.0.md`) : titre, commit marqué, puis les notes.
GitHub crée alors la Release correspondante (`.github/workflows/publier-version.yml`).

## Modifier les informations

| À modifier | Fichier |
|---|---|
| Adresse, téléphone, horaires de la mairie, agence postale, médiathèque | `_data/mairie.yml` |
| Maire, adjoints, délégations, permanences, conseillers | `_data/elus.yml` |
| Menu principal | `_data/navigation.yml` |
| Bandeau d'annonce temporaire de l'accueil (texte, dernier jour d'affichage) | `_data/annonce.yml` |
| Encadrés « Sécheresse » (afficher ou masquer) | `_data/secheresse.yml` |
| Articles du bulletin municipal | `_posts/AAAA-MM-JJ-titre.html` (un fichier par article) |
| Pages | `mairie.html`, `vie-pratique.html`, `vie-locale.html`, `decouvrir.html`… |
| Apparence | `assets/css/site.css` |
| Proposition / site adopté par la commune | `_config.yml` (`proposition`) |

## Le jour où la mairie adopte le site

1. Dans `_config.yml`, passer `proposition` à `false` (le bandeau disparaît, le site devient référençable
   et les mentions légales passent au nom de la commune).
2. Avec un nom de domaine : ajouter un fichier `CNAME` contenant le domaine, mettre `url` sur
   `https://le-domaine.fr` et `baseurl` sur `""`, puis configurer la zone DNS (comme pour Saint-Bonnet-de-Condat).

## Organisation

- `_layouts/` : gabarits communs (en-tête, pied de page, pages, articles)
- `_includes/` : éléments réutilisés (avis, cartes, horaires, icônes, dates en français)
- `assets/images/` : blason du Cantal et logo du massif du Cézallier
- `documents/infos-alertes/` : avis en PDF
- `documents/affichage-legal/` : documents de l'affichage légal en PDF
- `documents/transports/` : horaires des lignes de car

## Crédits

Blason du Cantal : dessin de Gretaz et contributeurs (Wikimedia Commons), licence CC BY-SA 3.0, image adaptée.
