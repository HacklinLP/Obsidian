Een variabele waarvan je de waarde niet kan veranderen.

Wat **WEL** kan veranderen is de inhoud van de content
(bijvoorbeeld de inhoud van een object of array)
```js
const person = { name: "Alex" };

// This is allowed:
person.name = "Sam";

console.log(person.name); // Sam

// This is NOT allowed:
person = {}; // Error
```

---
We gebruiken dit vooral als we een 'methode' gaan aanmaken of een event gaan aanroepen
bijvoorbeeld:

```js
const setup = () =>  
{  
    let div = document.getElementById("paradivke")  
    div.addEventListener('mouseenter', printEnter); 
}  
const printEnter = () => {  
    console.log("enter!");  
}
```

Eigenlijk dus gewoon als we een stuk code moeten runnen als het aangeroepen wordt.