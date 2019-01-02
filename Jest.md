[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)

***

# Jest | Enzyme

Jest est intégré de base avec les applications générées par Create React App. Si on regarde le fichier  package.json  à la racine du projet, on voit qu’il propose un script  test  dont la commande est  react-scripts test --env=jsdom  , lequel utilise Jest en interne.

Par défaut, Jest cherche dans tous les sous-dossiers (à part  node_modules  et  .git  , notamment) à la recherche de fichiers se terminant par  spec.js  ou  test.js  , précédé d’un trait d’union (  -  ) ou d’un point (  .  ).
Create React App étend les extensions examinées (il ajoute  .mjs  et  .jsx  ), limite la recherche au contenu du dossier  src/  et opte dans ses fichiers générés pour le suffixe  .test.js

Jest fournit de base une fonction  expect()  qui propose toute une série d’assertions (ce qu’ils appellent des matchers), telles que  .toEqual()  ,  .toContain()  ou  .toHaveBeenCalled()  , pour n’en citer que trois.

Jest: Permet de tester des fonctions standards

Enzyme: Permet de tester le rendu des composants react

Pour connaître toutes les assertions disponibles : 
https://jestjs.io/docs/en/expect.html#content

### Assertions jest

**expect(value)**

La fonction expect est utilisée chaque fois que vous souhaitez tester une valeur. Au lieu de cela, vous utiliserez expect avec une fonction "matcher" pour affirmer quelque chose à propos d'une valeur.

```Javascript
  test('the best flavor is grapefruit', () => {
    expect(bestLaCroixFlavor()).toBe('grapefruit');
  });
```

**expect.extend(matchers)**

Vous pouvez utiliser expect.extend pour ajouter vos propres matchers à Jest.

**expect.anything()**

expect.anything () match à tout sauf à null ou indéfini. Vous pouvez l'utiliser dans toEqual ou toBeCalledWith au lieu d'une valeur littérale. Par exemple, si vous voulez vérifier qu'une fonction fictive est appelée avec un argument non nul:

```Javascript
  test('map calls its argument with a non-null argument', () => {
  const mock = jest.fn();
  [1].map(x => mock(x));
  expect(mock).toBeCalledWith(expect.anything());
});
```

**expect.any(constructor)**

expect.any (constructeur) match avec tout ce qui a été créé avec le constructeur donné. Vous pouvez l'utiliser dans toEqual ou toBeCalledWith au lieu d'une valeur littérale. Par exemple, si vous voulez vérifier qu'une fonction fictive est appelée avec un numéro:

```Javascript
function randocall(fn) {
  return fn(Math.floor(Math.random() * 6 + 1));
}

test('randocall calls its callback with a number', () => {
  const mock = jest.fn();
  randocall(mock);
  expect(mock).toBeCalledWith(expect.any(Number));
});
```

**expect.arrayContaining(array)**

expect.arrayContaining (array) match si le tableau reçu contient tous les éléments du tableau attendu. C'est-à-dire que le tableau attendu est un sous-ensemble du tableau reçu.

```Javascript
  describe('arrayContaining', () => {
    const expected = ['Alice', 'Bob'];
    it('matches even if received contains additional elements', () => {
      expect(['Alice', 'Bob', 'Eve']).toEqual(expect.arrayContaining(expected));
    });
    it('does not match if received does not contain expected elements', () => {
      expect(['Bob', 'Eve']).not.toEqual(expect.arrayContaining(expected));
    });
  });
```
**expect.assertions(number)**

expect.assertions (number) vérifie qu'un certain nombre d'assertions sont appelées au cours d'un test. Cela est souvent utile lors du test de code asynchrone, afin de s'assurer que les assertions contenues dans un rappel sont effectivement appelées.

**expect.hasAssertions()**

expect.hasAssertions () vérifie qu'au moins une assertion est appelée lors d'un test.

**expect.not.arrayContainig(array)**

expect.not.arrayContaining (array) match si le tableau reçu ne contient pas tous les éléments du tableau attendu. C'est-à-dire que le tableau attendu n'est pas un sous-ensemble du tableau reçu.

C'est l'inverse de expect.arrayContaining.

**expect.not.objectContaining(object)**

expect.not.objectContaining (object) match si tout l'objet reçu qui ne correspond pas de manière récursive aux propriétés attendues. En d'autres termes, l'objet attendu n'est pas un sous-ensemble de l'objet reçu. 

C'est l'inverse de expect.objectContaining.

**expect.not.stringContaining(string)**

expect.not.stringContaining (string) match si la chaîne reçue ne contient pas la chaîne exacte attendue.

C'est l'inverse de expect.stringContaining.

**expect.not.stringMatching(string | regexp)**

expect.not.stringMatching (string | regexp) match la chaîne reçue si elle ne correspond pas à l'expression rationnelle attendue.

**expect.objectContaining(object)**

expect.not.objectContaining (object) match si tout l'objet reçu correspond de manière récursive aux propriétés attendues. En d'autres termes, l'objet attendu est un sous-ensemble de l'objet reçu. 

**expect.stringContaining(string)**

expect.stringContaining (string) match si la chaîne reçue contient la chaîne exacte attendue.

**expect.stringMatching(string | regexp)**

expect.stringMatching (string | regexp) match si la chaîne reçue correspond à l'expression rationnelle attendue.

