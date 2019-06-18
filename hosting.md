Javascript fait une première lecture sur le code.
Il recherche les déclarations de variable et de fonction et les hisses en début de code.
Dans la deuxième lecture, javascript execute le code.

# Hosting de fonctions

Le hosting de fonction fonctionne que pour les déclarations de fonctions et pas sur les expressions de fonction.
(stockage de fonction dans une variable)

```Javascript
multiplie(2,2);
function multiplie(a,b){
  console.log(a*b)
}
```
Ce code fonctionne
```Javascript
multiplie(2,2);
var multiplie = function(a,b){
  console.log(a*b)
}
```
Ce code ne fonctionne pas

# Hosting de variables

Le hosting fonctionne que avec le var!! (ne marche pas avec le let et le const)

Le hosting de variable hisse la déclaration de variable mais pas l'assignation.
```Javascript
console.log(x);
var x = 5;
```
Ne fonctionne pas car:
```Javascript
var x;
console.log(x); // undefined
x = 5;
```
# Les types primitifs et Object
```Javascript
var a = 8;
var y = a;
y = 2;
console.log(a);
```
Comment les variables sont stocké en mémoire ?
// [] représente un espace mémoire

a [8]
y [ref a]
-> change l'espace mémoire de y à [2]

Les Objects fonctionne par référence et non pas par valeur !!!!
```Javascript
var x = {namme: 'FF'};
console.log(x)
```
En mémoire:

x [pointe vers l'object => 452]adresse:468             [name:'FF']adresse:452

Exemple:
```Javascript
var x = {namme: 'FF'};
var y = x;
y.name = 'Carlos';
console.log(x);
console.log(y);
```
En mémoire

x [pointe vers l'object => 452]adresse:468             [name:'FF']adresse:452

y [452]

x et y affiche Carlos // On a changé la propriété name de l'object

# Contexte d'exécution

Un contexte d'exécution est crée lorsqu'une fonction est exécutée.
Le code qui n'est pas dans une fonction appartient au contexte d'exécution global. (En js => window)

Un contexte d'exécution est composé de 3 éléments:

1- L'objet des variables // toutes les variables et fonctions définies dans ce context
- arguments de fonctions
- déclaration de variables
- déclaration de fonctions


2- La chaine des scopes // toutes les variables dont notre context aura connaissance et donc pourra y accéder

3- Le this // Objet associé au context









