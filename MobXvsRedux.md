
[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Redux-thunk](https://github.com/d0ganoo/Docs/blob/master/Redux-thunk.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

# MobX vs Redux

Source : https://www.youtube.com/watch?v=khYesU0jTtI  __Grafikart__

Mobx est basé sur la notion d'écouteur/observeur de class.

```Javascript
import mobx from 'mobx';

class Tchat{
  constructor(){
    mobx.extendObservable(this, {
      messages:[],
      notifications:0;
    });
  }
}

let tchat = new Tchat();
mobx.autorun(function(){
  console.log('Voici la liste des messages : ', tchat.messages.join(', '));
});

global.tchat = tchat;
tchat.messages.push('Mon nouveau message'); // Mutation à l'arrache / déconseillé

```

Syntaxe différente mais un code qui fait exactement la même chose:

```Javascript
import mobx, {observable, action} from 'mobx';

mobx.useStrict(true); // Empêche les mutation à l'arache (oblige l'utilisation des actions)

class Tchat{
  @observable messages = [];
  @observabble notifications = 0;
  
  @action addMessage(message){
    this.messages.push(message);
  }
}

let tchat = new Tchat();
mobx.autorun(function(){
  console.log('Voici la liste des messages : ', tchat.messages.join(', '));
});

global.tchat = tchat;
tchat.addMessage('Mon nouveau message');

```

Dans cet exemple, on voit que mobx observe le tableau de message par le biais de __extenObservable__ et detecte un changement grâce à __autorun__  ou observe (fonction qui permet d'observer les variables de l'object du constructeur de la classe): c'est la magie de mobx.

autorun est intelligent, il se déclenche seulement sur la propriété modifiée et non pas sur tout l'objet (state) de extendObservable.

Conclusion:

Ce sont 2 générateurs de state avec une appoche différente du problème:

Mobx: l'approche est la moins contraingnate au niveau du fonctionnement. (La state peut garder la structure objet classique + greffe du système d'observable pour détecter les modifications mais magie noir mobx :p) Facile à utiliser avec react et angular Js (Avec vue, vaut mieux utiliser VueX)

Redux: Approche inspriré de la programmation fonctionnel. + testable avec moins d'effet de bord. Pas de mutation de la state. 
Problème concernant l'architecture de la state: Obligation de normaliser la state. Ne pas avoir d'objet trop imbriqué



