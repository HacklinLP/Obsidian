# Begin

Begonnen bij de DL met DTOs -> alle info die je uit de file haalt steek je in de DTO

Interface eerst maken (BL) -> big boss die zegt tegen de DL welke methodes hij moet bevatten
	Interface dient om te communiceren met een specifieke klasse in de datalaag


## FileReader (DL)

De **GetCharacters** methode is de enigste die public staat omdat dit terug moet 'antwoorden' aan de interface
	De ConvertToCharacter methode en ReadFile methode staan private omdat deze enkel worden aangeroepen vanuit DEZE GetCharacters methode (die dus in dezelfde klasse staat)
		Ze worden dus niet aangeroepen vanuit andere klassen

### De methode van Readfile (lijn 21)
Using streamreader gedeelte

We slaan de eerste lijn over omdat dit de 'header' is

string line -> "we gaan een lijn moeten lezen"

While loop -> lees alle lijnen tot als het null is (einde van de file)


string[] parts = line.Split(',')
	Je leest 1 lijn tot aan de komma. Na de komma 'jumped' hij naar de volgende plek in de array -> (In een csv is het altijd gescheiden door een komma -- als je wilt weten of het een ander teken is dan open je het in notepad en kijk)
	--
	--
	dtos.Add....
	Hier maken we dus eigenlijk een DTO objectje aan met de info die we zojuist uit de lijn hebben gehaald. 
	