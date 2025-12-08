CI/CD
<aside class="notes">
    <ul>
        <li>allemaal zelfde "C"</li>
        <li>integration: voortdurend afstemmen dmv samenvoegen broncode</li>
        <li>delivery: een volledige build afleveren</li>
        <li>deployment: die build ook in productie plaatsen</li>
    </ul>
</aside>

---

Je hebt net een coole feature gemaakt

Hoe raakt dit in productie?

---

### Optie 1: handmatig

Je connecteert via SSH met de server, doet een git pull en deployed

note:

- kost veel tijd
- veel kans op fouten
- hoe zit 't met je automatische testeb?

---

### Optie 2: scheduled releases

Je wacht. Het bedrijf waarin je werkt maakt elk halfjaar een nieuwe versie


note:

- dit is eerder zeldzaam geworden, maar werd vroeger gebruikt wanneer een nieuwe versie van de CD (!) gedistribueerd werd
- sommige OS doen dit nog, bv "Ubuntu", waar het versienummer (bv: 25.10) verwijst naar het jaar (2025) en de maand (oktober)
	+ Nog steeds backports voor dringende bugfixes via het internet!
- Dit soort release cycles hebben ook typisch een 'codefreeze' aka 'integratieperiode' om te testen

---

### Optie 3

# CI/CD

notes:
- staat voor _Continuous Integration/Continuous Deployment_

---
Pipeline
<img src="./afbeeldingen/ci-cd-flow-desktop.png" />

note:

- de "integration" slaat op het testen en samenbrengen van de verschillende stukken software
	- samenbrengen is bv de dependencies installeren
	- testen: automatische unit tests, maar bv ook of de laatste versie van een dependency niets kapot maakt
- de "delivery" is bv het maken en beschikbaar maken van artefacts (zoals binaries, logs)
	+ eerder voor software die men downloadt
- de "deployment" is het _uitrollen_ van de software,
	+ bv op de webserver
	
---

### Voordelen

- Automatisch, dus goedkoop want geen devtijd meer nodig
- Fixes en features vloeien sneller door
- Korte feedbackloop naar gebruikers
- Je kan ook branches en PRs automatisch bouwen én deployen
	- Testwebsite met nieuwste features kan online beschikbaar gesteld worden voor een testpubliek
	
---

### Wanneer géén CI/CD?

Als de kost van het updaten erg hoog is

Bv: besturingssysteem of programmeertaal

---

### Nadelen

- Kost wat tijd op te zetten
	+ Maar dit is slechts een fractie van wat je ermee uitspaart
- Je moet een buildserver opzetten
	+ Computers zijn vandaag vrij goedkoop
	+ Of waarom er een computer met 256GB RAM in mijn kelder staat (*)
	+ een _cloud_computer huren kan wel oplopen in kost!
	
	
note:

Wel, in de eerste plaats om de planet file te kunnen verwerken. Maar de CI/CD is een leuke bonus!
Soms kan je op ebay koopjes doen (mijn server: 256GB RAM + 6TB HDD = €300)

---


# Hoe?


---

### Git hooks

= Scriptjes met vaste namen in de map `.git/hooks`

note:
https://githooks.com

- pre-commit (kan via exit code commit tegenhouden)
- post-commit
- pre-receive (ook via exit code, maar voor accepteren push)
- post-receive (bv: email uitsturen)


staan (omwille van locatie) <strong>standaard niet</strong> in versiebeheer en dus ook niet gelinkt aan branches
kunnen in allerlei scriptingtalen geschreven zijn (Bash, PowerShell, Python, PHP,...)
kunnen op developermachines staan (dus lokaal), maar ook op remotes
Worden minder gebruikt door de opkomst van 'actions'


---

# Actions

---

Worden door de _forge_ uitgevoerd, op de server

note:
een _forge_ (letterlijk: smeltkroes, smidse) is een website waar men _samen_ aan software werkt

Meest bekende voorbeeld is github

---

### Software-specifiek

