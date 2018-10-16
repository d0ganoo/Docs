[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)

***

# Jest

Jest est intégré de base avec les applications générées par Create React App. Si on regarde le fichier  package.json  à la racine du projet, on voit qu’il propose un script  test  dont la commande est  react-scripts test --env=jsdom  , lequel utilise Jest en interne.

Par défaut, Jest cherche dans tous les sous-dossiers (à part  node_modules  et  .git  , notamment) à la recherche de fichiers se terminant par  spec.js  ou  test.js  , précédé d’un trait d’union (  -  ) ou d’un point (  .  ).
Create React App étend les extensions examinées (il ajoute  .mjs  et  .jsx  ), limite la recherche au contenu du dossier  src/  et opte dans ses fichiers générés pour le suffixe  .test.js

Jest fournit de base une fonction  expect()  qui propose toute une série d’assertions (ce qu’ils appellent des matchers), telles que  .toEqual()  ,  .toContain()  ou  .toHaveBeenCalled()  , pour n’en citer que trois.

Pour connaître toutes les assertions disponibles : 
https://jestjs.io/docs/en/expect.html#content