### SHALLOW RENDERING
  
  Le shallow rendering est utile pour vous contraindre à tester un composant en tant qu'unité et pour vous assurer que vos tests n'affichent pas indirectement le comportement des composants enfants.
  
  ```Javascript
  import { shallow } from 'enzyme';
  import Foo from './Foo';

  describe('<MyComponent />', () => {
    it('renders three <Foo /> components', () => {
      const wrapper = shallow(<MyComponent />);
      expect(wrapper.find(Foo)).to.have.lengthOf(3);
    });
  });
  ```

On shallow le component pour l'isoler de ses enfants, puis on peut effectuer des fonctions sur ce wrapper.
Exemples : 

**.find(selector)**

La fonction find permet de rechercher tous les noeuds de l'arbre de rendu correspondant au sélecteur fourni.

**.findWhere(predicate)** 

Permet de rechercher tous les nœuds de l’arbre qui renvoie true pour la fonction de prédicat fournie.

**.filter(selector)**

Permet de supprimer les noeuds qui ne correspondent pas au sélecteur dans le wrapper.

**.filterWhere(predicate)**

Permet de supprimer tous les noeuds qui ne renvoient pas la valeur true pour la fonction de prédicat fournie.

**.hostNodes()**

Supprime les noeuds qui ne sont pas des noeuds hôtes.

**.contains(nodeOrNodes)**

Indique si noeud ou un tableau de noeuds se trouve dans l'arbre de rendu.

**.containsMatchingElement(node)**

Indique si un élément react existe ou non dans l'arbre de rendu.

**.containsAllMatchingElements(nodes)**

Retourne si tous les éléments react existent ou non dans l'arbre de rendu.

**.containsAnyMatchingElements(nodes)**

Retourne si l'un des éléments react existe ou non dans l'arbre de rendu.

**.equals(node)**

Indique si l'arborescence de rendu actuelle est égale ou non au nœud donné, en fonction de la valeur attendue.

**matchesElement(node)**

Retourne si un élément react correspond ou non à l'arbre de rendu.

**.hasClass(ClassName)**

Indique si le noeud actuel a ou non le nom de classe donné.

**.is(selector)**

Indique si le noeud actuel correspond ou non à un sélecteur fourni.

**.exists([selector])**

Indique si le nœud actuel existe ou non, ou, si un sélecteur est fourni, si ce sélecteur a des résultats correspondants.

**.isEmptyRender()**

Indique si le composant actuel renvoie ou non une fausse valeur.

**.not(selector)**

Supprime dans le wrapper actuel les nœuds qui correspondent au sélecteur fourni. (inverse de .filter ())

**.children()**

Obtenez un wrapper avec tous les nœuds enfants du wrapper actuel.

**.childAt(index)**

Retourne un nouveau wrapper avec enfant à l'index spécifié.

**.parents()**

Obtenez un wrapper avec tous les parents (ancêtres) du nœud actuel.

**.parent()**

Obtenez un wrapper avec le parent direct du nœud actuel.

**.closest(selector)**

Obtenez un wrapper avec le premier ancêtre du nœud actuel pour qu'il corresponde au sélecteur fourni.

**.shallow([options])**

Shallow rend le nœud actuel et renvoie un wrapper.

**.render()**

Renvoie un CheerioWrapper du sous-arbre du nœud actuel.

**.renderProp(key)()**

Retourne un wrapper du noeud rendu en fonction de la prop de rendu fournie.

**.unmount()**

Une méthode qui démonte le composant.

**.text()** (return String)

Renvoie une représentation sous forme de chaîne des nœuds de texte dans l'arborescence de rendu actuelle.

**.html()**

Renvoie le rendu html static du noeud courant.

**.get(index)**

Retourne le noeud à l'index fourni du wrapper actuel.

**.getElement()**

Retourne l'élement react encapsulé.

**.getElements()

Retourne les éléments react encapsulé

**.at(index)**

Retourne un wrapper du noeud à l'index fourni du wrapper actuel.

**.first()**

Retourne un wrapper du premier noeud du wrapper courant.

**.last()**

Retourne un wrapper du dernier noeud du wrapper courant.

**.state([key])**

Retourne la state du composant racine

**.context()**

Retourne le context du composant racine

**.props()**

Retourne les props du noeud courant

**.prop(key)**

Retourne le nom de la prop du noeud courant.

**.key()** 

Retourne la clé du noeud courrant 

**.simulate(event[, data])**

Simule un évènement sur le noeud courant.

**.setState(nextState)**

Définit manuellement l'état du composant racine.

**.setProps(nextProps[, callback])**

Définit manuellement les props du composant racine.

**.setContext(context)**

Définit manuellement le context du composant racine.

**.instance()**

Retourne l'instance du composant racine.

**.update()**

Appel .forceUpdate() sur l'instance du composant racine.

**.debug()**

Retourne une représentation sous forme de chaîne de l'arbre de rendu  actuel à des fins de débogage.

**type()**

Retourne le type du noeud actuel du wrapper.

**.name()**

Retourne le nom du noeud courant du wrapper.

**.forEach(fn)*

Parcourt chaque noeud du wrapper actuel et exécute la fonction fournie

**.map(fn)**

Mappe le tableau actuel de noeuds vers un autre tableau en réponse à la fonction fournie.

**.reduce(fn[, initialValue])**

Réduit le tableau actuel de nœuds en une valeur, de droite à gauche.



ETC... https://airbnb.io/enzyme/docs/api/shallow.html

### react-addons-test-utils

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

Ne pas utiliser  // Utiliser jest.mock() ou **shallow rendering**

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
