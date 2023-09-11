<div align="center">
  <h3 align="center">
	<big>Publicodes Package Template</big>
  </h3>
  <p align="center">
   <a href="https://github.com/incubateur-ademe/publicodes-model-template/issues">Report Bug</a>
   •
   <a href="https://incubateur-ademe.github.io/publicodes-model-template/">API docs</a>
   •
   <a href="https://github.com/incubateur-ademe/publicodes-model-template/blob/master/CONTRIBUTING.md">Contribute</a>
   •
   <a href="https://publi.codes">Publicodes</a>
  </p>

Template dépôt GitHub pour créer un paquet Publicodes.

</div>

## Fonctionnalités

- 📦 compilation des règles publicodes en un seul fichier JSON grâce à
[`@incubateur-ademe/publicodes-tools`](https://github.com/incubateur-ademe/publicodes-tools)
- 📖 documentation du modèle interactive disponible sur GitHub Pages grâce à
[`@publicodes/react-ui`](https://publi.codes/docs/api/react-ui)
- 🚀 API REST pour utiliser le modèle dans une application grâce à
[`@publicodes/api`](https://publi.codes/docs/api/api-rest)

## Initialisation

Pour utiliser ce template, il suffit de cliquer sur le bouton `Use this
template`. Puis de remplacer les variables suivantes dans tous les fichiers du
projet :

- `%PACKAGE_NAME%` : nom du paquet npm / nom du repository GitHub
- `%GITHUB_USER%` : nom d'utilisateur GitHub / organisation GitHub

Pour utiliser les fonctionnalités de la CI, il faut ajouter les variables
suivantes dans les secrets du repository GitHub :

- `NPM_TOKEN` : token NPM pour publier le paquet sur [npmjs.com](https://npmjs.com)
- `PAT` : Personal Access Token pour publier la documentation sur GitHub Pages

Pour deployer la documentation sur GitHub Pages, il faut sélectionner la
branche `gh-pages` dans les paramètres du repository.

## Example de dépôts utilisant ce template

- [`@incubateur-ademe/modele-numerique`](https://github.com/incubateur-ademe/modele-numerique) -
_Modèle Publicodes pour calculer l'impact (en CO2eq) du numérique_

## Usage 

Ajouter le paquet à vos dépendandes : 
```
yarn add %PACKAGE_NAME
```

Instancier une nouveau moteur Publicode :
```typescript
import Engine from 'publicodes'
import rules from '%PACKAGE_NAME%'

const engine = new Engine(rules)

engine.evaluate('tablette . consommation en mode actif')
```

Utiliser certaines règles dans un autre modèle publicodes :
```yaml
importer!:
  depuis:
    nom: %PACKAGE_NAME% 
    url: https://github.com/incubateur-ademe/modele-numerique
  dans: modèle numérique
  les règles:
    - numérique . internet . consommation horaire 
    - ordinateur portable . construction
```

### En local

#### Compiler le modèle

> Les règles publicodes du modèle sont disponible dans le workspace
> [`rules/`](https://github.com/%GITHUB_USER%/%PACKAGE_NAME%/tree/main/rules).

Pour installer les dépendences et compiler tous les fichiers `.publicodes` en
un seul fichier JSON, il suffit d'exécuter la commande suivante : 

```
yarn && yarn run build
```

#### Lancer la documentation

> Le code de la documentation est disponible dans le workspace
> [`doc/`](https://github.com/%GITHUB_USER%/%PACKAGE_NAME%/tree/main/doc).

Pour lancer l'app React en local permettant de parcourir la documentation du
modèle, il suffit d'exécuter la commande suivante :

```
yarn install --cwd doc

yarn run doc
```

#### Lancer l'API

> Le code de l'API est disponible dans le workspace
> [`api/`](https://github.com/%GITHUB_USER%/%PACKAGE_NAME%/tree/main/api).

Pour lancer le serveur Node permettant d'utiliser l'API REST, il faut utiliser les commandes
suivantes : 

```
yarn run api

# En watch-mode
yarn run api:watch
```

## Publier une nouvelle version

Afin de publier une nouvelle version il suffit d'exécuter la commande `npm
version`.
