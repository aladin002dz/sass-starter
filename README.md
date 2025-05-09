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

## Structure du Projet

```
sass-starter/
├── css/          # Fichiers CSS compilés
├── sass/         # Fichiers source SASS
├── index.html    # Page principale
└── style.scss    # Fichier SASS principal
```

## Développement

Pour compiler les fichiers SASS en CSS :

```bash
npm run dev
```

Pour compiler les fichiers SASS en CSS compressé :

```bash
npm run build
```

## Fonctionnalités

- Compilation SASS vers CSS
- Structure de projet organisée
- Support pour les variables SASS
- Mixins et fonctions SASS

## Contribution

1. Fork le projet
2. Créez votre branche de fonctionnalité (`git checkout -b feature/AmazingFeature`)
3. Committez vos changements (`git commit -m 'Add some AmazingFeature'`)
4. Push vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une Pull Request

## Licence

Ce projet est sous licence MIT.
