# Netwerkmodellen

#### Hoe nadenken over het netwerk?

---

Als je een conversatie per brief hebt met iemand, dan:

- Denk je na over wat je schrijft (en in welke taal)
- Je schrijft het adres op en doet de brief op de post

Je denkt niet na over _hoe_ die brief in de brievenbus van de ander raakt

note:
~ application-layer

---

De postbode die de postbussen leegt, denkt na over hoe die met de fiets naar het sorteercentrum fiets

note:
~ physical layer

---

Het sorteercentrum (waar je brief terechtkomt) leest het adres en zorgt ervoor dat dit doorgestuurd wordt naar het juiste andere sorteercentrum

note:
~ routing, network layer

---

De camionchauffeur rijdt naar het andere sorteercentrum en denkt na over de beste route

note:
~ physical layer

---

Het andere postsorteercentrum zorgt ervoor dat de juiste postbode je brief op ronde meekrijgt

note:
~ routing, network layer

---

De postbode fiets rond en steekt de brief in je brievenbus


note:
~ physical layer (maar ook een beetje routing)

---

Je correspondent opent je brief en leest deze

note:
~ application layer

---

## Wie denkt er na bij al deze stappen wanneer je een brief post?

Abstractie = niet nadenken over/verbergen van implementatiedetails

note:
- Voordeel: degene die de service voorziet, kan een stap wisselen voor een equivalente stap
	Bv: verkeer tussen twee sorteercentra met de trein ipv camion
- Voordeel: weinig cognitieve belasting voor hogere niveaus
	Moeten niet bezig zijn met de onderliggende complexiteiten
- Nadeel: als het misgaat, soms niet duidelijk waarom
	Bv: verloren brief: waar ging die verloren?
	Dan moet je vaak de abstractie openbreken en uitzoeken wáár het misgaat!

---
Lagenschema

note:
- zelfde laag = zelfde soort taak
- kunnen rekenen op ondersteuning *onderliggende* laag
- werking hogere laag is "onzichtbaar"
- één interactie op één laag volgt één protocol
- kunnen meerdere protocols op dezelfde laag zijn
- **even conceptueel, zullen zien wat dit concreet betekent met Wireshark**
---
Voorbeeld: filosofen

<img src='./afbeeldingen/filosofen.png' style='height: 70vh'/>
<!-- figuur overgenomen uit Tanenbaum, Computer Networks, 5e editie -->
note:
- 3-lagenmodel
- analogie stopt hier, maar kan verder toegepast worden
  - we zouden een "faxlaag" kunnen voorzien, maar de fax is hier "black box"

---
<!-- .slide:data-background="#ffffff"-->
![OSI-model](./afbeeldingen/osi.svg)
<!--<a href="https://commons.wikimedia.org/wiki/File:Osi-model-jb.svg">SVG edition:Gorivero</a>,<a href="http://creativecommons.org/licenses/by-sa/3.0/">CC BY-SA 3.0</a>,via Wikimedia Commons-->
note:

- verwacht niet dat je ze na deze slide allemaal uit het hoofd kent, gewoon dat je je een beeld vormt!

--

