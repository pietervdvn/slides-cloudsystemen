# Wat is een communicatienetwerk?
---

### Wat is een communicatienetwerk?

Een (fysiek) systeem om data rond te sturen

---

### Voorbeelden van communicatienetwerken?

---

[Intro van "John Wick", welke communicatienetwerken zien jullie?](https://youtu.be/ro-uU074bj8)

notes:
buizenpost, telefonie (analoog), telefonie met automatische schakeling, manuele post
Maar ook: databank (in de vorm van een archief)

---

### De post

![decoratieve afbeelding brievenbus](./afbeeldingen/letter-box-4603815_1280.jpg)
<!-- Afbeelding van <a href="https://pixabay.com/nl/users/albarus-1663074/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=4603815">René</a> via <a href="https://pixabay.com/nl//?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=4603815">Pixabay</a>-->

---

Hoe oud is de post? Wanneer ontstonden de eerste postsystemen?

note:
Zie wikipedia voor achtergrond: https://en.wikipedia.org/wiki/Mail
- Eerste post rond 550 of zelfs 1700 voor Christus (!) in Iran, vooral om belastingen te regelen
- India: rond 300 voor Christus
- Rome: 50 BC

---

### Hoe is de post georganiseerd?

---

### Hoe is de post georganiseerd?

Brieven worden verzameld in een postsorteercentrum (typisch: provincie)

Post wordt gesorteerd per provincie
- Eigen provincie wordt rondgebracht
- Andere provincie: wordt naar _dat_ sorteercentrum gebracht
- Internationale post gaat naar centrale, internationale hub (Brussel)

---

### Internationale post

_Peering agreement_ met bevriende, buitenlanse posterijen

> wij brengen jullie post als jullie onze post rondbrengen

note:
Deze peering agreement heeft ons zuur opgebroken. 
Deze werd gemaakt in de veronderstelling dat er ongeveer evenveel uitgaande post is als binnenkomende.
Uitgaande post brengt op door internationale postzegels, verkocht door BPost.
Binnenkomende post is een kost: want die moet rondgebracht worden.

Vroeger ging een binnenkomende brief meestal gepaard met een uitgaand antwoord, dus dit komt ongeveer even.
Vandaag de dag: veel binnenkomende pakketjes uit china, via een _digitale_ bestelling...

---

### Welke transportmiddelen gebruikt de post?

note:
Brieven/pakketjes worden via verschillende manieren vervoerd:
te voet, fiets, auto, vliegtuig, boot, trein, koets, ...

Dankzij hubs gaan brieven van één transportmodus naar de andere

---

### Nadelen van de post?

---

### Nadelen van de post?

- Brief kan verloren gaan
- Je weet niet of je brief ontvangen is
- Piekperiodes (bv. rond kerstmis/nieuwjaar): langere levertijden door congestie
- maximale grootte en gewicht van zendingen

---

# Andere communicatienetwerken


---

[Tom Scott en de eerste telecomscam](https://www.youtube.com/watch?v=cPeVsniB7b0)

notes:
Eerste telecom-scam met de beurs, 1830

---

### Optische telegraaf

<div style="display: flex; gap-x: 2rem; justify-content: center; gap: 2rem">
<img src='./afbeeldingen/Reseau_chappe77.png' style="width: 25%"/>
<img src='./afbeeldingen/OptischerTelegraf.jpg' style="width: 25%"/>
</div>

Er liep een semafoorlijn van Parijs, [via Antwerpen naar Amsterdam](https://www.oudhouten.nl/recente-tijd/19e-eeuw/chappe/)

note:
- CC-BY-SA https://en.wikipedia.org/wiki/Optical_telegraph#/media/File:OptischerTelegraf.jpg
- CC-BY-SA https://en.wikipedia.org/wiki/File:Reseau_chappe77.png
- Meer weten, geen leerstof: https://en.wikipedia.org/wiki/Optical_telegraph
- "Semafoor": drager van het teken

---

### Book recommendation

"Going Postal" van Terry Pratchett (discworld)

Gaat over concurrentie tussen de post en een semafoornetwerk (in een fantasy-wereld)

> GNU Terry Pratchett

---


### "Sorry, ik ben verkeerd verbonden"

Waarvan komt dit?


---


### Telefoonlijnen

[Switchboard operator](https://www.youtube.com/watch?v=s9aThqUnGO0)

note:
- Op hackerkampen worden vaak nog oude field-phone netwerken uitgerold. Je mag die zélf bedienen daar!

---

![](./afbeeldingen/why.jpg)


---

### Switchboard
 
Vanaf ieder "gaatje" vertrekt een kilometerslange koperen kabel,
- verbonden met het toestel van een klant
- of verbonden met een switchboard in een andere stad

Wat zijn de *nadelen*?

note:
verkeerd verbonden: operator heeft kabel in het foute gaatje gestoken!

---

### Switchboard: nadelen

Nadeel: als er een telefoongesprek op bezig is, is de lijn bezet. Als er maar 10 kabels zijn tussen twee steden, maximaal 10 gesprekken tussen die steden op hetzelfde moment

Nadeel: operator kan altijd 'luistervinken'

Nadeel: menselijke operator: duur, maakt vergissingen
	Later geautomatiseerd met automatische switches, zoals de [strowger switch](https://en.wikipedia.org/wiki/Strowger_switch)

---

### Automatisch switchboard

[Strowger switch](https://www.youtube.com/watch?v=bvPH-tsD9ZM)

note:
- eerste halve minuut voor switching-process
- https://en.wikipedia.org/wiki/Strowger_switch voor achtergrondinfo (geen leerstof)

---

# Het internet

---

### De structuur van het internet lijkt het meest op de structuur van:

(stemming)

- A. de post
- B. het telefoonnetwerk
- C. het telegrafie-netwerk


---

### De structuur van het internet lijkt het meest op de structuur van:

(stemming)

- *A. de post*
- B. het telefoonnetwerk
- C. het telegrafie-netwerk

note:
Het juiste antwoord is: _de post_!
De digitale brieven (data-pakketjes) worden naar een centraal punt gestuurd, daar gesorteerd en verder doorgestuurd.
Tussen de verschillende netwerken zijn er "peering agreements" en "exchange points"

Het is aanlokkelijk om het telefoonnetwerk te zeggen, omdat het internet oorspronkelijk deze hardware gebruikte.
Echter, net zoals de post, kunnen de ""brieven"" via verschillende "transportmiddelen" vervoerd worden: 
electrische signalen via koper, radiogolven, licht in glasvezels, ...


---

## De Post vs Het Internet

- Verloren brieven ⇔ Pakketverlies
- Overbelasting ⇔ Congestie
- Een "eindadres" ⇔ IP-address
- Verschillende transportmodi
- Peering agreements tussen ISPs/Landen
 
 
---

Een internet / Het Internet
![het Internet als een hiërarchie van geconnecteerde netwerken](./afbeeldingen/een-het-internet.png)
<!-- figuur: Koen Laurent / Wouter Peetermans -->

---

## IP-protocol

Set van afspraken en regels (protocol) om Internet-data-pakketten op de juiste plaats te krijgen


---

## IP-Addressen?

Net zoals in de post, krijgt/heeft iedere computer op het internet een "adres"

note:
- Wie weet er de eigenschappen?

--

## IP-addressen: IPv4

> Het oude formaat

4 getallen tussen 0 en 255

Vergelijkbaar met een telefoonnummer

---

## Hoeveel IP-adressen zijn er?

note:
2^32 = ongeveer 4.2 miljard
Aantal mensen: 8 miljard anno 2022 (https://en.wikipedia.org/wiki/World_population#Milestones_by_the_billions)
Dus ongeveer een _half_ IP-adress per persoon
Hoeveel internet-apparaten hebben jullie? 

note: 
(Smartphone, Laptop, Tablet, bewakingscamera, slimme deurbel, IoT sensor, online VPS)
Gemiddeld 3 apparaten PP in de Westerse wereld!

note:
- te weinig IP-adressen!
- Verschillende truuks, zoals NAT, meerdere domeinen per IP,

---

### Oefening IP-address


- Wat is het IP-adres van je computer? Noteer dit

> Om je IP-addr te zien, gebruik `ip addr` op linux of `ipconfig \all` op windows

- Vergelijk dit met wat https://whatismyipaddress.com/ (of soortgelijke website) rapporteert; noteer dit
- Wat zegt het veld 'ISP' op bovenstaande website?

Doe bovenstaande opzoekingen met op **AP Wifi**, **Bletchley** en je **mobiele hotspot**

Vergelijk met je buren

---

## NAT

Waarom een ander adres op je computer als via die website?

note:
- We delen binnen AP-Wifi één IP-adres, de router stuurt de pakketjes juist door
- Heel wat trickery, zien jullie meer over in Datacom & Netwerken

---

## De ISP

ISP = 'Internet Service Provider'

Bedrijf of organisatie dat klanten _netwerkdiensten_ aanbiedt


note:
- Bv: Telenet, Proximus, Orange, EDPNet, Digi, Belnet, Starlink

---

## De ISP

Vergelijk het (publieke) IP-adres dat je hebt via je hotspot met iemand die dezelfde provider heeft als jij.

Wat valt op?

note:
- De eerste getallen zouden hetzelfde moeten zijn

---

## IP-adressen

Toegekend in blokken door het ICANN


- 5.23.128.* tot 5.23.255.*, 62.205.*.*, 78.20.*.*-78.23.*.*, (en meer): [Telenet](https://apps.db.ripe.net/db-web-ui/query?bflag=false&dflag=false&rflag=true&searchtext=Telenet&source=RIPE&types=inetnum)
- 12.*.*.*: AT&T (Amerikaanse Telecom)
- 17.*.*.*: Apple
- 10.*.*.* en 192.168.*.*: intern gebruik binnen netwerken
- 127.*.*.*: loopback

---

## IPv6

Nieuwere versie van IP-addressen.

Voorbeeld: `2001:0db8:85a3:0000:1319:8a2e:0370:7344`

- 4 getallen van 32 bits = 128 bits
- Vanaf juni 2012 voor het eerst publiek bruikbaar

note:
wij gebruiken in de cursus vnml IPv4

---

# Hoe raakt een pakketje op de juiste plaats?

---

### Router

Apparaat dat een pakketje ontvangt en in de juiste richting verder stuurt

Bv: Wifi Access Point

_Meer hierover in een volgende les_

---

# Oefeningen

---

### Ping

- Windows: `ping /?`
- Mac / Linux: `man ping`
- geblokkeerd op AP-wifi en Eduroam, maar eigenlijk ongevaarlijk; kan op Bletchley

note:
- iemand die de term van ergens kent? (Pingpong)
  - wat staat er dan vaak bij?
- geeft idee kwaliteit verbinding (snelheid respons)
- ontvanger is niet verplicht te antwoorden!

Hoe: 
Windows: open powershell, type `ping example.org` en duw enter
Linux: open terminal, zelfde

---
 
### Opdracht

- verbind met Bletchley of zoek een online ping tool (`ping.eu`,...)
- ping volgende adressen:
  - 127.0.0.1
  - www.marian.edu
  - telenet.be
  - www.ap.be
- noteer je antwoord op volgende vragen:
  - welke onderdelen spreken voor zichzelf?
  - welke onderdelen zijn je onbekend?
  - zijn er herhalingen? zo ja, waarom?
  - wat lijkt niet te veranderen?
  - wat zou je morgen anders verwachten?
  
---

### DNS

Ping kreeg een adres zoals "www.ap.be". Hoe wist die welk IP-adres hierbij hoort?

> Meer hierover in een volgende les
  
---

### Traceroute

Doe een `traceroute` (Windows: `tracert`) naar:
  - www.marian.edu
  - telenet.be
  - www.ap.be
  
Noteer het antwoord op de volgende vragen:
  - Hoeveel tussenstappen zijn er?
  - Welke stappen zijn iedere keer hetzelfde?
  - Vanaf wanneer begint het te verschillen?
  - Wat gebeurt er met de tijd?
  
note:
Meer hierover in een volgende les

Hoe: 
Windows: open powershell, type `tracert example.org` en duw enter
Linux: open terminal, type `traceroute example.org`

  
---
Installatie-opdrachten:

- [Wireshark](https://www.wireshark.org/)
- [PacketTracer](https://www.netacad.com/cisco-packet-tracer)
  - Dit vereist dat je een account maakt.
