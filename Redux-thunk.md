[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Redux](https://github.com/d0ganoo/Docs/blob/master/Redux.md) | [Redux-thunk](https://github.com/d0ganoo/Docs/blob/master/redux-thunk.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)

# Redux-thunk

Redux ne permet pas les requêtes asynchrones => Le middleware redux-thunk répond a cette problématique
Il permet de passer une fonction à la place d'une action et de dispatcher depuis cette fonction. 

```Javascript

// Exemple d'action avec redux-thunk, au lieu de retourner une action, on retourne une fonction et on dispatch les actions

import thunk from 'redux-thunk';

export function getCountries(){
  return function (dispatch){
    axios("http://url_api").then(function(response){
      dispatch({type:GET_COUNTRIES, payload: response.data.countries})
    }).catch(function(error){
      disptach({type:ERROR_GET_COUNTRiES, error:error.response.data.detail})
    });
  }
}

```
