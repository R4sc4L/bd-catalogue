# 📚 Ma Collection — Catalogue de bandes dessinées & collections

Application web **mono-fichier** pour cataloguer, organiser et explorer une collection de bandes dessinées (et d'autres types de collections). Tout tient dans un seul fichier HTML, fonctionne **100 % en local dans le navigateur**, sans serveur ni compte en ligne, et stocke les données sur votre machine via IndexedDB.

> Aucune donnée ne quitte votre ordinateur : pas de backend, pas de cloud, pas de traçage.

---

## ✨ Fonctionnalités

### Hub multi-collections
Un écran d'accueil présente vos collections sous forme de tuiles (avec compteurs et code couleur), plus une **vue globale** qui agrège toutes les collections. L'architecture repose sur un *Module Registry* déclaratif : ajouter une nouvelle collection = ajouter une entrée, sans toucher au reste du code.

- **BD** — bandes dessinées & comics (module principal)
- **Pin's** — pin's & badges
- **Cartes à jouer** *(à venir)*
- **Cartes postales** *(à venir)*

Les modules sont **activables/désactivables** par l'utilisateur (état mémorisé).

### Gestion des œuvres
- Fiches détaillées : titre, série/cycle, auteurs et rôles, éditeur, collection, année/mois, ISBN, format, tirage, n° d'exemplaire, état, prix d'achat et cote, localisation…
- **Langues multiples** par œuvre, avec affichage des **drapeaux** correspondants dans les vues collection (utile pour les catalogues bilingues).
- Caractéristiques physiques structurées : reliure, couverture et finitions, format ; section dédiée **emboîtage** (étui, coffret, matière, qualité) réservée aux tirages de tête et portfolios.
- Signatures, dédicaces, ex-libris, et contenus additionnels.
- **Remplissage automatique** des fiches par recherche ISBN ou titre (sources : BNF, Google Books, Open Library).

### Vues & navigation
- Trois affichages de la collection : **grille**, **petite grille** et **liste**.
- Tri (catégorie + chronologie, auteur, cote…), filtres (catégorie, auteur, éditeur, année, état, localisation…) et recherche globale.
- **Tableau de bord par collection** (statistiques, dernières acquisitions, répartition par catégorie cliquable).
- Pages dédiées : **Auteurs/Éditeurs**, **Statistiques**, **Catégories**, **Souhaités** (wishlist), **Bibliothèque** (simulation d'étagères).

### Sélection multiple & édition groupée
- Mode sélection avec cases à cocher.
- **Maj+clic** : sélection par plage (tous les items entre deux).
- **Ctrl/Cmd+clic** : ajout/retrait d'un item (et entrée automatique en mode sélection).
- **Ctrl/Cmd+A** : tout sélectionner.
- **Suppr** : supprimer la sélection (avec confirmation).
- Édition groupée de plusieurs œuvres en une fois.

### Confort & accessibilité
- Interface **bilingue français / anglais**.
- En-tête et barre d'outils **collants** (toujours accessibles au défilement).
- Espacement **normé par tokens** pour un rythme visuel cohérent.
- Protection par **code PIN** pour les contenus réservés aux adultes.
- Accès protégé par mot de passe local (avec code de récupération).

### Import / Export
- Export et import **JSON** (sauvegarde complète).
- Export et import **CSV** (tableur).
- Sauvegarde recommandée régulière vers votre cloud personnel.

---

## 🚀 Utilisation

Aucune installation, aucune dépendance, aucun build.

1. Téléchargez `bd-collection.html`.
2. Ouvrez-le dans un navigateur moderne (Chrome, Safari, Firefox, Edge).
3. Créez votre accès local, puis commencez à cataloguer.

> Les données sont stockées dans le navigateur (IndexedDB) **par profil et par navigateur**. Pour transférer votre collection sur une autre machine ou un autre navigateur, utilisez l'**export JSON** puis l'import.

---

## 🛠️ Technique

- **Mono-fichier** : HTML + CSS + JavaScript natif, sans framework ni bibliothèque externe.
- **Stockage** : IndexedDB (base `bdCollectionDB`), `localStorage` pour les préférences.
- **Zéro backend** : tout s'exécute côté client.

---

## 💾 Sauvegarde des données

Comme les données vivent dans le navigateur, pensez à **exporter régulièrement** (JSON) pour ne rien perdre en cas de réinitialisation du navigateur ou de changement de machine.

---

## 🗺️ Feuille de route

- Module **Cartes à jouer**
- Module **Cartes postales**
- Enrichissement de la vue globale cross-collections

---

## 📄 Licence

À définir.

---

*Projet personnel — catalogue de collection, conçu pour un usage local et privé.*
