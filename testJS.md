[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

# Test Js

### Couverture de test

Lorsqu’on commence à avoir des tests, il devient possible de mesurer la couverture de tests, c’est-à-dire le pourcentage de notre code—à l’expression près !–qui est sollicité par les tests. On peut alors repérer les parties non testées, ou insuffisamment testées, et savoir ainsi où concentrer nos prochains efforts d’écriture de tests.

Il existe **TROIS** niveaux de test:

* **Les tests unitaires:**

  Permet de tester une unité de code. Principalement une méthode ou function 

* **Les tests d'intégrations**

  Permet de tester le comportement de plusieurs components mais ensemble. Pour savoir s'ils intéragissent bien l'un avec l'autre.
  Intéraction avec la base de données

* **Les tests fonctionnels**

  Permet de tester le produit final.

  Navigateur, driver pour piloter de manière automatiser ce navigateur et un langague pour communiquer avec le driver
  
  ex: cypress

### Règles tests unitaires

* Un test unitaire doit être véritablement unitaire. La classe testée doit l’être en isolation complète, afin de ne tester qu’une classe (et une méthode) à la fois, le SUT (System Under Test).
* Si une classe est difficile à tester, il est temps de faire du refactoring. Est-elle trop volumineuse ? Présente-t-elle trop de dépendances ? Profitez de l’occasion pour la découper et déplacer du code dans des classes annexes.
* Un test unitaire doit s’exécuter le plus rapidement possible afin d’avoir un retour quasi immédiat. Il faut donc proscrire l’accès à des fichiers, des bases de données ou des services externes dans un test unitaire. Un test qui dialogue avec une base de données n’est pas un test unitaire, c’est un test d’intégration.
* Le code d’un test unitaire fait partie du code applicatif. Il doit donc, à l’image du reste de l’application, respecter des conventions de code. Chouchoutez vos tests unitaires, faites du refactoring sur leur code, respectez les bonnes pratiques, présentez le code à vos collègues, codez les tests en pair programming, sans quoi on trouvera certainement dans votre application des tests smells, des tests unitaires peu lisibles et difficilement maintenables. De bons tests unitaires doivent permettre à leur lecture de comprendre le comportement du SUT.
* Isolez les dépendances de la classe testée grâce à l’injection de dépendances.
* Ne testez qu’un comportement à la fois. Soyez raisonnable et gardez le test simple, lisible et concentré sur ce comportement.
* Pensez à utiliser un framework de mocks pour injecter les dépendances sous forme de bouchons. Ces outils permettent de respecter le commandement n°1. Ne bannissez pas pour autant les bouchons codés à la main ; ils peuvent parfois rendre le test unitaire plus simple et plus lisible qu’avec un mock provenant d’un framework.
* Identifiez précisément les étapes setup, exercise, verify, teardown dans votre code. On retrouve ces quatre étapes dans tout test unitaire.
* Ne vous concentrez pas sur une couverture de code à 100%. Ce n’est qu’un indicateur technique, qui doit être examiné dans le contexte de l’application, et qui ne prouve en rien la qualité du code et des tests unitaires.
* Ne développez pas vos tests unitaires « plus tard ». Si vous n’utilisez pas l’approche TDD, développez-les le plus tôt possible.

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

