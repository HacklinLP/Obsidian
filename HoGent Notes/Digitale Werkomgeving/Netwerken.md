# Talstelsels
Wij gebruiken normaal gezien het **decimale** talstelsel (10-delig)
Door ze te combineren kunnen we ook grote getallen maken (30, 45, 60)

Computers werken intern met binaire getallen (bi=2). Ze gebruiken enkel 0 en 1. Ook hier worden er grote getallen gevormd door deze cijfers te combineren (10, 1011 1001)

In de informatica gebruikt men soms ook **hexadecimale** getallen (16-delig). We gebruiken dan 16 verschillende cijfers. 0 tot 9 en A tot F.
Om verwarring te voorkomen worden er aan hexadecimale getallen soms ook tekens toegevoegd.
Bvb. `0x12` of `#12`.

|   **Decimaal**   |  0   |  1   | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   | 12   | 13   | 14   | 15   |
| :--------------: | :--: | :--: | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|    **Binair**    | 0000 | 0001 | 0010 | 0011 | 0100 | 0101 | 0110 | 0111 | 1000 | 1001 | 1010 | 1011 | 1100 | 1101 | 1110 | 1111 |
| **Hexadecimaal** |  0   |  1   | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | A    | B    | C    | D    | E    | F    |

FYI: Voor het octale talstelsel te weten neem je gewoon de binaire notatie en splits je het in groepjes van 3 (ipv 4 zoals we altijd doen)

# Onderdelen van netwerk (definities)

**ISP**: Internet Service Provider

**NIC**: Network Interface Card = netwerk adapter

**Ethernet-kabel/UTP-kabel**: UTP = unshielded twisted pair

**Mac-adres**: = hardware-adres = physical adres. Een MAC-adres bestaat uit 6 bytes of dus 48 bits. Iedere producent krijg een bepaalde range toegekent waarin men binnen moet blijven zodanig dat er geen dubbels zijn.

**Switch**: Een switch verbind computers binnen hetzelfde netwoek (subnet). Hij houdt enkel rekening met MAC-adressen en kijkt niet naar IP-adressen.

**Hub**: Een hub houdt geen rekening met MAC-adressen en stuurt dus altijd alles naar iedereen door. Dit wordt echt zelden gebruikt. Nu gebruikt men dus bijna altijd een switch waar een vroeger een hub werd gebruikt.

**WAP**: = Wireless Access Point. Idem als een "switch/hub" maar dan Wireless (WiFi) (wordt soms ook WiFi-extender genoemd)

**Powerline-adapter**: Idem switch en/of WAP, maar via elektriciteit. Beide stopcontacten kunnen best op dezelfde "kring" (zekering) zitten. Niet altijd even stabiel en werkt niet goed met slappe elektriciteitsdraden (verlengdraad bvb) maar wel goed met "stijve" (bedrading in muur). Indien mogelijk kan je beter een ethernet-kabel gebruiken

**Router**: Een router verbindt verschillende netwerken (subnetten) met elkaar. Hij maakt wél gebruik van IP-adressen.
Een router heeft slechts een beperkt aantal ethernet-poorten. Deze moeten allemaal apart geconfigureerd worden en krijgen elk een IP-adres dat in het subnet ligt waarmee ze verbonden zijn. Dat IP-adres kan vrij gekozen worden (binnen het subnet). 

**Modem**: Een modem is een router die verbinding maakt met je ISP en dus voor de toegang tot het internet zorgt.

**Firewall**: Een firewall inspecteert het netwerkverkeer en kan bepaalde pakketten tegenhouden.

**LAN**: = Local Area Network. Het lokale netwerk, tot aan de modem via je ISP.

**WAN**: = Wide Area Network. Een WAN-verbinding is een verbinding die (eventueel gedeeltelijk) over "het internet" loopt. Met "het internet" wordt er hier het publieke netwerk bedoeld.

---

**Subnet Mask**: (bvb. 255.255.255.0) duidt aan waar het "netwerkgedeelte" eindigt en dus ook het "hostgedeelte" begint. Als we het omzetten naar binair zien we dat er bij het netwerkgedeelte eentjes staan en bij de host-bits nulletjes

