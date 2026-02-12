Kan er bijvoorbeeld voor zorgen dat je code kan uitvoeren op een asynchrone manier

Timeout: Run de code maar na x aantal tijd
Interval: Run de code om de x aantal tijd

Queue: Volgorde waarop er dingen worden uitgevoerd (volgt first-in, first-out principe)

Eerst wordt er gekeken of de asynchrone lijst is afgerond en DAN pas wordt er gekeken naar de queue (of er alweer iets nieuw in staat om uit te voeren)

De timer van een interval bvb. zal nagenoeg nooit stipt stipt zijn hierdoor. Eerst moet alle taken afgehandeld worden en dan pas kan er iets uit de queue runnen.



Als er in de asynchrone lijst een timeout staat, wordt die naar de queue verplaatst en pas uitgevoerd als de asynchrone lijst compleet is (indien de timer ook al verlopen is)

**Voorbeeld:**
Stel iets op lijn 5 wordt naar de queue verplaatst met 25s timeout
Iets op lijn 1000 wordt dan ook verplaatst naar de queue met een 10s timeout.

Als de asynchrone lijst nu is doorlopen en we kijken naar onze queue, zien we dat de 10s timeout al verlopen is en de 25s timeout nog niet.

Er is inderdaad het first come first serve principe, MAAR als er een andere taak lager in de lijst sneller klaar is, dan wordt die ook direct uitgevoerd zonder te wachten op de taak die hoger staat in de lijst

Je kan dus eigenlijk redeneren dan de queue ook soort van asynchroon is aangezien er gewoon gekeken wordt van wat er al klaar is en dat wordt dan instant uitgevoerd.
Als er meerdere dingen tegelijk klaar zouden zijn dan beginnen we wel bij de taken die als eerst in de lijst zijn gekomen.


Timeout testen in console
```js
setTimeout(() => { console.log("Test");}, 1000);
```
Hier wordt dus iets geschreven in de console met een timeout (timer). Het zal verschijnen na 1s (1000ms).
Je zal ook zien als je dit intypt dat er een getal verschijnt. Dit is een unieke ID van de timout.

**Speciaal geval:**
Als er iets wordt gerunt met een timeout van 0s wordt het ook eerst verplaatst naar de queue en pas uitgevoerd nadat alles uit de asynchrone lijst is doorgelopen.


NPM of YARN --> blijf binnen een project altijd dezelfde gebruiken.