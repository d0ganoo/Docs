[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)

***

# Jest | Enzyme

Jest est intégré de base avec les applications générées par Create React App. Si on regarde le fichier  package.json  à la racine du projet, on voit qu’il propose un script  test  dont la commande est  react-scripts test --env=jsdom  , lequel utilise Jest en interne.

Par défaut, Jest cherche dans tous les sous-dossiers (à part  node_modules  et  .git  , notamment) à la recherche de fichiers se terminant par  spec.js  ou  test.js  , précédé d’un trait d’union (  -  ) ou d’un point (  .  ).
Create React App étend les extensions examinées (il ajoute  .mjs  et  .jsx  ), limite la recherche au contenu du dossier  src/  et opte dans ses fichiers générés pour le suffixe  .test.js

Jest fournit de base une fonction  expect()  qui propose toute une série d’assertions (ce qu’ils appellent des matchers), telles que  .toEqual()  ,  .toContain()  ou  .toHaveBeenCalled()  , pour n’en citer que trois.

Pour connaître toutes les assertions disponibles : 
https://jestjs.io/docs/en/expect.html#content

Jest: Permet de tester des fonctions standards

Enzyme: Permet de tester le rendu des composants react

En plus de Jest, React propose un ensemble de fonctions utiles à la manipulation des composants dans le cadre de tests au travers de l'API react-addons-test-utils.

### Simulate

Permet de simuler un évènement sur un noeud DOM avec des données d'event optionnelles.
Simulate propose une méthode pour chaque événement compris par React.

```Javascript
// Click sur un element

// <button ref={(node) => this.button = node}>...</button>
const node = this.button;
ReactTestUtils.Simulate.click(node);

// Changer la valeur d'un input et taper sur la tuche entrée

// <input ref={(node) => this.textInput = node} />
const node = this.textInput;
node.value = 'giraffe';
ReactTestUtils.Simulate.change(node);
ReactTestUtils.Simulate.keyDown(node, {key: "Enter", keyCode: 13, which: 13});

```
### renderIntoDocument()

Rendre un élément React dans un nœud DOM détaché du document. Cette fonction nécessite un DOM.

### mockComponent ()

Ne pas utiliser  // Utiliser jest.mock() ou shallow rendering

### isElement ()

Retourne true si l'élément est un élément React.

```Javascript
isElement(element)
```

### isElementOfType()

Renvoie true si élément est un élément React dont le type est d'une classe de composants React.

```Javascript
isElementOfType(
  element,
  componentClass
)
```
### isDOMComponent()

Renvoie true si l'instance est un composant DOM (tel qu'un <div> ou un <span>).
  
```Javascript
isDOMComponent(instance)
```

### isCompositeComponent()

Renvoie true si l'instance est un composant défini par l'utilisateur, tel qu'une classe ou une fonction.

### isCompositeComponentWithType()

Renvoie true si l'instance est un composant dont le type est d'une classe de composants React.

```Javascript
isCompositeComponentWithType(
  instance,
  componentClass
)
```

### findAllInRenderedTree()

Parcours tous les composants de l'arborescence et accumule tous les composants pour lesquels test(component) est TRUE.
Ce n'est pas très utile en soi, mais c'est une primitive pour d'autress tests.

```Javascript
findAllInRenderedTree(
  tree,
  test
)
```
### scryRenderedDOMComponentsWithClass()

Trouve tous les éléments DOM des composants de l'arborescence qui ont le nom de classe correspond à className.

```Javascript
scryRenderedDOMComponentsWithClass(
  tree,
  className
)
```
### findRenderedDOMComponentWithClass()

Comme scryRenderedDOMComponentsWithClass () mais attend un seul résultat et renvoie ce résultat ou lève une exception s'il existe un nombre de correspondances différent de celui-ci.

```Javascript
findRenderedDOMComponentWithClass(
  tree,
  className
)
```
### scryRenderedDOMComponentsWithTag()

Trouve tous les éléments DOM des composants de l'arborescence rendue qui sont des composants DOM dont le nom de balise correspond à tagName.

```Javascript
scryRenderedDOMComponentsWithTag(
  tree,
  tagName
)
```
### findRenderedDOMComponentWithTag()

Comme scryRenderedDOMComponentsWithTag () mais attend un seul résultat et renvoie ce résultat ou lève une exception s'il existe un nombre de correspondances différent de celui-ci.

```Javascript
findRenderedDOMComponentWithTag(
  tree,
  tagName
)
```
### scryRenderedComponentsWithType()

Trouve toutes les occurrences de composants dont le type est égal à composantClass.

```Javascript
scryRenderedComponentsWithType(
  tree,
  componentClass
)
```
### findRenderedComponentWithType()

Identique à scryRenderedComponentsWithType () mais s'attend à ce qu'il y ait un résultat et renvoie ce résultat ou lève une exception s'il existe un nombre de correspondances différent de celui-ci.

```Javascript
findRenderedComponentWithType(
  tree,
  componentClass
)
```