Bijvoorbeeld: 255.224.0.0 heeft 8+3 "eentjes" en komt dus overeen met prefix-length 11.
Het netwerkgedeelte bestaat dan uit 11 bits, het hostgedeelte bestaat dan uit 21 bits.

**Prefix length**: In plaat van een subnet mask (zie boven) kunnen we ook de prefix-length (bvb. 24) gebruiken. De "prefix-length" is gewoon het aantal ééntjes in de subnet mask.
(m.a.w. uit hoeveel bit het "netwerkgedeelte" bestaat).

**CIDR-notatie**: De CIDR-notatie is de combinatie van een "dotted-decimal"-vorm met de prefix-length. Dit kan zowel bij een IP-adres (bvb. 192.168.10.10/24) als om een subnet (netwerk) te benoemen (bvb. 192.168.10.0/24), zoals hieronder wordt uitgelegd.
	**Netwerkadres**: Als je alle bits van het "hostgedeelte" op nul zet, dan krijg je het netwerkadres/naam van het subnet (bvb. 192.168.10.0)
	Bij een netwerkadres moet je wel altijd de subnet mask of prefix-length vermelden. Meesta wordt de prefix-length gebruikt en gebruiken we dus de CIDR-notatie (192.168.10.0/24).

**Default Gateway**: Om een computer buiten je eigen subnet te bereiken moet je steeds via je router gaan. De router die je eigen subnet verbindt met andere subnetten noemen we de default gateway.

Het IP-adres van je default gateway kan vrij gekozen worden door de netwerkbeheerder die de router configureerd. De enige beperking is dat dit IP-adres in het eigen subnet moet liggen. Het is echter wel de gewoonte om ofwel het eerste of het laatste beschikbare adres van het subnet te nemen. (bvb. 192.168.10.1 OF 192.168.10.254)

**Broadcast**: Een broadcast doen is een bericht zenden naar alle computers in hetzelfde subnet. Hiervoor gebruikt men het broadcast-adres dat bij je subnet hoort.

Het broadcast adres verkrijg je door alle bits van het "hostgedeelte" op één te zetten.

**DNS**: Domain Name System. Een DNS-server vertaalt een domeinnaam (chamilo.hogent.be) in een IP-adres (forward lookup) of evt. omgekeerd (reverse lookup).

Je gebruikt best een DNS-server "uit de buurt", bvb. die van je ISP. Enkel als daar problemen of beperkingen mee zijn, is het zinvol om een andere DNS-server in te stellen. (bvb. 8.8.8.8 -> Google)

**FQDN**: Fully Qualified Domain Name is een complete, eenduidige naam voor een specifieke computer of host op het internet. (bvb. chamilo.hogent.be). chamilo -> hostname, hogent.be -> domain name

---

| port number | protocol | (port-forward mogelijkheid) |
| ----------- | -------- | --------------------------- |
| 22          | SSH      | 2222                        |
| 53          | DNS      |                             |
| 80          | HTTP     | 8000                        |
| 443         | HTTPS    |                             |

---

# Verschillende IPv4-ranges
## Local/internal/private IPv4 address ranges

10.0.0.0/8
172.16.0.0/12
192.168.0.0/16

## Loopback Adress/localhost
127.0.0.0/8 (127.0.0.1 wordt veel gebruikt)

## Link-local Adressen
169.254.0.0/16

Beter bekend als **APIPA**-adressen

## TEST-NET Adressen
192.0.2.0/24

## Multi-cast adressen
224.0.0.0/4 (224.X.X.X tot 239.X.X.X)

## External/public IP-adress
Alle overblijvende adressen

# IPv6-ranges
## Loopback (=localhost)
::1/128

## Link-local (=binnen een subnet), private
FE80::/10 (FE8x, FE9x, FEAx, FEBx)

## Unique-local (=binnen een "site")
FC00::/7 (FCxx, FDxx)

## Global unicast adress (=public)
2000::/3 (2xxx, 3xxx)