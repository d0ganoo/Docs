#### Jquery
## Bonnes patiques / approche objet => par module


```Javascript

(function (app){
  let self = {};
  
  self.init = function(){
    // some code
  }
  
  app.module1 = self;
})(NameApp);

(function (app){
  let self = {};
  
  self.init = function(){
    // some code
  }
  
  app.module2 = self;
})(NameApp);

$(document).ready(function () {
    NameApp.module1.init();
    NameApp.module2.init();
});

```