[In een notendop](https://www.youtube.com/watch?v=EPoNyBss5I8)

---
- conceptueel overzicht
- relaties tussen gehelen zijn duidelijk
- "swappable" (met beperkingen, bv. bedraad naar draadloos of interplanetair...)

note:
- Dit zijn voordelen van het lagenmodel

---
- Theorie: OSI-model
- Praktijk: TCP/IP-model

---
![TCP/IP](./afbeeldingen/TCP-IP_Model_-_en.png)
<!--afgeleid van 	 <a
								href="https://commons.wikimedia.org/wiki/File:TCP-IP_Model_-_en.png">Michel Bakni</a>,
							<a href="https://creativecommons.org/licenses/by-sa/4.0">CC BY-SA 4.0</a>, via Wikimedia
							Commons-->
note:

- spreken soms over "laag 1", "laag 2",... en betreft dan meestal dit model, van onder naar boven
- verwacht nog steeds niet dat je ze allemaal uit het hoofd kent!
- de concrete protocols zouden kunnen zijn "Filosofie", "Recht", "Geneeskunde",... of "Engels", "Frans", "Duits" of "Fax", "Telefoon", "e-mail",...
---

### Voorbeelden

1. Fysieke laag

---

### Voorbeelden

1. Fysieke laag

Definitie van hoe de fysieke kabel eruit moet zien.

Bv: een ethernetkabel moet 8 kabels hebben van 0.2mm dik, de stekkerkop moet er zo uitzien...

note:
- ethernetkabel
- radiogolven volgens bv. Wifi-protocol, 4G-protocol ...
- de fiber
- telefoonkabel

---

### Voorbeelden

2. Datalinklaag

---

### Voorbeelden

2. Datalinklaag

Beschrijft hoe het signaal over de kabel eruit ziet

Bv: een puls van 10ms op de groene kabel betekent "1", een puls op de bruine kabel is "0"

note:

Uiteraard is het véél complexer dan dit voor gigabits per seconde erdoor te krijgen
Andere voorbeelden:
de vorm van het radiosignaal in wifi/4G,
de puls in fiber, ...


---

### Voorbeelden

2. Datalinklaag: één- of tweerichtingsverkeer?

Simplex
Half-Duplex
Full-duplex

note:

Simplex: altijd in één richting; vb: radio, GPS-signaal vanaf satteliet; babyfoon; afstandsbediening TV/garagepoort/...
Half-Duplex: om beurten zenden en ontvangen, bv: walkie talkie
	> Dit kan snel omdraaien, bv elke 10ms wisselen van rol! Illusie full-duplex
Full-duplex:
	Ondersteunt tegelijk zenden en ontvangen

---

### Voorbeelden

3. Netwerklaag

---

### Voorbeelden

3. Netwerklaag

Beschrijft hoe de data op de juiste locatie raakt

**Routering**

note:

vb: IP-adressen, telefoonnummer en automatische schakelkast,
sorteercentrum van de post

Beschrijft ook wat er moet gebeuren als een pakketje _niet_ op de juiste bestemming raakt: TTL (time to live) <ref>https://en.wikipedia.org/wiki/Time_to_live</ref>

---

### Voorbeelden

4. Transportlaag


note:

- UDP (User Datagram Protocol)
- TCP (Transport Control Protocol)
- Connectie van een telefoon

---

### Voorbeelden

4. Transportlaag

Zetten (de illusie van) een **stabiele verbinding** op

> Poortnummers

note:

Laag 3 laat soms pakketjes vallen.
TCP probeert hier omheen te werken, door:
- pakketjes een volgnummer te geven
- indien een pakketje (volgnummer) niet doorkomt: dit pakketje opnieuw te vragen aan de andere kant
- de hoeveelheid pakketjes te regelen. Veel pakketjes die niet meer doorkomen?
	Minder pakketjes per seconde sturen!
  Alle pakketjes komen vlot door? Meer sturen want meer capaciteit beschikbaar!

---

### Voorbeelden

5. 6. 7. Application layer (+ presentation + Session)

note:

- HTTP(S)
- SSH
- Telnet
- Bittorrent
- ...

---
<!-- .slide:data-background="#ffffff"-->
![OSI-model](./afbeeldingen/osi.svg)
<!--<a href="https://commons.wikimedia.org/wiki/File:Osi-model-jb.svg">SVG edition:Gorivero</a>,<a href="http://creativecommons.org/licenses/by-sa/3.0/">CC BY-SA 3.0</a>,via Wikimedia Commons-->
note:

- wat bedoelen we met een "level 8 fout"?

---

<!-- .slide:data-background="#ffffff"-->
![netwerkcomponenten en situering](./afbeeldingen/netwerkcomponenten.png)
note:
- elke component ruwweg geassocieerd met bepaalde laag
- in principe enkel toegang tot eigen laag en lagere lagen
- metadata van lagere lagen mag worden aangepast, inhoud normaal niet
- hub: kopieert gewoon bits (in dat opzicht fysiek)
- switch: werkt alleen binnen één lokaal netwerk (kent geen laag 3 protocol), maar kopieert niet domweg
- router: inspecteert IP-adressen, dus kent het IP-protocol, dus laag 3
	Router kan tussen twee IP-ranges in werken, bv 78.77.*.* en 10.0.*.*

---
<!-- .slide:data-background="#ffffff"-->
![encapsulatie in het TCP/IP-model](./afbeeldingen/encapsulatie.svg)
<!--<a href="https://commons.wikimedia.org/wiki/File:Inkapseling_bij_tcp-ip-nl.svg">David Mudrák (mudrdmz)</a>, <a href="https://creativecommons.org/licenses/by-sa/3.0">CC BY-SA 3.0</a>, via Wikimedia Commons-->
note:
- allerlaagst: bits op het medium
- data van de hogere laag = "payload"
- "payload" is dus verschillend naargelang de laag
- dit is wat je in Wireshark te zien krijgt als je een pakket in detail bekijkt, je kan de verschillende laagjes data bekijken
---
<!-- .slide:data-background="#ffffff"-->
![encapsulatie doorheen het netwerk](./afbeeldingen/encapsulatie-doorheen-netwerk.svg)

note:
- constant proces van "inpakken, uitpakken, inpakken, uitpakken,..." van data
---
Client vs. server
![client-server interactie](./afbeeldingen/client-server.png)
<!--Client-server, afbeelding van <a href="https://pixabay.com/users/sandra_schoen-53876/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=341420">Sandra Schön</a> from <a href="https://pixabay.com//?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=341420">Pixabay</a>-->
---
Demonstratie Wireshark

note:
- surf naar website zonder TLS, bijvoorbeeld neverssl.com, nossl.sh of flowgorithm.org en toon de inhoud in Wireshark
- surf ook naar www.ubuntu.com of iets dergelijks en toon structuur


---

### Opdracht met bestaande trace

- Download `oefentrace.pcapng` van digitap.
- Welke lagen van TCP/IP zijn hier vertegenwoordigd?
- Uit hoeveel bytes bestaan de volledige pakketjes?
- Hoeveel bytes bedraagt de payload in elk pakket?
- Van waar komen deze pakketjes eigenlijk? Wat heeft ze doen genereren?
- Wat is het laag 3-adres van de client in deze interactie?
- Wat is het laag 3-adres van de server in deze interactie?
- Is deze interactie "simplex", "duplex" of "half-duplex"?
- Hoeveel hops zitten er (waarschijnlijk) tussen ons en de server?

---

### Eigen trace maken

- Start een capture in Wireshark
- Surf naar neverssl.com/online OF nossl.sh OF neverssl.eu/online
- Stop meteen de capture en sla op
- Start een nieuwe capture
- Surf naar www.ap.be
- Stop meteen de capture en sla op
- Zoek in beide captures de HTML voor de pagina
  - Verklaar
  
---

# Meer info

[Zie de paragraaf 'Layer Architecture' op het Wikipedia-artikel](https://en.wikipedia.org/wiki/OSI_model#Layer_architecture)
