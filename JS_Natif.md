[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

# JS natif

## Variables et leur portée  
* <b>globale</b>: Déclare une variable accessible partout
* <b>var</b>: Déclare une variable dans le contexte de l'exécution (scope de la fonction par exemple)
* <b>const</b>: Comme let mais ne peut pas être réassignée ou redéclarée
* <b>let</b>: Déclare une variable dans le bloc local (if, while...). Variable accessible depuis un bloc enfant

## Fonctions  
* <b>Déclaration (const a = function(){...} != function a() {})</b>: La déclaration classique “function a() {}” déclare une fonction nommée qui sera accessible depuis le haut du scope bloc local. Une expression comme “const a = function() {}” créée une fonction anonyme qui est ensuite assignée à la variable “a”, et les règles liées aux mot-clés “const” s’appliqueront.  
basiques  
* <b>Arrow function</b>: Syntaxe plus courte pour déclarer une fonction, mais qui change le comportement de “this”, “arguments”, “new.target” et “super” par rapport à une déclaration basique.  
* <b>Fonctions pures</b>: fonctions “déterministes” qui retourne un résultat similaire pour une même entrée (getDate() par exemple n’est pas pure)  
* <b>Déclaration (new Object() VS {})</b>: C'est deux déclarations font la même chose. La première instancie un nouvel objet Oject. En pratique on utilise toujours {}.  
* <b>Array</b>: Liste de plusieurs éléments indexés par un entier, le premier élément ayant pour index 0.  
* <b>Déclaration (new Array() VS [])</b>: la déclaration “new Array()” appelle le constructeur de la classe Array pour créer un objet, ce qui alloue de la mémoire. Un entier peut être passé en paramètre, permettant de fixer la taille du tableau.  
* <b>Scope</b>: Le scope défini la portée des variables.  
* <b>this</b>: Dans le contexte global ou en mode non strict, “this” est l’objet global, l’équivalent de “window” dans les navigateurs. Dans le contexte d’une fonction et en mode strict, this n’est pas défini par défaut.  
* <b>Closures</b>: C'est une fonction qui retourne une fonction. La fonction retounée capture l'environnement de la fonction appelante (closure) et va pouvoir lors de son exécution utiliser les variables de la closure alors que son contexte d'exécution a été détruit.
* <b>Bind</b>: Crée une nouvelle fonction qui, lorsqu'elle est appelée, a pour contexte this la valeur placée en paramètre. Cette fonction n’est pas exécuté.
* <b>Apply</b>: Fait la même chose que la fonction bind, mais elle est exécutée directement  
* <b>Promise</b>: 	L'objet promise est utilisé pour les traitements de façon asynchrone. Elle repésente une VALEUR qui peut être disponible maintenant, dans le futur voire jamais.
	```Javascript
	var promise = new Promise((resolve, reject) => resolve("Bonjour petite promise"));
	promise.then(e => console.log(e)); // Afiche : Bonjour petite promise
	```
	La méthode resolve(valeur) renvoie un objet promise qui est résolu avec la valeur donnée.
	Si la promesse revoyée possède une méthode then(), elle suivra cette méthode et prendra son état. 

* <b>async function</b>: Une async function définit une fonction asynchrone qui renvoie un objet AsyncFunction.
	```Javascript
	async function test(args){
		 // instructions
		 Promise
	}
	```
	Valeur de retour: Une promise qui sera résolue avec la valeur renvoyée par la fonction asynchrone ou rompue s'il y a une exception non interceptée émise depuis la fonction asynchrone.
* <b>Le mot clé await</b>: 
			Une fonction async peut contenir une expression await.
			await interrompt l'exécution de la fonction asynchrone et attend 
			la résolution de la promesse passée Promise. Puis reprise de la fonction async.
			Valide que dans les fonction async
	```Javascript
			function resolveAfter2Seconds(x) {
			  return new Promise(resolve => {
			    setTimeout(() => {
			      resolve(x);
			    }, 2000);
			  });
			}

			async function add1(x) {
			  const a = await resolveAfter2Seconds(20); 
			  const b = await resolveAfter2Seconds(30); 
			  return x + a + b;
			}

			add1(10).then(v => {
			  console.log(v);  // affiche 60 après 4 secondes.
			});
	```
* <b>Quelle est la différence principale entre une expression async function et une instruction async function ?</b>

	Dans une expression async function, on peut ommetre le nom de la fonction.
		 On peut donc utiliser une expression async dans une IIFE qu'on exécute au moment de sa déclaration.
	```Javascript
		 function resolveAfter2Seconds(x) {
		  return new Promise(resolve => {
		    setTimeout(() => {
		      resolve(x);
		    }, 2000);
		  });
		};

		(async function(x) { // fonction asynchrone immédiatement appelée
		  var a = resolveAfter2Seconds(20);
		  var b = resolveAfter2Seconds(30);
		  return x + await a + await b;
		})(10).then(v => {
		  console.log(v);  // affiche 60 après 2 secondes.
		});
	```

### Les différents types d’héritages:  
   * <b>Prototypes</b>: Chaque objet possède un lien vers un objet prototype qui possèdent également un prototype. C’est la chaîne des prototypes. Elle s'arrête seulement lorsque le protoype est null.
   * <b>Classes</b>: Une classe est une fonction spéciale composé d’un constructeur qui permet d’initialiser les objets créés avec la classe. Les classes remplacent les fonctions constructeurs. Une classe peut hériter des méthodes d’une autre classe par l'intermédiaire du mot-clé extends.
   * <b>Methode super()</b>: Mot clé permettant d'accéder aux fonctions et propriétés d’un objet parent
   * <b>Imports / exports</b>: le mot clé “export “ permet d’exporter des variables, objects ou fonctions déclarées dans un fichier pour les uttiliser dans un autre fichier grâce au mot clé “import” 

## Web worker

Un web worker fournit un moyen d'exécuter des scritps dans un thread parallèle au thread principal.
Un worker a son propre fichier js (name.js)
Un worker a son propre contexte global qui est différent de window.
Les données sont envoyées entre le worker et le thread principal via un système de messages.
Envoie grâce à postMessage();
Réponse grâce à onmessage();
 
* <b>Workers dédiés</b>:

Un worker dédié est seulement accessible depuis le script qui l'a appelé.

* <b>Workers partagés</b>:

Un worker partagé est accessible depuis plusieurs scritps.
Utilisation de ports.

## DOM (Document Object Model)

Le DOM est un modèle charger dans le navigateur. La représentation du document est un arbre nodal.
Chaque noeud représente une partie du document

### Les 4 types de fuites mémoires en JS

#### 1- Les variables globales créées accidentelement.

```Javascript
	function foo(arg) {
	    bar = "this is a hidden global variable";
	}
	// ou
	function foo() {
	    this.variable = "potential accidental global";
	}
```
Le mode strict permet de détecter ces erreurs.

#### 2- Les minuteurs ou rappels oubliés.

Penser à clear les intervals (setInterval() => clearInterval())
Dans le cas des Observeurs (addEventListener):Faire des appels explicites pour les supprimer une fois qu'ils ne sont plus nécessaires.

```Javascript
	var element = document.getElementById('button');
	function onClick(event) {
	    element.innerHtml = 'text';
	}
	element.addEventListener('click', onClick);
	// Do stuff
	element.removeEventListener('click', onClick);
	element.parentNode.removeChild(element);
```

#### 3- Hors des références DOM

Attention lorsque l'on stock des élements du DOM dans un objet, il y a alors 2 références à supprimer.
La référence vers l'objet et la référence de l'arbre du DOM. (window + enfants)

#### 4- Closures

Exemple de grosse fuite:

```Javascript
	var theThing = null;
	var replaceThing = function () {
	  var originalThing = theThing;
	  var unused = function () {
	    if (originalThing)
	      console.log("hi");
	  };
	  theThing = {
	    longStr: new Array(1000000).join('*'),
	    someMethod: function () {
	      console.log(someMessage);
	    }
	  };
	};
	setInterval(replaceThing, 1000);
```



unused a une référence pour originalThing alors qu'elle n'est jamais utilisé...

## Gestion de la mémoire (garbage collector)  
 
Le garbage collection représente le processus de libération automatique de la mémoire.
Il répond à la question: Est-ce que la mémoire est encore requis ? (un objet n'a pas d'objet le référençant)

Depuis l'implématation de l'algorithme mark-and-sweep dans le garbage collection,
il répond maintenant à la question: Est-ce que la mémoire aloué est encore ratachée à ne autre partie de l'application ?
(Un objet possède 0 référence) 

Cette approche automatique contraste avec les langages bas niveau comme le C, où la mémoire doit être allouée par le développeur.  

## Ecmascript  
 
* <b>ES5</b>: ECMAScript est un standard, et JavaScript en est l’implémentation la plus connue. ES5 est la cinquième édition d’ECMAScript, qui clarifie les ambiguïtés de la 3e édition et ajoute les choses suivantes : accesseurs, introspection, contrôle des attributs, fonctions de manipulation de tableaux supplémentaires, support du format JSON, mode strict.  
<b>ES5 strict</b>: Le mode strict transforme les erreurs silencieuses en erreurs “throw”, interdit certains mots-clés qui seront définis dans des versions ultérieurs de ECMAScript (package, private, protected...) et rend l’optimisation du code par les interpréteurs JavaScript plus facile.  
* <b>ES6 (aka ES2015)</b>: Remplacement syntaxique des fonctions constructeurs par des classes. Fonctions Fléchées, Let et const, portée du this, destructuring, template string, spread operator, parametre rest “Modules, classes, portée lexicale au niveau des blocs, itérateurs et générateurs, promesses pour la programmation asynchrone, patrons de destructuration, optimisation des appels terminaux, nouvelles structures de données (tableaux associatifs, ensembles, tableaux binaires), support de caractères Unicode supplémentaires dans les chaînes de caractères et les expressions rationnelles, possibilité * d'étendre les structures de données prédéfinies.”
* <b>ES7 (aka ES2016)</b>: Fonction includes, exponentiation operator
* <b>ES8 (aka ES2017)</b>: Fonctions await et async, permettant de gérer l’asynchrone d’une manière plus lisible que les callbacks et les Promise. Le mot clé “async” permet de créer une fonction asynchrone qui sera donc exécutée dans un thread parallèle. Le mot clé “await” suivi d’une promesse n’est valable que dans une fonction async, et mettra en pause l’exécution de la fonction, tant que la promesse n’est * pas résolue. ES8 ajoute aussi des méthodes supplémentaires pour les classes String et Object.
* <b>ES9 (aka ES2018)</b>: Les opérateurs rest et spread appliqués aux objets, l’itération asynchrone, et de nouvelles fonctionnalités dans les expressions régulières.
  
## Le typage en JS  
  
* <b>Typescript</b>: Langage de programmation qui se compile en Javascript natif, et qui permet un typage statique des variables et des fonctions, ainsi que la création de classes et d’interfaces.  
* <b>Flow</b>: Performe le même service que Typescript, mais n’est pas un langage de programmation à part entière. C’est un “type checker” qui fonctionne avec des annotations de types similaires à TypeScript, mais qui devront être supprimés du code source avec un outil tiers comme Babel ou flow-remove-types. En plus du typage, Flow examine la structure générale du programme.  
* <b>Notion d’immutable en JS</b>: Ce qui est “immutable” ne changera pas de valeur une fois défini. En JavaScript c’est le cas des nombres et des chaînes de caractères (la méthode slice par exemple ne modifie pas la chaîne de caractères sur laquelle elle est appelée, mais en créé une nouvelle). En revanche ce n’est pas le cas des tableaux et des objets. 

## Utilisation des web socket  
  
Elle permet d’ouvrir une connexion permanente entre le navigateur et le serveur. Ainsi, chaque requête est plus rapide, et plus légère.  
Connection du serveur vers le navigateur.

## Notion de Progressive Web App  
 
Application web tirant avantage des fonctionnalités des navigateurs modernes et de l’expérience mobile.  
Fluide, rapide, légère.  
Chargé une fois, puis possibilité d’utilisation hors connexion.  
Expérience immersive: possibilité d’affichage plein écran.

## Paradigmes de programmation  

* <b>Procédurale</b>: En programmation procédurale, le développeur écrit des procédures/fonctions qu’il appellera dans le code en fonction de ses besoins.
* <b>Orientée objet</b>: Approche qui consiste à définir des classes possédants des attributs et des méthodes, puis à créer des instances de ces classes : les objets.
* <b>Réactive</b>: Paradigme qui met l’accent sur le flux de données, la gestion d'événements, et la propagation du changement. En programmation impérative, une expression comme “a = b + c” ne changera pas la * valeur de a dans le futur si b ou c changent. Au contraire dans la programmation réactive, sa valeur changera automatiquement si b ou c changent.
* <b>Fonctionnelle</b>: La programmation fonctionnelle se concentre sur la déclaration et l’appel de fonctions pures, évitant les effets de bord.
