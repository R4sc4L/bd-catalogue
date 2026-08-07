# 📚 Ma Collection — Catalogue de bandes dessinées & collections

Application web **mono-fichier** pour cataloguer, organiser et explorer une collection de bandes dessinées (et d'autres types de collections). HTML, CSS et JavaScript natif dans un seul fichier : ni framework, ni build, ni dépendance.

**➡️ Application en ligne : https://r4sc4l.github.io/bd-catalogue/**

---

## Deux variantes, un seul code

Le même fichier fonctionne dans deux modes, choisis automatiquement selon l'adresse d'où il est ouvert.

| | **En ligne** *(référence)* | **Locale** |
|---|---|---|
| Ouverture | https://r4sc4l.github.io/bd-catalogue/ | fichier HTML ouvert directement |
| Stockage | Supabase (Postgres + Storage, région EU) | IndexedDB, dans le navigateur |
| Accès | compte, depuis n'importe quel appareil | un seul navigateur, une seule machine |
| Confidentialité | données hébergées, accès restreint par compte | **rien ne quitte l'ordinateur** |
| Caméra (scanner) | oui | non — nécessite HTTPS |

Depuis **août 2026, la version en ligne fait référence.** La version locale reste utilisable en lecture et pour les sauvegardes, mais ne doit plus recevoir de saisie : les deux bases divergeraient sans possibilité de fusion.

Un repère **⌂ Local / ☁ En ligne** est affiché dans l'en-tête pour lever toute ambiguïté.

---

## ✨ Fonctionnalités

### Hub multi-collections
Un écran d'accueil présente les collections sous forme de tuiles (compteurs, code couleur), plus une **vue globale** qui les agrège. L'architecture repose sur un *Module Registry* déclaratif : ajouter une collection = ajouter une entrée, sans toucher au reste du code.

- **BD** — bandes dessinées & comics (module principal)
- **Pin's** — pin's & badges
- **Cartes à jouer** *(à venir)*
- **Cartes postales** *(à venir)*

Les modules sont activables et désactivables, l'état est mémorisé.

### Fiches adaptées à la catégorie
La fiche d'une œuvre **change selon sa catégorie** : un moteur d'archétypes n'affiche que les champs pertinents.

- **Standard** — album relié : série, cycle, tirage, ISBN, format…
- **Portfolio / Tirage de tête / Édition limitée / Intégrale / Travaux publicitaires** — tirage, n° d'exemplaire, section **emboîtage** (étui, coffret, matière — carton, pleine toile, bristol, découpe laser, plexiglas — et qualité)
- **Planche originale** — technique, dimensions, provenance
- **Éphémères** — fiche allégée, organisée en six familles : ex-libris et estampes, invitations et cartons, presse, imprimés promotionnels, marque-pages, divers

Les éphémères livrés avec un album sont **rattachés à leur album** de façon réciproque : la fiche indique « toujours en place dans l'album », avec un lien direct, et la localisation est héritée.

### Gestion des œuvres
- Titre, série et cycle, auteurs et rôles, éditeur, collection, année, ISBN, format, tirage, n° d'exemplaire, état (avec précisions libres), prix d'achat et cote, localisation.
- **Langues multiples** par œuvre, avec drapeaux dans les vues collection.
- Signatures et dédicaces (dont **tampon**), ex-libris, contenus additionnels.
- **Suivi personnel** : œuvre **lue**, œuvre **prêtée** (à qui, depuis quand) — signalés par des icônes sur les vignettes et sur les rayonnages, avec filtres dédiés et liste des prêts en cours.

### Saisie assistée
- **Scanner de code-barres** par la caméra (EAN-13), avec choix du périphérique vidéo — utilisable depuis l'iPhone, y compris en caméra de continuité sur Mac. Fonctionne sur macOS, iOS, Windows et Android : le décodage passe par l'API du système quand elle existe, sinon par une copie embarquée de ZXing, sans aucun appel réseau.
- **Remplissage automatique** par ISBN ou par titre : BNF, Google Books, Open Library, interrogés en ISBN-13 comme en ISBN-10.
- Les **auteurs inconnus sont créés automatiquement**, avec rapprochement tolérant pour éviter les doublons.
- **Auto-complétion de la liste de souhaits** : saisir une série renseigne l'éditeur, les auteurs et la catégorie d'après les albums déjà possédés.

### Vues & navigation
- Trois affichages : **grille**, **petite grille**, **liste**.
- Tris (catégorie + chronologie de cycle, auteur, cote…), filtres (catégorie, auteur, éditeur, année, état, localisation, lu, prêté) et recherche globale.
- **Tableau de bord** par collection : statistiques, dernières acquisitions, répartition cliquable.
- Pages dédiées : **Auteurs / Éditeurs** (auteurs collectionnés par défaut, bascule « Tous les auteurs »), **Statistiques**, **Catégories**, **Souhaités**, **Bibliothèque** (meubles, étagères, piles et classeurs, ordre réglable).

### Sélection multiple & édition groupée
- Mode sélection avec cases à cocher.
- **Maj+clic** : sélection par plage. **Ctrl/Cmd+clic** : ajout ou retrait. **Ctrl/Cmd+A** : tout sélectionner — y compris les seuls résultats d'une recherche en cours. **Suppr** : supprimer, avec confirmation.
- Édition groupée de plusieurs œuvres en une fois.

### Confort & accessibilité
- Interface **bilingue français / anglais**.
- En-tête et barre d'outils collants.
- Espacement normé par tokens.
- **Code PIN** pour les contenus réservés aux adultes ; accès protégé par mot de passe local avec code de récupération (variante locale).

### Import / Export
- Export **JSON complet et auto-suffisant** : œuvres, auteurs, catégories, Bibliothèque, souhaits, préférences — et **images intégrées au fichier**, y compris depuis la version en ligne où elles ne sont autrement que des liens signés temporaires. Une sauvegarde reste donc exploitable des années plus tard.
- Import JSON en remplacement complet, rejouable autant de fois que nécessaire.
- Export et import **CSV** pour le tableur.

---

## 🚀 Utilisation

**En ligne** — ouvrez https://r4sc4l.github.io/bd-catalogue/ et connectez-vous. Sur iPhone, ajoutez le site à l'écran d'accueil (Partager → *Sur l'écran d'accueil*) : l'application s'ouvre en un geste, scanner compris.

**En local** — téléchargez `index.html`, ouvrez-le dans un navigateur moderne, créez votre accès. Les données sont alors stockées dans le navigateur, **par profil et par navigateur** ; pour les transférer ailleurs, passez par l'export JSON.

---

## 🛠️ Technique

- **Mono-fichier** : HTML + CSS + JavaScript natif, sans framework ni build. Aucune ressource n'est chargée depuis un tiers à l'exécution ; la seule bibliothèque utilisée, le décodeur de codes-barres [ZXing](https://github.com/zxing-js/browser) (Apache-2.0), est embarquée dans le fichier sous forme inerte et n'est évaluée qu'au premier scan.
- **Détection du mode** : le fichier bascule en mode cloud s'il est servi depuis `github.io` (ou avec le paramètre `?cloud`), en mode local sinon.
- **Stockage local** : IndexedDB (base `bdCollectionDB`), `localStorage` pour les préférences.
- **Stockage en ligne** : Supabase — Postgres avec RLS par utilisateur, Storage pour les images. Les champs souples sont regroupés en colonnes JSONB, ce qui permet d'ajouter un champ sans migration SQL.
- **Publication** : `publier-webapp.sh` copie le fichier de travail en `index.html`, montre les changements et demande confirmation avant de pousser sur GitHub Pages.

Le dépôt ne contient qu'un seul fichier d'application, `index.html` : c'est à la fois ce qui est servi en ligne et ce qui se télécharge pour un usage local.

---

## 💾 Sauvegarde

Exportez régulièrement en JSON. Les images étant embarquées dans le fichier, ces exports sont de véritables archives : elles restent lisibles même si l'hébergement disparaissait.

---

## 🗺️ Feuille de route

- **Assistant IA** pour l'enrichissement des fiches — spécifié, différé ; validation champ par champ, jamais d'écriture automatique sur les données factuelles sensibles (ISBN, tirage, pagination, cote)
- Module **Cartes à jouer**
- Module **Cartes postales**
- Enrichissement de la vue globale entre collections
- Déclinaisons Mac, iOS, Android

---

## 📄 Licence

À définir.

---

*Projet personnel — catalogue de collection, développé et éprouvé sur une collection réelle.*
