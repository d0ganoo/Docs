[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

# React

Au départ, React.js a été développé par Facebook pour ses propres besoins : avoir une interface utilisateur (UI) à la fois dynamique et performante. Depuis il a connu une très grande popularité notamment dans de nombreuses start-up. En 2011, Jordan Walke (également créateur de Reason) et son équipe issue de Facebook développent le projet React JS : une bibliothèque JavaScript qui propose une nouvelle façon de générer les pages web, en rendant plus naturelles et plus fluides les interactions utilisateur.

### Les avantages

- DOM (document object model) est un compromis des vus sur les entrées et sorties de données. Le DOM virtuel de React est plus rapide que le modèle de rafraîchissement complet conventionnel, puisque le DOM virtuel ne rafraîchit que certaines parties de la page. Ce qui est intéressant, c’est que l’équipe de Facebook n’était pas consciente qu’une actualisation partielle d’une page se révélerait plus rapide. Facebook cherchait juste un moyen de réduire leur temps de reconstruction, et le rafraîchissement partiel du DOM était juste une bonne solution. Au final, cela augmente les performances et accélère la programmation.

- Vous pouvez réutiliser des composants de code dans React JS, ce qui vous fait gagner beaucoup de temps.

- Il améliore la vitesse de débogage, facilitant ainsi la vie de votre développeur.

- Couplé avec NextJS par exemple, il améliorera le référencement de votre application web.

- Code lisible, concepts utilisé dans d'autre framework comme VUE js

Le JSX
---

JSX (une extension syntaxique de JS) est recommendé pour React. Exemple de JSX :  
```Javascript
const element = <h1>Hello, world!</h1>;
```


Au lieu de séparer les balises (le HTML) et l’algorithmique, React réuni les deux dans des components.

En JSX on peut uttiliser entre accolades toute expression JS valide.  
```Javascript
const name = 'Josh Perez';  
const element = <h1>Hello, {name}</h1>;
```

Les éléments
---

Les éléments sont les atomes des applis React. Ils décrivent ce qu’on veut voir sur l’écran et sont immutables.

React ne change que ce qui est nécessaire, si on veut remplacer un élément par un autre, il va comparer les deux. Seule la différence sera modifiée dans le DOM, au lieu de réécrire tout le nouvel élément.

Les components
---

Les components sont des fonctions JS qui acceptent un seul paramètre (les “props”) et qui renvoie un élément React.  
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
```

Attention : il faut nommer les components avec une majuscule, car React traite les balises en minuscule comme des balises HTML classiques.
On peut appeler des components dans d’autre components.
Règle de base en React : les props doivent être read-only.

Les états et le cycle de vie
---

Les états sont les attributs privés d’un components, on ne peut s’en servir que si on déclare le component sous forme d’une classe (ES6) et non pas une fonction. On déclare l’état dans le constructeur de la classe, et on écrit une méthode “render()” pour spécifier ce que le component doit renvoyer (on y écrit la même chose que ce qu’on écrit dans le corps du même component déclaré sous forme de fonction.).

Quand un component écrit dans le DOM pour la première fois, on dit qu’il “mount”, quand ce qu’il écrit dans le DOM disparaît, il “unmount”. On peut écrire des méthodes spéciales appelées lors de ces deux évenement, respectivement “componentDidMount
” et “componentWillUnmount”. Ces méthodes s’appellent des “lifetime hooks”.

Pour mettre à jour l’état d’un components on utilise la méthode “setState()”. Son appel déclanchera un nouvel appel de “render()”.

Attention : il ne faut pas modifier l’état directement :  
```Javascript
this.state.comment = 'Hello'; // Wrong  
this.setState({comment: 'Hello'}); // Correct
```


“props” et “state” peuvent être mis à jour de façon asynchrone, donc on ne peut pas se baser sur leur valeur pour calculer le nouveau “state”. Une solution : “setState” accepte une fonction en argument, qui prend en paramètre l’ancien state ainsi que le props au moment de l’exécution.

Le flux de données est unidirectionnel : un component parent peut passer des données vers ses enfants, mais pas l’inverse.

Ref
---



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

