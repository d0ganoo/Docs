
[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Redux-thunk](https://github.com/d0ganoo/Docs/blob/master/Redux-thunk.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

# MobX vs Redux

Mobx est basé sur la notion d'écouteur/observeur de class.

```Javascript
import mobx from 'mobx';

class Tchat{
  constructor(){
    mobx.extendObservable(this, {
      messages:[]
    });
  }
}

let tchat = new Tchat();
mobx.autorun(function(){
  console.log('Voici la liste des messages : ', tchat.messages.join(', '));
});

global.tchat = tchat;
tchat.messages.push('Mon nouveau message');

```
Dans cet exemple, on voit que mobx observe le tableau de message par le biais de __extenObservable__ et detecte un changement grâce à __autorun__ : c'est la magie de mobx.

autorun est intelligent, il se déclenche seulement sur la modifié et pas sur tout l'objet (state) de extendObservable.