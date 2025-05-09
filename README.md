# Projet SASS Starter

## Prérequis

Avant de commencer, assurez-vous d'avoir installé :

- Node.js (version LTS recommandée)
- npm (généralement installé avec Node.js)

**Vérifier l'installation de Node.js et npm**

```bash
node --version
npm --version
```

### Solution 1 (recommendée) : Créer un nouveau projet avec npm :

```bash
npm init -y
npm install -D sass
```

### Ajouter un script dans le fichier package.json :

```json
"scripts": {
  "dev": "sass --watch sass/style.scss:css/style.css",
  "build": "sass sass/style.scss:css/style.css --style=compressed"
}
```

## Structure du Projet

```
sass-starter/
├── css/          # Fichiers CSS compilés
├── sass/         # Fichiers source SASS
└── index.html    # Page principale
```

## Développement

Pour compiler les fichiers SASS en CSS, ouvrir le terminal et lancer la commande :

```bash
npm run dev
```

### arrêter le serveur se fait avec `ctrl + c`

Pour compiler les fichiers SASS en CSS compressé :

```bash
npm run build
```

### Pour initialiser Git

Créer un fichier `.gitignore` pour ignorer le dossier `node_modules`

```bash
git init
git add .
git commit -m "Initial commit"
```

## Solution 2 : Cloner le projet

forker le repo sur GitHub, ensuite cloner la version forkée en local

```bash
git clone [URL_DU_REPO]
   cd sass-starter
```

3. **Installer les dépendances**
   ```bash
   npm install
   ```

# Les Fonctionnalités Clés de Sass

Sass (Syntactically Awesome Style Sheets) est un préprocesseur CSS qui offre de nombreuses fonctionnalités pour rendre le code CSS plus puissant et maintenable. Voici quelques exemples pratiques des fonctionnalités clés:

## 1. Variables

Les variables permettent de stocker des valeurs réutilisables comme des couleurs, tailles de police, ou espacements.

```scss
// Définition de variables
$primary-color: #3498db;
$secondary-color: #2ecc71;
$base-padding: 15px;
$font-stack: "Roboto", sans-serif;

.button {
  background-color: $primary-color;
  padding: $base-padding;
  font-family: $font-stack;
}

.alert {
  border: 1px solid $secondary-color;
  padding: $base-padding;
}
```

## 2. Imbrication (Nesting)

L'imbrication permet d'organiser le code CSS de manière hiérarchique, similaire à la structure HTML.

```scss
nav {
  background-color: #333;

  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li {
    display: inline-block;

    a {
      color: white;
      padding: 10px 15px;

      &:hover {
        text-decoration: underline;
      }
    }
  }
}
```

## 3. Importation de fichiers partiels

L'organisation modulaire du code avec des fichiers partiels.

```scss
@use "./reset";
@use "./composants/footer";
```

les fichiers partiels doivent commencer par un underscore "\_"

## 4. Media Queries imbriquées

Sass permet d'imbriquer les media queries directement dans les sélecteurs.

```scss
.navbar {
  display: flex;
  width: 100%;

  @media (min-width: 768px) {
    flex-direction: column;
  }

  .logo {
    margin-right: 20px;

    @media (min-width: 768px) {
      margin: 0 0 10px 0;
    }
  }
}
```

## 5. Mixins

Les mixins sont des blocs de code réutilisables, semblables à des fonctions.

```scss
// Définition d'un mixin
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

// Mixin avec paramètres
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  border-radius: $radius;
}

.card {
  @include flex-center;
  @include border-radius(5px);
  background-color: #fff;
}

.button {
  @include border-radius(3px);
  padding: 10px 15px;
}
```

## 6. Extend/Inheritance

La directive `@extend` permet d'hériter des styles d'un sélecteur à un autre.

```scss
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}

.warning {
  @extend %message-shared;
  border-color: yellow;
}
```

## 7. Opérations mathématiques

Sass permet d'effectuer des calculs directement dans les styles.

```scss
$base-size: 16px;
$padding: 20px;

.container {
  width: 100% - 20%;
  font-size: $base-size * 1.2;
  padding: $padding / 2;
  margin-bottom: $padding * 2;
}
```

## 8. Fonctions

Sass offre de nombreuses fonctions intégrées et permet d'en créer des personnalisées.

```scss
// Fonction personnalisée
@function calculateWidth($n) {
  @return $n * 60px + ($n - 1) * 20px;
}

// Utilisation de fonctions intégrées
.box {
  width: calculateWidth(3);
  background-color: lighten(#3498db, 20%);
  color: darken(#3498db, 30%);
  opacity: rgba(#3498db, 0.8);
}
```

## 9. Conditionnels

Les directives conditionnelles permettent d'appliquer différents styles selon certaines conditions.

```scss
$theme: "dark";

.component {
  @if $theme == "dark" {
    background-color: #333;
    color: white;
  } @else {
    background-color: white;
    color: #333;
  }
}

@mixin text-color($size) {
  @if $size > 20px {
    color: red;
  } @else if $size > 15px {
    color: blue;
  } @else {
    color: green;
  }
}

.text {
  @include text-color(18px);
}
```

## 10. Boucles

Sass offre plusieurs types de boucles pour générer du CSS répétitif.

```scss
// Boucle for
@for $i from 1 through 5 {
  .col-#{$i} {
    width: 20% * $i;
  }
}

// Boucle each
$social-colors: (
  "facebook": #3b5998,
  "twitter": #1da1f2,
  "instagram": #e1306c,
);

@each $platform, $color in $social-colors {
  .btn-#{$platform} {
    background-color: $color;
    border: 1px solid darken($color, 10%);
  }
}

// Boucle while
$i: 1;
@while $i <= 5 {
  .margin-#{$i} {
    margin: 5px * $i;
  }
  $i: $i + 1;
}
```

Ces exemples illustrent comment Sass peut simplifier et améliorer considérablement votre workflow CSS, en rendant votre code plus modulaire, maintenable et DRY (Don't Repeat Yourself).

## Contribution

1. Fork le projet
2. Créez votre branche de fonctionnalité (`git checkout -b feature/AmazingFeature`)
3. Committez vos changements (`git commit -m 'Add some AmazingFeature'`)
4. Push vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une Pull Request

## Licence

Ce projet est sous licence MIT.
