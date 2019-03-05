
[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

source : https://putaindecode.io/fr/articles/js/react/react-new-context-api/

# API context

Depuis la version 16.3, l'Api context de react est devenue viable, plus facile à uiliser avec une syntaxe assouplie et simplifiée.

### A quoi ça sert ?

A l'instar de redux, Api contexxt permet de rendre disponible des propriétés au sein de ses composants React sans avoir à les passer directement à ces derniers.
Avec API Context, on peut facilement créer un ou plusieurs stores pour nos données.

## Exemple d'utilsation

```Javascript
// store/UserProvider.js
import React, { createContext, Component } from "react"; // on importe createContext qui servira à la création d'un ou plusieurs contextes

/**
 * `createContext` contient 2 propriétés :
 * `Provider` et `Consumer`. Nous les rendons accessibles
 * via la constante `UserContext` et on initialise une
 * propriété par défaut "name" qui sera une chaîne vide.
 * On exporte ce contexte afin qu'il soit exploitable par
 * d'autres composants par la suite via le `Consumer`
 */
export const UserContext = createContext({
  name: "",
});

/**
 * la classe UserProvider fera office de... Provider (!)
 * en englobant son enfant direct
 * dans le composant éponyme. De cette façon, ses values
 * seront accessibles de manière globale via le `Consumer`
 */
class UserProvider extends Component {
  state = {
    name: "Putain de Code", // une valeur de départ
  };

  render() {
    return (
      /**
       * la propriété value est très importante ici, elle rend
       * le contenu du state disponible aux `Consumers` de l'application
       */
      <UserContext.Provider value={this.state}>
        {this.props.children}
      </UserContext.Provider>
    );
  }
}

export default UserProvider;
```

```Javascript
// app.js
import React from "react";
import { render } from "react-dom";
import Hello from "./Hello";

// On importe la classe `UserProvider`
import UserProvider from "./store/UserProvider";

const styles = {
  fontFamily: "sans-serif",
  textAlign: "center",
};

const App = () => (
  <div style={styles}>
    {/* A noter qu'aucune propriété n'est passée au composant `Hello` */}
    <Hello />
  </div>
);

render(
  /**
   * On pourrait tout à fait n'englober que les composants qui
   * nous intéressent, mais pour l'exemple, nous englobons le bootstrap
   * de notre app dans notre `UserProvider`
   */
  <UserProvider>
    <App />
  </UserProvider>,
  document.getElementById("root"),
);
```
