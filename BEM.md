[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md)

***

# BEM

Block-Element--Modifier est une méthodologie pour nommer les classes en CSS

.Block {
}

.Block--modifier {
}

.Block-element {
}

.Block-element--modifier {
}

Les blocks sont en "PascalCase" (ou UpperCamelCase), les elements et modifiers sont en "camelCase" (ou lowerCamelCase). Nous séparons le block de l'élément par "-" et le block ou l' element d'un modifier par "--".

Il existe plusieurs conventions de BEM. Celle-ci est la norme de montage.js.

La convention pseudo officielle ressemeble à: .my-block__my-element--my-modifier

L'inconvénient de ceci est que c'est moins lisible au premier abord qui est quoi, et de plus, les _ ne permettent pas de sélectionner facilement un terme en double-cliquant dessus.

Dans le but d'éviter de se faire écraser nos proppriétés par quelqu'un d'autre (lib, sdk etc...), il peut être utile de rajouter une organisation:

.org-Block-element--modifier. Tout en minuscule et si possible ne pas dépasser les 3 lettres. (Pour éviter d'alourdir le css)

La deuxième chose est la classe qui sert de sélecteur en JavaScript. Plutôt que binder un élément via sa classe "CSS" (à chaque classe sa responsabilité), il est nettement préférable de créer une classe spécifique au JavaScript. Cela donne : .org-js-Block-element--modifier. Il suffit simplement de rajouter -js entre l'organisation et le block.

Nous arrivons à la convention suivante : .org[-js]-Block[-element][--modifier]
