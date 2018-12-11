
[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

# Redux

Structure d'un projet Redux:

```Bash

|-- Src
  |-- actions
  |-- components
  |-- containers 
  |-- reducers
index.js

```

Redux permet d'avoir un gros objet State qui va contenir toutes les données de l'application. C'est le Store de redux.

### Les reducers

Un reducer est une fonction qui retourne un objet. Il permet de mettre à jour le Store de redux.
Chaque patie du store de redux est donc renseigné par un reducer.

Root reducer: CombineReducers(func) permet de lier les parties du store et leur reducer.

Les reducers ne sont jamais appelé directement dans notre application. Ils sont appelés par le biais d'un déclencheur qui va appelé tous les reducers qui sont présent dans le root reducer.
Donc au lancement de l'application tous les reducers sont appelés.

```Javascript

export default function(state,action){
  switch(action.type){
    case USER_SELECTED: return action.payload; // continent le user, cf l'action
  }
  return state;
}

```

### Connecter reduc à react

La fonction connect fait le pont entre redex et react: import {connect} from 'react-redux';

Code issus d'un container (après la class étendu du component react)

```Javascript

function mapStateToProps(state){
  return{
     myUsers:state.users
  }
}

export default connect(mapStateToProps)(nom_Component);

```
Le reducer retourne le state et mapStateToProps la transmet aux props de react. C'est connect qui définit mapStateToProps comme pont en react et redux.

### Les actions

Les actions permettent de déclencher le reducer attendu.
L'écriture de l'action se fait dans le dossier action

```Javascript

export function selectUser(user){
  return {
    type: USER_SELECTED,
    payload: user
  }
}

```

## Faire le pont entre les actions et les reducers

Code appartenant au container

```Javascript
import {bindActionCreators} from 'redux';

function mapDispatchToProps(dispatch){
  return bindActionCreators({selectUser:selectUser}, dispatch)
}

```
Dispatch permet d'envoyer l'action à tous les reducers et bindActionCreators de les rendre accèssible dans les props pour react.
