[JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [Git](https://github.com/d0ganoo/Docs/blob/master/git.md)  

* * * 

# React
Le JSX
---

JSX (une extension syntaxique de JS) est recommendé pour React. Exemple de JSX :  
```Javascript
const element = &lt;h1&gt;Hello, world!&lt;/h1&gt;;
```


Au lieu de séparer les balises (le HTML) et l’algorithmique, React réuni les deux dans des components.

En JSX on peut uttiliser entre accolades toute expression JS valide.  
```Javascript
const name = 'Josh Perez';  
const element = &lt;h1&gt;Hello, {name}&lt;/h1&gt;;
```

Babel transforme le JSX en expression React.

Les éléments
---

Les éléments sont les atomes des applis React. Ils décrivent ce qu’on veut voir sur l’écran et sont immutables.

React ne change que ce qui est nécessaire, si on veut remplacer un élément par un autre, il va comparer les deux. Seule la différence sera modifiée dans le DOM, au lieu de réécrire tout le nouvel élément.

Les components
---

Les components sont des fonctions JS qui acceptent un seul paramètre (les “props”) et qui renvoie un élément React.  
```Javascript
function Welcome(props) {  
  return &lt;h1&gt;Hello, {props.name}&lt;/h1&gt;;  
}
```

On peut afficher le rendu d’un component avec JSX.  
```Javascript
function Welcome(props) {  
  return &lt;h1&gt;Hello, {props.name}&lt;/h1&gt;;  
}

const element = &lt;Welcome name="Sara" /&gt;;  
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
