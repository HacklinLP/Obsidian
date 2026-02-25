jsv9000.app -> toont werking van de time-outs en task queue
Promise krijgt prioriteit (gaat naar microtask queue)

-Moet eigenlijk niet gekend zijn, gewoon de werking snappen en achterliggende logica-

---

forEach() -- altijd gebruiken tenzij dat je vervroegd uit een loop moet


map() -- belagrijk -- Map functie gaat iets returnen, namelijk de nieuwe array in het voorbeeld (callback functie)

Belangrijk: De oorspronkelijke array wordt niet gewijzigd!
Over arrays mappen wordt veel gebruikt in react

reduce() -- weer een callback functie dat je meegeeft
De waarde die gereturned wordt zal in de accumulator gestoken worden. Hierdoor wordt er dus opgeteld tot het einde van de array
Er wordt dus eigenlijk soort van geloopt binnenin de functie
reduceRight() doet hetzelfde maar van vanachter beginnen

filter() --  bepaalde waarden uit een array 'uitfilteren'. Heel handig als je bijvoorbeeld een specifiek uit een array wil halen

Some() -- kijken of er een element gelijk is aan een bepaalde conditie

Includes() -- indien je dit gebruikt moet je zeker zijn dat je effectief verwijst naar het specifieke object en niet gewoon kijkt of er een object overeen komt met het object dat je zoekt. (je maakt dan eigenlijk gewoon een nieuw object met dezelfde waarden)

Every() -- Check of alle elementen gelijk zijn aan bepaalde voorwaarde/conditie

### rest parameter
In principe enkel bij functies

genoteerd als drie puntjes (...). Dit laat ons toe om argumenten mee te geven (ongelimiteerd) en die worden dan voorgesteld als een array.

kan handig gepaard worden met reduce om bijvoorbeeld een variabel aantal getallen mee te geven en die te laten optellen met elkaar.

### spread operator - belangrijk
gebruikt worden om twee arrays samen te voegen als één.


### Promises


### Async/Await
