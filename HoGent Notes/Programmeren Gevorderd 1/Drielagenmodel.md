# Single Responsibility
Elk onderdeel in je programma moet verantwoordelijk zijn voor slechts één ding. (Je kan dit bekijken per methode, klasse, module,...) Met andere woorden, een stukje code, een klasse of een laag in je software moet slechts één taak hebben en mag niet overmatig belast worden met meerdere verantwoordelijkheden.

Voordelen: 
- Als je een klasse moet wijzigen in de toekomst, dient er slechts één reden te zijn om dat te doen
- Voorkomt dat een klasse te veel taken krijgt
- Verhoogt de leesbaarheid, testbaarheid en onderhoudbaarheid van je code

Dit **principe** kan je ook toepassen op een hoger niveau dan klassen.
Het kan ook op een model met meerdere lagen worden toegepast door er voor te zorgen dat elke laag specifieke verantwoordelijkheden heeft en zich concentreert op één type taak.

# Loose Coupling
Een ontwerpprincipe waarbij componenten in een systeem zo onafhankelijk mogelijk van elkaar worden gemaakt. Dit betekent dat wijzigingen in één component minimale impact hebben op andere componenten. 

In het drielagenmodel (bestaande uit:)
- User-Interface / presentatielaag - **UI**
- Bedrijfslaag / Business Layer / domeinlaag - **BL**
- Datalaag / Data Layer - **DL**
Wordt dit als volgt toegepast

### Tussen presentatielaag (UI) en domeinlaag (BL)
- UI weet **niet** hoe de BL precies werkt
- Communicatie verloopt via duidelijk gedefinieerde interfaces
- presentatielaag roept alleen methodes aan zonder te weten hoe deze intern werken
- Wijzigingen in de GUI hebben geen impact op onderliggende logica

### Tussen domeinlaag (BL) en datalaag (DL)
- De business logica is niet direct afhankelijk van specifieke DB implementatie
- Er worden abstracties gebruikt zoals repositories of data acces objects ([[DAO]]'s)
- Domeinlaag werkt met modellen/entities zonder te weten hoe deze worden opgeslagen
- Bij wijziging van DB-technologie hoeft alleen de DL aangepast te worden

## Voordelen van deze losse koppeling
- Betere onderhoudbaarheid doordat lagen onafhankelijk kunnen worden aangepast
- Eenvoudiger testen omdat lagen geïsoleerd kunnen worden getest
- Flexibiliteit bij technische wijzigingen in één van de lagen
- Herbruikbaarheid van componenten in andere contexten

---
# User-Interface (UI)
Toont de gegevens aan de gebruiker, neemt invoer van de gebruiker aan.

### Toepassing van single responsibility
De UI moet niet verantwoordelijk zijn voor het rechtstreeks ophalen van gegevens uit de DB of uitvoeren van complexe BL-logica. De verantwoordelijkheid van deze laag is **enkel** gericht op het **presenteren** van info aan de gebruiker en het ontvangen van **user-input**

**Verboden:**
Geen domeinregels of andere business logica implementeren EN mag niet met de DL communiceren.

# Bedrijfslaag (BL)
Kernlogica van de applicatie

### Toepassing van single responsibility
De BL moet niet bezig zijn met het direct manipuleren van de DB of het presenteren van info aan de gebruiker. De verantwoordelijkheid van deze laag is alleen de logica bevatten die specifiek is voor het domein van de applicatie, zoals het valideren van gegevens, toepassen van bedrijfsregels en het coördineren van acties.

**Verboden:**
Vanuit deze laag met de gebruiker communiceren.


# Datalaag (DL)
Gegevensopslag en toegang tot de database

### Toepassing van single responsibility
De DL moet niet betrokken zijn bij gebruikersinterface-gerelateerde taken of complexe BL-logica. De verantwoordelijkheid van deze laag is zich concentreren op het effectief communiceren met de DB en het omzetten van gegevens tussen het domein en de DB.
