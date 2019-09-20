## Supprimer les doublons dans un array 
```javascript
const dedupe = array => {
  return [...new Map(array.map(item => [item, true])).keys()];
};
```
