# 19/12
Begonnen aan de opdracht

UML is deels af -- moeten nog wat aanpassingen gebeuren (zie blad)

DB model is ook redelijk in orde denk ik. Er is nog wat ruimte voor verbetering evt.

De verschillende lagen zijn aangemaakt.

**TO DO**: 
- Datasets kunnen importeren en kunnen schrijven naar de databank
- BL -> Model klassen opstellen
- ~~Lagen al opstellen (manager -> interface -> repository)~~

# 24/12

Adressen txt files inlezen lukt volledig

---
Nu bezig aan de namen in te lezen:
- Belgie lukt volledig 


# 28/12

**!** **Lees zeker na hoe de code van de json en reader werkt.**
Het inlezen van de straten van Belgie lukt perfect, hooray!

Later nog doen
- Gender eventueel veranderen naar een enum
- Zwitserland leest alle namen maar slaat ze op als beide genders

# 29/12
TO DO
- ~~Achternaamlezer maken~~
- ~~Adressen uploaden naar DB~~
- (namen uploaden naar DB)
- (eventueel als de rest beu ben verder XAML)

AchternaamInstellingen gemaakt bij Belgie in appsettings.json

**Maak de connectionstring eerst** 

Notes for later:
- In de SQLdatabank in geval van opvragen van de data MOET de straat gejoined zijn aan de gemeente en NIET de versie.
	  Stel je hebt 500 straten en 1000 gemeenten, dan zou hij 500 000 rows returnen bvb. -- a.k.a "Cartesian Product"


# 30/12
TO DO
- ~~Namen uploaden naar de DB~~
- Beginnen aan de UI-laag - Venstertjes maken
- 

Hoe pak ik de DL aan voor Voornamen
- VerwerkAlleVoornamen (manager)
- Interface correct aanroepen
- SQL statements schrijven in de repo

**BELANGRIJK -- TO FIX**
Er zit een fout bij het lezen van de namen van Zwitserland 
(tijdelijke oplossing voorzien in de reader)

Nu heb ik 2 if statements geschreven die snel checkt of de gelezen lijn/deel overeen komt met de footer, waarna hij een break doet

Oplossing: eventueel in appsettings.json voor iedere file een index meegeven die de laatste lijn bepaalt of gewoon een string meegeeft van wat de footer is zodat ik niet in de reader code altijd een if-statement moet schrijven.

TER OVERZICHT -ATM- :
De data inlezen van achternamen lukt perfect, nergens fouten
De data inlezen van voornamen lukt bijna perfect, enkel zwitserland runt 2 keer alles
De data inlezen van adressen lukt perfect (denk ik)

UI --
Landen tonen lukt
Gemeentes voor corresponderende landen tonen lukt

# 31/12
TO DO:
- Data ophalen uit de DB -> eventueel aparte repo klasse puur voor het opvragen van de methode
- Bepalen welke methodes er moeten gemaakt worden om de gesimuleerde klant samen te stellen

Welke methodes moet ik allemaal kunnen opvragen
- GeefAlleLanden
- GeefAlleGemeentesVanLand
- GeefAlleStratenVanGemeente
- GeefAlleVoornamenVanLand
- GeefAlleAchternamenVanLand

**Zeker de SIMMANAGER klasse bekijken om te zien hoe de gesimuleerde klanten worden aangemaakt**
De hulpmethodes echt wel vragen aan AI om het uit te leggen (snap er geen bal van)
**Het gedeelte met LINQ ook zien te begrijpen**

# 2/1

Applicatie werkt nu zo goed als volledig -- de exportwindow is af denk ik (test het zeker nog eens)

Wat staat er nog te doen:
- Alles nog eens goed testen
- Eventueel wat UT schrijven
- De code lezen en proberen begrijpen
- alles overzetten naar laptop en daarop testen