[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

# Test Js

### Assertions

La brique élémentaire de nos tests est une assertion. Il s’agit tout simplement d’un morceau de code qui vérifie qu’une condition est bien remplie, à défaut de quoi elle lève une  AssertionError  adaptée.

Exemple:
```Javascript
it('should use an empty array for its default state', () => {
  const initialState = undefined
  const expectedState = []

  expect(reducer(initialState, {})).to.deep.equal(expectedState)
})
```

### Harnais
Un harnais de test est un programme qui agit en quelque sorte comme le chef d’orchestre de vos tests. Classiquement, il permet de :
- Trouver vos fichiers de tests (suites)
- Fournir une syntaxe de structuration de ces fichiers (  describe()  ,  it()  , etc.)
- Exécuter ces fichiers dans un environnement de test approprié (protection contre les exceptions, timeouts, etc.)
- Fournir un rapport sur les tests ayant réussi ou échoué
- En développement, surveiller vos fichiers de test et codes sources testés, pour relancer les tests appropriés lors d’une modification de fichier.


Certains harnais font davantage, en fournissant par exemple une bibliothèque d’assertions intégrée, en mesurant la couverture de tests, etc.
Il existe de nombreux harnais pour JavaScript, les plus populaires étant Mocha, Jest et Jasmine. Create React App utilise Jest, qui est le plus populaire dans l’univers React, et utilisé par Facebook pour tester React lui-même et tout leur propre code JavaScript.

### Couverture de test

Lorsqu’on commence à avoir des tests, il devient possible de mesurer la couverture de tests, c’est-à-dire le pourcentage de notre code—à l’expression près !–qui est sollicité par les tests. On peut alors repérer les parties non testées, ou insuffisamment testées, et savoir ainsi où concentrer nos prochains efforts d’écriture de tests.

Il existe trois niveaux de test:

Les tests unitaires:

  Permet de tester une unité de code. Principalement une méthode ou function 

Les tests d'intégrations

  Permet de tester le comportement de plusieurs components mais ensemble. Pour savoir s'ils intéragissent bien l'un avec l'autre

Les tests fonctionnels 

  Permet de tester le produit final.

  Navigateur, driver pour piloter de manière automatiser ce navigateur et un langague pour communiquer avec le driver
  
  ex: cypress
