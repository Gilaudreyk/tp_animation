# Motion — Landing page animée

Landing page moderne intégrant HTML sémantique, CSS (Flexbox/Grid/animations) et animations JavaScript via IntersectionObserver et requestAnimationFrame.

## ■ Démo

[Voir la démo en ligne](https://Gilaudreyk.github.io/tp_animation)

## ■ Description du projet

Ce projet est une landing page pour une application fictive appelée **Motion**. Il démontre les meilleures pratiques en front-end :

- Structure HTML5 sémantique
- Design moderne et responsive (Flexbox + CSS Grid)
- Animations CSS fluides (transitions, @keyframes)
- Animations JavaScript dynamiques (scroll, compteur)
- Workflow Git professionnel avec branches par section
- Accessibilité (prefers-reduced-motion, sémantique)

## ■ Stack technique

- **HTML5** : structure sémantique
- **CSS3** : variables, Flexbox, Grid, @keyframes, prefers-reduced-motion
- **JavaScript Vanilla** : IntersectionObserver, requestAnimationFrame, smooth scroll
- **Git** : feature branching workflow

## ■ Structure du projet

```
tp_animation/
├── index.html          # Page principale
├── css/
│   └── style.css       # Styles globaux + animations
├── js/
│   └── main.js         # Animations JS
├── README.md           # Ce fichier
└── .gitignore          # Fichiers à ignorer
```

## ■ Workflow Git

Le projet suit un workflow professionnel avec une branche par section :

1. **main** : branche principale (fusionnée et testée)
2. **feature/structure-html** : structure HTML sémantique
3. **feature/styles-globaux** : variables CSS et styles globaux
4. **feature/layout-responsive** : mise en page responsive (Flexbox/Grid)
5. **feature/animations-css** : animations CSS
6. **feature/animations-js** : animations JavaScript
7. **feature/finalisation** : README et déploiement

Chaque branche est créée à partir de `main`, développée indépendamment, puis fusionnée.

## ■ Installation locale

### Prérequis
- Git installé
- Un navigateur moderne
- Un éditeur de code (VS Code recommandé)

### Étapes

```bash
# Cloner le dépôt
git clone https://github.com/Gilaudreyk/tp_animation.git
cd tp_animation

# Ouvrir dans VS Code
code .

# Pour visualiser le projet : ouvrir index.html dans votre navigateur
# Ou utiliser une extension comme "Live Server" dans VS Code
```

## ■ Fonctionnalités principales

### 1. Navigation avec effet de soulignement
- Lien de navigation avec barre de soulignement animée
- Transition fluide au survol

### 2. Section Hero
- Titre et sous-titre avec animation fadeInUp
- Bouton avec animation de pulsation
- Gradient d'arrière-plan moderne

### 3. Section Stats (Compteur animé)
- 3 statistiques avec compteur animé
- Utilise `requestAnimationFrame` pour la fluidité
- Se déclenche à l'entrée en viewport
- Easing ease-out cubique

### 4. Section Fonctionnalités
- Grille responsive avec CSS Grid
- Cartes avec animation au scroll (IntersectionObserver)
- Effet de levée au survol

### 5. Smooth Scroll
- Navigation fluide vers les sections (ancres)
- Comportement `behavior: smooth`

### 6. Accessibilité
- Respect de `prefers-reduced-motion` pour utilisateurs sensibles aux animations
- Structure HTML sémantique
- Contrastes de couleurs suffisants

## ■ Points clés du code

### Variables CSS (design tokens)
```css
:root {
  --color-primary: #FF6B35;
  --color-dark: #0A2540;
  --color-light: #F5F7FA;
  --transition-base: 0.3s ease;
  /* ... */
}
```

### Grid responsive (without media queries)
```css
.features__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--space-md);
}
```

### IntersectionObserver pour animations au scroll
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add("is-visible");
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.15 });
```

### Compteur animé avec requestAnimationFrame
```javascript
function animateCounter(el, target, duration = 1500) {
  const startTime = performance.now();
  
  function update(now) {
    const progress = Math.min((now - startTime) / duration, 1);
    const eased = 1 - Math.pow(1 - progress, 3); // ease-out cubique
    const value = Math.floor(target * eased);
    el.textContent = value.toLocaleString("fr-FR");
    
    if (progress < 1) requestAnimationFrame(update);
  }
  
  requestAnimationFrame(update);
}
```

## ■ Commits atomiques

Le projet suit la convention des commits conventionnels :

- `feat:` nouvelle fonctionnalité
- `fix:` correction de bug
- `style:` mise en forme
- `docs:` documentation
- `chore:` tâche technique

## ■ Critères d'évaluation

| Critère | Points | Détail |
|---------|--------|--------|
| Structure HTML sémantique | 3 | Balises adaptées, hiérarchie claire |
| CSS (variables, layout) | 4 | Flexbox + Grid, responsive |
| Animations CSS | 3 | Transitions fluides, @keyframes |
| Animations JS | 4 | IntersectionObserver, compteur |
| Workflow Git | 4 | 6 branches, commits atomiques |
| README & déploiement | 2 | README complet, site accessible |
| **TOTAL** | **20** | |

## ■ Pour aller plus loin

- **Dark mode** : toggle thème clair/sombre avec variables CSS
- **Parallaxe** : effect de profondeur au scroll
- **Formulaire** : validation JavaScript en temps réel
- **Menu mobile** : burger menu animé
- **SEO** : meta tags, sitemap

## ■ Auteur

TP pédagogique - Développement Front-End - MyDigitalSchool - Learni

## ■ Licence

Ce projet est à usage pédagogique. Libre de le modifier et partager.

---

**Création**: Avril 2026  
**Dernière mise à jour**: Avril 2026
