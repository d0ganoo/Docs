## Supprimer les doublons dans un array 
```javascript
const dedupe = array => {
  return [...new Map(array.map(item => [item, true])).keys()];
};
```

## Manipuler les dates

```Javascript
function getWeekNumber() {
    let d = new Date();
    let DoW = d.getDay();
    d.setDate(d.getDate() - (DoW + 6) % 7 + 3); // Nearest Thu
    let ms = d.valueOf(); // GMT
    d.setMonth(0);
    d.setDate(4); // Thu in Week 1
    return Math.round((ms - d.valueOf()) / (7 * 864e5)) + 1;
  }
  
  function FirstDayOfWeek(sem:any, an:any){
    let debut=new Date()
    debut.setUTCFullYear(an,0,1);
    let FirstDayOfYear= debut.getDay()
    let FirstBitLength=0
    switch(FirstDayOfYear){
       case 0: FirstBitLength=FirstDayOfYear+2;
                   break;
       case 1: FirstBitLength=FirstDayOfYear;
                   break;
       case 2: FirstBitLength=FirstDayOfYear+5;
                   break;
       case 3: FirstBitLength=FirstDayOfYear+3;
                   break;
       case 4: FirstBitLength=FirstDayOfYear+1;
                   break;
       case 5: FirstBitLength=FirstDayOfYear-1;
                   break;
       case 6: FirstBitLength=FirstDayOfYear-3;
                   break;
    }
    let adddays=(sem-1)*7+FirstBitLength
    let finalDate=new Date()
    finalDate.setUTCFullYear(an,0,adddays)
    let finalDateEnd=new Date()
    finalDateEnd.setUTCFullYear(an,0,adddays+6)
    
    return (sem==0 || sem>53)?"erreur":an+" <br/>debut de semaine : "+finalDate.toLocaleString()+"<br/>fin de semaine : " +finalDateEnd.toLocaleString();
    }
```
