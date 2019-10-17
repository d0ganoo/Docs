## Nightwatch.js

### End-to-end testing

C'est un type de test fonctionnnel qui permet de contrôler le comportement général d'une application sur un support browser.
En complément des tests unitaires pour tester le code.

Nightwatch s'appuie sur l'outil selenium (écrit en java) qui sert à piloter les navigateurs.

Pré-requis : Java et JDK installé sur le système.

#### Installation:

```Javascript
npm i --save nightwatch
```

#### Configuration
Créer un fichier nightwatch.json à la racine du projet et copier la configuration fournit par la documentation de nightwatch.

#### Pour lancer nightwatch: lancer l'éxecutable

```Javascript
/node_modules/.bin/nightwatch
```
