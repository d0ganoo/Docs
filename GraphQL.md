API REST:
  - On récupère plus d'info qu'il n'en faut dans pas mal de cas. Pas très opti
  - Nous oblige souvent à faire plusieurs appels pour avoir le résultat souhaité
  - Ce n'est pas fait pour gérer les relations entre objets
  - C'est statique (On obtient le résultat que le développeur a choisi de renvoyer)
  - Impose des changements si on veut réutiiser les mêmes API dans plusieurs projets

GraphQL: 
  - Alternative aux API REST
  - Graph représentant le schéma de données
  
  Fonctionne avec express.
  
  Ex:
 
```Javascript
  const graphQL = requi("graphQL");
  const {
    GraphQLObjectType,
    GraphQLString,
    GraphQLInt,
  } = graphQL;
  
  const UserType = new GraphQLObjectType({
    name: 'User',
    fields: {
      id: {type: GraphQLString},
      firstname: {type: GraphQLString},
      age: {GraphQLInt}
    }
    })
```
```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```
