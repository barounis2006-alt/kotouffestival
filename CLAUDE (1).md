# Projet : Site web Kotouf

<!-- À placer à la racine du dépôt du site. Complète le ~/.claude/CLAUDE.md global. -->
<!-- Les éléments marqués TODO sont à vérifier ou compléter par toi. -->

## Contexte

Kotouf est une association culturelle à but non lucratif de Houmet Souk, Djerba (Tunisie), qui promeut la littérature et la lecture. Le site est une **page unique (one-page)** statique.

**Langue de travail : français.** Les échanges, les commentaires de code et les textes du site sont en français. Le contenu du site est multilingue là où c'est prévu (FR/EN/AR pour la section Programme).

## Stack technique

| Couche | Technologie |
|--------|------------|
| Langage | HTML5 / CSS3 / JavaScript (vanilla) |
| Structure | `index.html` + CSS et JS associés (TODO : confirmer les noms/dossiers) |
| Base de données | Aucune (site statique) |
| Style | CSS maison avec variables (design tokens) |
| Polices | Google Fonts : Archivo Black, Newsreader, JetBrains Mono |
| Animation | GSAP + Lenis (via CDN) ; effets inspirés de React Bits recréés en JS vanilla |
| Formulaire | Formspree (candidature bénévole, "Envoyer ma candidature") |
| Hébergement | GitHub Pages |

### Règles pour les animations

- Intégrer **GSAP** (ScrollTrigger si besoin) et **Lenis** (défilement fluide) via CDN avec une version exacte (jamais `latest`).
- Le site est en HTML/JS vanilla : les composants **React Bits** ne sont pas utilisables tels quels. Recréer l'effet voulu (texte animé, boutons magnétiques, fonds animés) avec GSAP.
- Respecter `prefers-reduced-motion` : désactiver Lenis et réduire les animations dans ce cas.
- Ne jamais bloquer le contenu ni le SEO derrière une animation (le texte doit rester dans le HTML).

## Design

- **Palette méditerranéenne** : beige, blanc, bleu, terracotta.
- **Motifs** : portes bleues de Djerba, architecture locale, **arche djerbienne** (motif signature).
- **Typographie** : Archivo Black (titres), Newsreader (texte), JetBrains Mono (détails).
- Utiliser les **variables CSS existantes** (couleurs, polices, espacements). Pas de valeurs en dur si une variable existe.
- Photos réelles dans la galerie et les en-têtes de cartes d'activités (les placeholders SVG ont été remplacés).

## Sections du site

Activités ("Nos activités"), Programme (multilingue FR/EN/AR, onglets par jour, bouton de téléchargement PDF), Événements, Galerie, Actualités, Dons, Formulaire bénévole. (TODO : compléter la liste exacte des 10 sections.)

## Règles du projet

- **Branches** : `main` = production (GitHub Pages). Travailler sur une branche, puis fusionner.
- **Commits** : style conventionnel (`feat:`, `fix:`, `content:`, `chore:`, `refactor:`).
- **HTML sémantique** (`header`, `nav`, `main`, `section`, `footer`), un seul `h1`, hiérarchie de titres correcte.
- **Accessibilité** : `alt` sur toutes les images, contrastes suffisants, navigation clavier, `aria-label` sur les boutons-icônes, onglets accessibles dans la section Programme.
- **Responsive** : mobile d'abord. Vérifier à 360 px, 768 px et 1280 px.
- **Images** : nommage sans espaces ni accents, formats optimisés (WebP si possible), `loading="lazy"` hors écran initial.
- **Pas de données personnelles** (téléphones, e-mails de bénévoles) dans le dépôt.

## Tests (vérifications manuelles)

Pas de suite de tests automatisés. Avant chaque commit :

1. Ouvrir `index.html` en local (ou `npx serve`) et parcourir toutes les sections.
2. Vérifier la console du navigateur : aucune erreur.
3. Tester mobile et desktop, avec et sans `prefers-reduced-motion`.
4. Vérifier les liens (Facebook Reel dans "Nos activités", boutons de don, PDF du programme).
5. Tester le formulaire (envoi réel Formspree) après tout changement.

## Déploiement

| Environnement | URL | Branche | Déploiement auto |
|---------------|-----|---------|------------------|
| Production | TODO : URL GitHub Pages | `main` | Oui (GitHub Pages) |
| Local | `http://localhost:3000` | toute | N/A |

**Checklist avant mise en ligne :**
1. Toutes les vérifications ci-dessus passent.
2. `sitemap.xml` et `robots.txt` à jour (soumission Google Search Console).
3. Balises SEO présentes : `title`, `meta description`, Open Graph, `lang`.
4. Chemins relatifs corrects (GitHub Pages sert parfois depuis un sous-dossier du dépôt).

## Formulaire bénévole (Formspree)

GitHub Pages n'a pas de traitement serveur : le formulaire envoie ses données à **Formspree** (`action="https://formspree.io/f/TODO_ID"`). Ne pas casser les attributs `name` des champs. Prévoir un message de confirmation et un champ anti-spam (honeypot).

## Section Programme

- Contenu multilingue FR/EN/AR (l'arabe en `dir="rtl"`).
- Onglets par jour, bouton de téléchargement du PDF.
- La mise à jour du programme (Kotouf 2, du 14 au 17 octobre) se fait à partir du document Word fourni : conserver la structure et le style existants, ne changer que les contenus.

## Terminologie

| Terme | Signification |
|-------|--------------|
| Kotouf | Nom de l'association |
| Houmet Souk | Ville de Djerba où se trouve l'association |
| Arche djerbienne | Motif graphique signature du site |
| Programme | Section multilingue avec onglets par jour |

## Pièges connus

- GitHub Pages ne gère pas les formulaires : toujours passer par Formspree.
- Renommer une image oblige à mettre à jour le HTML et le CSS qui la référencent.
- Texte arabe : vérifier `dir="rtl"`, l'alignement et la police de repli.
- Lenis peut gêner les ancres et les onglets : tester les liens internes (`#section`) après tout changement d'animation.
