Bij javascript mag je bijvoorbeeld wel 2 keer een var definiëren met dezelfde naam
```
var greeter = "hi";
var greeter = "hello";
```

**Hoisting** principe.
Declaratie van variabelen en functies worden naar de top van de scope verplaatst. Dit laat ons dus toe om eerst code te schrijven waar een variabele gebruikt wordt en dan pas de variabele aan te maken.

vb:
```
console.log(greet);

var greet = "hello";
```
De console zal hier daadwerkelijk 'hello' printen.

((check zeker de slides voor goede uitleg hierover -- ben niet zeker of juist))

VAR IS FUNCTION SCOPED
Als een var wordt gedifinieerd in een functie dan behoort het tot de scope van die functie

Voorbeeld:
```js
function example() {
	console.log(x);
	var x = 1;
	console.log(x);
}
```

Bovenaan zal het undefined zijn en onderaan 1.

**Met let en const ga je wel het gedrag hebben van in C# (wat handig is in heel veel gevallen)**

Bij const mag je ENKEL de referentie niet veranderen, wel de inhoud.

arr.push(5) of naamVanConst.fName = "Bob" mag dus wel.