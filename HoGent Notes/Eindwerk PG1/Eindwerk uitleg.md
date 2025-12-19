# Doelstelling

We moeten een **Klantensimulator** maken die testdata kan genereren voor diverse landen.
Voor **Elk** land moet er een *realistische* combinatie gemaakt worden (gegenereerd worden) van:
- voornamen
- achternamen
- adressen
	- straat
	- huisnr
	- gemeente

De gegenereerde klantendatasets worden gebruikt voor test- en demonstratiedoeleinden

Ze worden opgeslagen in een **Databank**

---
# Beschikbare gegevens

Er zijn voor verschillende landen gegevens beschikbaar, maar deze zijn niet steeds in hetzelfde formaat

**!!** Bekijk zeker ieder document (bvb. via Excel) om te kijken naar het formaat

## België

![[Pasted image 20251211232205.png]]

---
Mannennamen_belgië.csv heeft volgende structuur:

| Volgorder van voorkomen | Naam    | # keer dat voorkomt |
| ----------------------- | ------- | ------------------- |
| 1                       | Marc    | 61231               |
| 2                       | Jean    | 59366               |
| 3                       | Patrick | 49546               |
| 4                       | Luc     | 46798               |
| 5                       | Michel  | 43352               |
Hetzelfde geldt voor de familienamen

---
De adresgegevens vinden we dan bvb. terug in belgium_streets2.csv (afkomstig van OpenStreetMap)

| Municipality | Street                  | HighwayType  |
| ------------ | ----------------------- | ------------ |
| Fernelmont   | Rue de Thiribut         | residential  |
| Yvoir        | Rue du Bois des Loges   | residential  |
| Fernelmont   | Avenue de la Libération | tertiary     |
| Fernelmont   | Rue de pontillas        | unclassified |
### *Wat is de betekenis van HighwayType?*
In OpenStreetmap (OSM) betekent de tag highway=* dat een object een weg- of pad-gerelateerde functie heeft.

Het woord moet hier dus niet letterlijk worden opgevat: het is een verzamelterm voor vrijwel alle soorten wegen, straten en paden.

De tag wordt gebruikt voor onder andere:
	- Autowegen(bvb. motorway, trunk)
	- Normale wegen (bvb. primary, secondary, residential)
	- Landwegen (unclassified, track)
	- Fietspaden (cycleway)

Voorbeelden:
- highway=motorway --> Snelweg
- highway=primary --> Belangrijke hoofdweg

---
#### Samenvatting:
highway=* definieert het type weg of pad van een object in OSM.

Het betekent dus niet per se "snelweg", maar duidt op alles wat te maken heeft met verkeersroutes.

## Denemarken:
![[Pasted image 20251211235745.png]]

---
Het bestand 'foravne 2025 - maend (3+) - med overskrifter.txt bevat de voornamen voor **mannen** en het aantal keer dat deze naam voorkomt.'

| Navn    | Antal |
| ------- | ----- |
| PETER   | 46145 |
| MICHAEL | 44161 |
| LARS    | 42961 |
| THOMAS  | 41842 |
| JENS    | 41333 |

Voor **vrouwennamen en familienamen** is dit op een analoge manier opgesteld.

--- 

De **straten** zijn exact hetzelfde opgesteld als België.

| Municipality | Street                  | HighwayType  |
| ------------ | ----------------------- | ------------ |
| (unknown)   | Rue de Thiribut         | residential  |
| Yvoir        | Rue du Bois des Loges   | residential  |

Ook hier moet er gefilterd worden op HighwayType. Hebben straten geen Municipality (unknown dus) dan moeten ze *niet* worden opgenomen

 **!**  Ook merken we op dat de naam van de gemeente steeds gevolgd wordt door *"Kommune"*. Dit moeten we **weglaten**.

## Polen

De poolse namen zijn dan weer helemaal anders opgesteld. Deze zijn namelijk **niet** beschikbaar als **txt**, maar als **json**.
```json
/*DIT IS NOG NIET COMPLEET DENK IK*/
"title": "Polish"
"name": {
	"first_name_male": [],
	"first_name_female": [],
	"last_name": []
}

/*ingevuld*/
"title": "Polish"
"name": {
	"first_name_male": [],
	"first_name_female": [],
	"last_name": []
}
```

Voor deze namen hebben we **niet** ter beschikking hoeveel keer ze **voorkomen**.

## Tsjechië
Bij dit land bevinden alle gegevens zich in het volgende json-bestand (cz.locale.json).
Ook hier zijn er geen gegevens beschikbaar over de frequentie van de namen.
```json
"title": "Polish"
"address": {
	"city_name": [],
	"street": []
}
"name": {
	"male_first_name": [],
	"female_first_name": [],
	"male_last_name": [],
	"female_last_name": []
}
```

De namen van de gemeenten en de straatnamen bevinden zich eveneens in dit bestand, maar er is **geen** **verband** tussen de **straatnaam en de gemeente**.
m.a.w
Deze mag dus willekeurig worden toegekend.

## Zweden
Voor Zweden zijn de volgende bestanden beschikbaar:
![[Pasted image 20251212004822.png]]

Voor de gemeentenamen gelden dezelfde opmerkingen als in[[Eindwerk uitleg#Denemarken|Denemarken]].
Voor de vrouwen- en mannennamen wordt ook de gemiddelde leeftijd (medelålder) meegegeven, maar daar houden we geen rekening mee.

# Uitvoering
## Deel 1 -- Uploaden-tool
Upload de gegevens in een SQL databank, zodat er voor de simulaties geen gebruik meer moet gemaakt worden van de files. 

Zorg ervoor dat de upload-tool flexibel en uitbreidbaar is. 

Het moet eenvoudig zijn om nieuwe landen toe te voegen

## Deel 2 -- Simulator
De simulator zelf schrijven.

De simulator moet volgende instellingen en/of keuzes bevatten:
- Het land waarvoor de simulatie moet worden uitgevoerd
- a
- geef de optie om ook specifieke gemeenten te selecteren(in dit geval worden enkel adressen binnen deze gemeentes gesimuleerd). Extra geefeen percentage meevoor elke gemeente.
- het aantal klanten dat moet worden gesimuleerd
- Opdrachtgever waarvoor we de simulatie maken
- Minimum en max leeftijd
- Huisnummerdefinities