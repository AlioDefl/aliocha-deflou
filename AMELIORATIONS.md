# Liste des Améliorations du Site Web

Ce document répertorie tous les problèmes identifiés et les améliorations à apporter au site portfolio.

---

## 🔴 Bugs & Problèmes Critiques

### 1. Dates obsolètes dans sitemap.xml
- **Fichier**: `sitemap.xml`
- **Problème**: Les dates `lastmod` indiquent 2025-12-08 alors que nous sommes en 2026
- **Action**: Mettre à jour toutes les dates avec la date actuelle

### 2. Copyright obsolète
- **Fichiers**: `index.html:325`, `formations.html:336`, `projets.html:198`
- **Problème**: © 2025 au lieu de © 2026
- **Action**: Mettre à jour l'année dans tous les footers

### 3. Skip-link mal configuré
- **Fichier**: `index.html:151`
- **Problème**: Le lien d'accessibilité pointe vers `#accueil` au lieu de `#main-content`
- **Action**: Changer `href="#accueil"` en `href="#main-content"`

---

## 🟠 Problèmes d'Accessibilité (WCAG)

### 4. Skip-link manquant sur les pages secondaires
- **Fichiers**: `formations.html`, `projets.html`
- **Problème**: Pas de lien "Aller au contenu principal" pour les utilisateurs de lecteurs d'écran
- **Action**: Ajouter `<a href="#main-content" class="skip-link">Aller au contenu principal</a>` et le CSS associé

### 5. Navigation sans aria-label sur pages secondaires
- **Fichiers**: `formations.html:205`, `projets.html:105`
- **Problème**: `<nav>` sans attribut `aria-label` ni `role="navigation"`
- **Action**: Ajouter `role="navigation" aria-label="Navigation principale"`

### 6. Carte "CV Numérique" non interactive au clavier
- **Fichier**: `projets.html:180`
- **Problème**: Cette carte n'a pas de `onclick`, `tabindex`, ni `role="button"` alors que les autres l'ont
- **Action**: Soit retirer `cursor:default` et ajouter une interaction, soit la distinguer visuellement comme non-cliquable

### 7. Contraste de couleur insuffisant
- **Fichiers**: Tous
- **Problème**: `--text-muted: #999` sur fond `#fafafa` = ratio de contraste ~2.8:1 (minimum WCAG AA = 4.5:1)
- **Action**: Changer `--text-muted` en `#767676` ou plus foncé pour un ratio ≥ 4.5:1

### 8. ID main-content manquant
- **Fichiers**: `formations.html`, `projets.html`
- **Problème**: Les balises `<main>` n'ont pas d'attribut `id="main-content"`
- **Action**: Ajouter `id="main-content"` aux balises `<main>`

---

## 🟡 Problèmes SEO

### 9. Meta tags Twitter manquants
- **Fichiers**: `formations.html`, `projets.html`
- **Problème**: Pas de `<meta name="twitter:card">` contrairement à index.html
- **Action**: Ajouter les meta tags Twitter sur toutes les pages

### 10. Theme-color incohérent
- **Fichier**: `index.html:21`
- **Problème**: `theme-color` est `#1a1a1a` sur index.html mais `#fafafa` sur les autres pages
- **Action**: Uniformiser sur toutes les pages (recommandé: `#fafafa` pour cohérence avec le design clair)

### 11. Apple-touch-icon manquant
- **Fichiers**: `formations.html`, `projets.html`
- **Problème**: Pas de `<link rel="apple-touch-icon">` contrairement à index.html
- **Action**: Ajouter `<link rel="apple-touch-icon" href="favicon.png">`

---

## 🟢 Améliorations UX/Design

### 12. Navigation mobile absente
- **Fichiers**: Tous (CSS `@media(max-width:500px)`)
- **Problème**: Sur mobile < 500px, la navigation disparaît complètement sans alternative (hamburger menu)
- **Action**: Implémenter un menu hamburger pour mobile avec toggle JavaScript

### 13. Pas de feedback visuel au chargement des modales
- **Fichiers**: `index.html`, `projets.html`
- **Problème**: Aucune indication visuelle pendant l'ouverture de la modale
- **Action**: Optionnel - ajouter une micro-animation ou transition plus visible

### 14. Certifications span 2 colonnes cassé sur tablette
- **Fichier**: `index.html:308`
- **Problème**: `grid-column: span 2` ne fonctionne pas bien entre 500px et 768px
- **Action**: Ajouter une media query pour gérer ce cas

---

## 🔵 Qualité du Code & Maintenabilité

### 15. CSS minifié dans index.html difficile à maintenir
- **Fichier**: `index.html:30-148`
- **Problème**: CSS sur une seule ligne, difficile à lire et éditer
- **Action**: Reformater le CSS avec indentation propre (comme dans formations.html)

### 16. JavaScript minifié difficile à maintenir
- **Fichiers**: `index.html:329-342`, `projets.html:202-208`
- **Problème**: JS sur quelques lignes, difficile à débugger
- **Action**: Reformater le JavaScript avec indentation propre

### 17. Code modal dupliqué
- **Fichiers**: `index.html`, `projets.html`
- **Problème**: Le HTML de la modale projet et son CSS sont dupliqués
- **Note**: Acceptable pour un site statique, mais à surveiller pour la cohérence

### 18. Données projets dupliquées
- **Fichiers**: `index.html:330`, `projets.html:203`
- **Problème**: L'objet `projects` est défini deux fois avec des données légèrement différentes
- **Action**: S'assurer que les données sont identiques ou créer un fichier JS partagé

---

## ⚪ Optimisations Performance

### 19. Image OG trop lourde
- **Fichier**: `og-image.png`
- **Problème**: 739 KB pour une image de prévisualisation sociale
- **Action**: Compresser l'image (objectif: < 200 KB) avec TinyPNG ou similaire

### 20. Pas de preload pour la police critique
- **Fichiers**: Tous
- **Problème**: Les polices Google Fonts pourraient bloquer le rendu
- **Action**: Optionnel - ajouter `<link rel="preload" as="font">` pour IBM Plex Sans 400

---

## 📋 Contenu à Vérifier

### 21. Lien portfolio externe
- **Fichier**: `index.html:317`
- **URL**: `https://portfolio-aliocha.vercel.app/`
- **Action**: Vérifier que ce lien est toujours valide et à jour

### 22. Cohérence des descriptions projets
- **Fichiers**: `index.html`, `projets.html`
- **Problème**: Les descriptions de projets diffèrent légèrement entre les deux pages
- **Action**: Harmoniser les textes

---

## 📊 Résumé par Priorité

| Priorité | Nombre | Catégorie |
|----------|--------|-----------|
| 🔴 Critique | 3 | Bugs, dates obsolètes |
| 🟠 Important | 5 | Accessibilité |
| 🟡 Moyen | 3 | SEO |
| 🟢 Mineur | 3 | UX/Design |
| 🔵 Technique | 4 | Code quality |
| ⚪ Optionnel | 2 | Performance |
| 📋 Vérif | 2 | Contenu |

**Total: 22 points d'amélioration**

---

## Ordre de Priorité Recommandé

1. **Bugs critiques** (1-3): Dates, copyright, skip-link
2. **Accessibilité** (4-8): WCAG compliance
3. **SEO** (9-11): Meta tags manquants
4. **Navigation mobile** (12): UX critique
5. **Qualité code** (15-18): Maintenabilité
6. **Performance** (19-20): Optimisations
7. **Contenu** (21-22): Vérifications

---

*Document généré le 2026-02-04*