Door de _forge_ uitegevoerd -> specifiek voor welke serversoftware je gebruikt

Bv: github gebruikt "Github actions"-bestanden met hun specificatie, deze staan in `.github/workflows`

Github biedt ook gratis rekenkracht aan voor Open-source projecten

note:

niets in het leven is gratis. Waar zit het verdienmodel?

---

### Software-specifiek

Specifieke spec en gratis rekenkracht?

Dit ruikt naar lock-in!

_enter gitea_

---

### Gitea aka Forgejo aka Forgejo

Open-Source alternatief voor Github


- Gitea is het oorspronkelijke pakket
- Werd geforked onder de naam _Forgejo_
- Codeberg e.V. is de VZW die _Forgejo_ ontwikkeld
- Codeberg.org is hun gehoste versie

---

### Waarom een selfhosted versie?

- Onafhankelijk van VS
- Werkt beter (!) dan Github: sneller, minder bloat...
- ... maar een schaamteloze kopie: alles staat op de gekende plaats
- spam is ietwat een probleem (maar: OAUth met externe provider lost dit op)

Kan je zélf hosten
note:
- source.mapcomplete.org is een seflhosted forgejo, login met OSM-account
- er is ook nog Gitlab, maar die gebruik ik niet graag

--- 

### En hoe zit het nu met die actions?

_Ook_ een schaamteloze kloon, een _Github-actions_ werkt (meestal) out of the box
Codeberg.org biedt zelf (gelimiteerde) runners aan


---

# Actions

---

Elke actie wordt beschreven in een yaml-bestand.

Deze staan in `.github/workflows/` of `.forgejo/workflows/`

![](./afbeeldingen/workflows_all.png)

note:
Forgejo gaat _ook_ .github/workflows bekijken

---

Een actie kan bestaan uit verschillende _jobs_

![](./afbeeldingen/workflows_multi_job.png)

---

Via de webinterface kan je de status van de actions zien

![](./afbeeldingen/workflows_interface.png)

---

### Syntax


Eerste blok: _wanneer_ wordt dit uitgevoerd?

```
on:
  workflow_dispatch:
  push:
  schedule:
    - cron: "0 2 * * *"
```

### Syntax

Tweede blok: _jobs_

_Wat_ moet er uitgevoerd worden?

```
jobs:
  <naam>:
    runs-on: [ <voorwaarden, bv: ubuntu-latest> ]
    steps:
      - uses: actions/checkout@v4
      
      - name: <name>
        run: ... bash ...

```

---



<li>wel onder versiebeheer en branchspecifiek, dus goed voor teams</li>
<li>niet de enige tool voor dit soort taken</li>
<li>maar wel dominant: zonder setup geïntegreerd met populaire dienst</li>
<li>gratis voor publieke code (zoals vaker bij Github)</li>
<li>zelf scripten blijft mogelijk, maar er is bijkomende structuur ("kant-en-klare" actions)</li>
<li>runnen standaard in specifieke VM, scripts runnen lokaal en (tenzij ze zelf VM of container
starten) kan resultaat dus verschillen</li>
---
workflows / jobs / steps
<aside class="notes">
    <ul>
        <li>workflow = 1 proces dat doorlopen moet worden</li>
        <li>job = 1 taak binnen dat proces, normaal parallel</li>
        <li>step = 1 stap binnen een job, altijd sequentieel</li>
        <ul>
            <li>steps kunnen scripts of actions (voorverpakte handelingen) zijn</li>
            <li>typische actions kunnen uit soort "app store" gehaald worden</li>
            <li>hoef dan zelf geen volledig script te schrijven</li>
        </ul>
    </ul>
</aside>
---
<section>Opdrachten</section>
<section>Schrijf een Workflow om de tests voor de voorbeeldapplicatie te runnen voor elke commit. Test uit.</section>
<section>Zet de in-memory versie van de gastenboekapplicatie in een Git repository. Zet die op Github. Zorg dat een Docker image gebouwd wordt wanneer je main uitbreidt.</section>
