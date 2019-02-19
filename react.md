[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

// Reprendre la doc à partir des cycles de vies

# React

Au départ, React.js a été développé par Facebook pour ses propres besoins : avoir une interface utilisateur (UI) à la fois dynamique et performante. Depuis il a connu une très grande popularité notamment dans de nombreuses start-up. En 2011, Jordan Walke (également créateur de Reason) et son équipe issue de Facebook développent le projet React JS : une bibliothèque JavaScript qui propose une nouvelle façon de générer les pages web (SPA => Single page application), en rendant plus naturelles et plus fluides les interactions utilisateur.

### Les avantages

- DOM (document object model) est un compromis des vus sur les entrées et sorties de données. Le DOM virtuel de React est plus rapide que le modèle de rafraîchissement complet conventionnel, puisque le DOM virtuel ne rafraîchit que certaines parties de la page. Ce qui est intéressant, c’est que l’équipe de Facebook n’était pas consciente qu’une actualisation partielle d’une page se révélerait plus rapide. Facebook cherchait juste un moyen de réduire leur temps de reconstruction, et le rafraîchissement partiel du DOM était juste une bonne solution. Au final, cela augmente les performances et accélère la programmation.

- Prends en charge le server-side rendering (Bien mieux avec Next.js) 

- Vous pouvez réutiliser des composants de code dans React JS, ce qui vous fait gagner beaucoup de temps.

- Il améliore la vitesse de débogage, facilitant ainsi la vie de votre développeur.

- Couplé avec NextJS par exemple, il améliorera le référencement de votre application web.

- Code lisible, concepts utilisé dans d'autre framework comme VUE js

Le JSX
---

Le JSX, une extension de syntaxe de type XML à ECMAScrpit (Signifie Javascript XML) est recommendé pour React. Exemple de JSX :  
```Javascript
const element = <h1>Hello, world!</h1>;
```


Au lieu de séparer les balises (le HTML) et l’algorithmique, React réuni les deux dans des components.

En JSX on peut uttiliser entre accolades toute expression JS valide.  
```Javascript
const name = 'Josh Perez';  
const element = <h1>Hello, {name}</h1>;
```

State et props
---

Le props et la state d'un composant sont des objets javascript. Bien que les influent sur le rendu, leurs fonctionnalités sont différentes en ce qui concerne les composants.
Les props sont transmis au composant de la même manière que des paramètres de fonction, tandis que la state est géré dans le composant dans le composant de la même manière ques les variables déclarées dans une fonction.

Les états sont les attributs privés des components, on ne peut s’en servir que si on déclare le component sous forme d’une classe (ES6) et non pas une fonction. On déclare l’état dans le constructeur de la classe, et on écrit une méthode “render()” pour spécifier ce que le component doit renvoyer (on y écrit la même chose que ce qu’on écrit dans le corps du même component déclaré sous forme de fonction.).

Pour mettre à jour l’état d’un components on utilise la méthode “setState()”. Son appel déclanchera un nouvel appel de “render()”.

Attention : il ne faut pas modifier l’état directement :  
```Javascript
this.state.comment = 'Hello'; // Wrong  
this.setState({comment: 'Hello'}); // Correct
```

“props” et “state” peuvent être mis à jour de façon asynchrone, donc on ne peut pas se baser sur leur valeur pour calculer le nouveau “state”. Une solution : “setState” accepte une fonction en argument, qui prend en paramètre l’ancien state ainsi que le props au moment de l’exécution.

Le flux de données est unidirectionnel : un component parent peut passer des données vers ses enfants, mais pas l’inverse.

**Quel est le but de la fonction de callback en tant qu'argument de setState ()?**

La fonction de rappel est appelée lorsque setState est terminé et que le composant est rendu. Comme setState () est asynchrone, la fonction de rappel est utilisée pour toute action ultérieure.

Remarque: Il est recommandé d'utiliser la méthode de cycle de vie plutôt que cette fonction de rappel.

```Javascript
setState({ name: 'John' }, () => console.log('The name has updated and component re-rendered'))
```

Les éléments
---

Les éléments sont les atomes des applis React. Ils décrivent ce qu’on veut voir sur l’écran et sont immutables.

React ne change que ce qui est nécessaire, si on veut remplacer un élément par un autre, il va comparer les deux. Seule la différence sera modifiée dans le DOM, au lieu de réécrire tout le nouvel élément.

```Javascript
const element = React.createElement(
  'div',
  {id: 'login-btn'},
  'Login'
)

// Cette fonction React.createElement() retourne un objet:

{
  type: 'div',
  props: {
    children: 'Login',
    id: 'login-btn'
  }
}

// Le rendu :

<div id='login-btn'>Login</div>

```

Les components
---

Les components sont des fonctions JS qui acceptent un seul paramètre (les “props”) et qui renvoie du JSX.  
```Javascript
function Welcome(props) {  
  return <h1>Hello, {props.name}</h1>;  
}
```

On peut afficher le rendu d’un component avec JSX.  
```Javascript

function Welcome(props) {  
  return <h1>Hello, {props.name}</h1>;  
}

const element = <Welcome name="Sara" />;  

ReactDOM.render(  
  element,  
  document.getElementById('root')  
);

// D'autres façons de déclarer un component

const element1 = () => <h1>Hello world</h1>;

class element2 extends React.Component{
  constructor(props){
    super(props);
  }
  render(){
    return <h1>Hello World</h1>
  }
}

```

Attention : il faut nommer les components avec une majuscule, car React traite les balises en minuscule comme des balises HTML classiques.
On peut appeler des components dans d’autre components.
Règle de base en React : les props doivent être read-only.

**1- Comment faire pour savoir s'il faut utiliser un component de class ou de function ?**

Si le composant nécessite un state ou un cycle de vie, utilisez le class component sinon utilisez un function component.

**2- Qu'est-ce qu'un composant pur ?**

React.PureComponent est exactement le même que React.Component, à la différence qu'il gère pour vous la méthode shouldComponentUpdate().
Lorsque les props ou la state changent, le PureComponent effectue une comparaison entre les props et la state.
Un PureComponent se re-render uniquement si l’une de ses props a changée.

Les events
---

Les events en React sont écrit en camelCase.

```Javascript
<button onClick={activateLasers}>
```

**Comment bind les méthodes ou les gestionnaires d’événements dans des callbacks JSX?**

Pour bind, il y a plusieurs façon de faire:

1- Bind dans le constructor

```Javascript
class Component extends React.Componenet {
  constructor(props) {
    super(props)
    this.handleClick = this.handleClick.bind(this)
  }

  handleClick() {
    // ...
  }
  
  render(){
    return (
      <button onClick={this.handleClick}>
          Click me
      </button>
    )
  }
}
```
2- Bind les methodes des class grâce à l'arrow function

```Javascript
class Component extends React.Componenet {
  constructor(props) {
    super(props)
  }

  handleClick = () => {
    console.log('this is:', this)
  }
  
  render(){
    return (
      <button onClick={this.handleClick}>
          Click me
      </button>
    )
  }
}
```
3- Utiliser l'opérateur de bind :: ES7

```Javascript
class Component extends React.Componenet {
  constructor(props) {
    super(props)
  }

  handleClick(){
    console.log('this is:', this)
  }
  
  render(){
    return (
      <button onClick={::this.handleClick}>
          Click me
      </button>
    )
  }
}
```

4- Arrow function directement dans le callback

```Javascript
class Component extends React.Componenet {
  constructor(props) {
    super(props)
  }

  handleClick(event){
    console.log('this is:', this)
  }
  
  render(){
    return (
     <button onClick={(event) => this.handleClick(event)}>
        Click me
     </button>
    )
  }
}
```
Remarque: Si le rappel est transmis en tant que prop aux composants enfants, ceux-ci peuvent effectuer un nouveau rendu. Dans ces cas, il est préférable d’utiliser l’approche syntaxique .bind () ou des champs de classe publics en tenant compte des performances.


5- Bind directement dans la fonction de callback

```Javascript
class Component extends React.Componenet {
  constructor(props) {
    super(props)
  }

  handleClick(id){
    console.log('this is:', this)
  }
  
  render(){
    return (
     <button onClick={this.handleClick.bind(this, id)} >
        Click me
     </button>
    )
  }
}
```

HOC - Higher-Order components
---

Un HOC est une fonction qui prend un composant en paramètre et retourne un nouveau composant. Il permet de pouvoir réutiliser la même logique pour plusieurs components. On dit que c'est des fonctions purs car elles n'ont pas de side effect. Ils ne modifieront ni ne copieront le comportement du composant d'entré.

**HOC peut être  réutilisé dans plusieurs cas:**

- Réutiliser du code, de la logique
- Render hijacking : capacité de contrôler ce qu'un composant produira à partir d'un autre composant. Envelopper votre composant dans un composant d'ordre supérieur qui permettra de surcharger en lui injectant de nouvelle props.
- Abstraction et manipulation de la state.
- Manipulation des props

**Comment créer un proxy pour le composant HOC?**

Vous pouvez ajouter / modifier les props transmis au composant à l'aide du modèle proxy props, comme suit:

```Javascript
function HOC(WrappedComponent) {
  return class Test extends Component {
    render() {
      const newProps = {
        title: 'New Header',
        footer: false,
        showFeatureX: false,
        showFeatureY: true
      }

      return <WrappedComponent {...this.props} {...newProps} />
    }
  }
}
```

Les hooks
---

https://www.masterreact.io/articles/2019-02-13-premiers-pas-avec-les-hooks/

Cycle de vie
---

Quand un component écrit dans le DOM pour la première fois, on dit qu’il “mount”, quand ce qu’il écrit dans le DOM disparaît, il “unmount”. On peut écrire des méthodes spéciales appelées lors de ces deux évenement, respectivement “componentDidMount
” et “componentWillUnmount”. Ces méthodes s’appellent des “lifetime hooks”.

**Les différentes phases du cycle de vie d'un composant?**

Il existe 4 phases:

1. **Initialisation:** A cette étape, le composant prépare la configuration de la state initial et des props par défault.
2. **Mounting:** Le composant est prêt à être mount dans le DOM du navgateur. ComponentWillMount() et componentDidMount().
3. **Updating:** Envoie des nouvelles props et mise à jour la state    
4. **Unmounting:** Le composant est démonté du DOM.

![lifecycle](https://github.com/sudheerj/reactjs-interview-questions/blob/master/images/phases.png)

* **componentWillMount():** Exécuté avant le rendu
* **componentDidMount():** Exécuté après le premier rendu. Les requêtes ajax doivent avoir lieu ici
* **componentWillReceiveProps():** Exécuté quand une prop est mise à jour pour déclencher la transition de state
* **shouldComponentUpdate:** Détermine si le composant sera mis à jour ou non. Par défault, il retourne TRUE. Si vous êtes certain que le composant n'a pas besoin d'être rendu, vous pouvez retourné FALSE.
C'est la fonction idéale pour améliorer les performances (Eviter des rendus inutiles)
* **componentWillUpdate:** Exécuté avant de re-render le composant une fois que shouldComponentUpdate renvoie TRUE
* **componentDidUpdate:** Il est principalement utilisé pour mettre à jour le DOM en réponse à un changement de props ou de la state.
* **componentWillUnmount:** Il sera utilisé pour annuler tout requête reseau sortante ou pour supprimer tous les écouteurs d'évènements associés au composant.

Les refs 
---

La ref est utilisée pour renvoyer une référence à l'élément. Ils doivent être évités dans la plupart des cas. Toutefois, ils peuvent être utiles lorsque vous avez besoin d'un accès direct à l'élément DOM ou à une instance d'un composant.

**Créer une référence :**

```Javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props)
    this.myRef = React.createRef()
  }
  render() {
    return <div ref={this.myRef} />
  }
}
```
**Les forward refs**

Les forward refs permettent à certains composants de prendre une référence qu’ils reçoivent et de la transmettre à un enfant.

```Javascript
const ButtonElement = React.forwardRef((props, ref) => (
  <button ref={ref} className="CustomButton">
    {props.children}
  </button>
));

// Create ref to the DOM button:
const ref = React.createRef();
<ButtonElement ref={ref}>{'Forward Ref'}</ButtonElement>
```

Error Bundaries
---

Le concept du composant Error boundaries est de permettre d'intercepter les erreurs des composants qu'ils encapuslent.
L'idée étant de pouvoir continuer d'utiliser l'application là où les composants fonctionnent encore, tout en informant l'utilisateur qu'il y a un problème sur l'un ou certains d'entre eux.

``` Javascript

<ErrorBoundary>
 <MyInput
 name="email"
 validations="isEmail"
 label="Adresse E-Mail"
 placeholder="E-Mail"
 validationError="Adresse E-Mail non valide"
 required
 error={true}
 />
</ErrorBoundary>

<ErrorBoundary>
 <MyInput
 name="password"
 label="Mot de passe"
 placeholder="Mot de passe"
 validationError="Field empty"
 required
 type="password"
 error={false}
 />
</ErrorBoundary>

```
(Une erreur est attendue dans le cas du premier input)
Le premier ne fonctionnera pas et affichera un message d'erreur à l'utilisateur tandis que le deuxième fonctionnera et s'affichera parfaitement.

PropTypes
---

PropTypes exporte des validateurs pouvant être utilisés pour vérifier que les données reçues sont valides. Dans cet exemple, nous utilisons PropTypes.string. Lorsqu'une valeur non valide est fournie pour un component, un avertissement apparaît dans la console JavaScript. 
Cette vérification du typage est effectuée au runtime.
Pour des raisons de performances, propTypes est uniquement vérifié en mode développement.

``` Javascript
import PropTypes from 'prop-types';

class Greeting extends React.Component {
  render() {
    return (
      <h1>Hello, {this.props.name}</h1>
    );
  }
}

Greeting.propTypes = {
  name: PropTypes.string
};

```

