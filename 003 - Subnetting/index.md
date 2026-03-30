# Subnetting

---

## Wat is subnetting?
Subnetting = een groot netwerk opdelen in kleinere 'subnetten'

---

## Waarom Subnetting?


| Efficiëntie | Beveiliging | Prestaties |
|-------------|------------|------------|
| Voorkomt verspilling van kostbare IP-adressen door netwerken precies op maat te maken. | Houdt verschillende afdelingen gescheiden. _Sales kan niet zomaar bij de servers van IT._ | Vermindert netwerkverkeer (broadcasts) door grote netwerken op te delen in kleinere stukjes. |


---


## Wat is een IP-adres?

<div style="text-align: left; border-left: 4px solid #00cfff; padding: 10px; margin-bottom: 1em;">

#### Digitale Identiteit

Een IP-adres is het **unieke adres** van een apparaat op een netwerk. Vergelijk het met een telefoonnummer: zonder dit adres kan een apparaat niet gevonden worden en geen data uitwisselen.
</div>

*⚠ Elke computer, smartphone en server heeft er één nodig om deel te nemen aan het internet.*

---

## De IPv4 Structuur

<div class="ipv4-structure">

<div class="octet-row">

<div class="octet">
<strong>192</strong><br>
<code>11000000</code><br>
<em>Octet 1</em>
</div>

<div class="dot">.</div>

<div class="octet">
<strong>168</strong><br>
<code>10101000</code><br>
<em>Octet 2</em>
</div>

<div class="dot">.</div>

<div class="octet">
<strong>10</strong><br>
<code>00001010</code><br>
<em>Octet 3</em>
</div>

<div class="dot">.</div>

<div class="octet">
<strong>45</strong><br>
<code>00101101</code><br>
<em>Octet 4</em>
</div>

</div>

<div class="info-row">

<div class="info-box">

**32 Bits Totaal**

<div class="text-small">

Een IPv4-adres bestaat uit exact **32 bits**.  
Deze zijn verdeeld in **4 groepen van 8 bits (octetten)**.

</div>
</div>

<div class="info-box">

**Punten als Scheiding**

<div class="text-small">

We gebruiken **punten** om de octetten te scheiden.  
Dit maakt het adres leesbaar voor mensen.

</div>
</div>

</div>

*Samen vormen deze 4 blokken het volledige adres van een apparaat.*

</div>

---

## Netwerk vs. Host Gedeelte

<div class="network-host">

<div class="intro">
Elk IP-adres in een subnet bestaat altijd uit twee delen:

Een <span class="network">netwerkgedeelte</span> en een  
<span class="host">hostgedeelte</span>.
</div>

<div class="two-columns">

<div class="card">

### Netwerk Gedeelte

Identificeert het **netwerk** zelf.  
Alle apparaten in hetzelfde subnet hebben hetzelfde netwerkgedeelte.

</div>

<div class="card">

### Host Gedeelte

Identificeert het **unieke apparaat** binnen dat netwerk.

</div>

</div>

|            | Waarde |
|------------|-------|
| IP-adres | **192.168.10.<span class="host">45</span>** |
| Subnetmasker | **255.255.255.<span class="host">0</span>** |

</div>

---

## Het Subnetmasker

> Het subnetmasker is de **scheidsrechter**.  
> Het bepaalt welk deel van het IP-adres bij het **netwerk** hoort en welk deel bij de **host**.

> Zonder masker is een IP-adres slechts een getal.  
> Het masker geeft de **context** die nodig is om te routeren.

<div class="example">

**Voorbeeld: /24 → 255.255.255.0**

</div>

---

## Het Hostgedeelte

<div class="binary-box">

**IP-ADRES:**  
<span class="network">192.168.1.</span><span class="host">45</span>

`11000000 . 10101000 . 00000001 . 00101101`

**SUBNETMASKER:**  
<span class="network">255.255.255.</span><span class="host">0</span>

`11111111 . 11111111 . 11111111 . 00000000`

</div>

De <span class="host">rode 0-bits</span> in het subnetmasker geven het **hostgedeelte** aan.

Deze bits kunnen waarden aannemen van:

`192.168.1.1 t.e.m 192.168.1.254`

---

## Het Netwerkgedeelte

De <span class="network">blauwe 1-bits</span> in het subnetmasker bepalen het **netwerkgedeelte**.

In dit voorbeeld: `192.168.1`

Alle apparaten in hetzelfde netwerk delen dit gedeelte.


---


## Speciale Adressen

**Voorbeeld Netwerk:** `192.168.1.0 / 24`

| Type | Adres |
|-----|------|
| Subnetmasker | 255.255.255.0 |
| Netwerkadres (alle hostbits op 0) | 192.168.1.0 |
| Broadcastadres (alle hostbits op 1) | 192.168.1.255 |
| Bruikbaar bereik | 192.168.1.1 – 192.168.1.254 |
| Aantal hosts | 2⁸ − 2 = **254** |

---

## Stappenplan

1. **Binaire voorstelling**
   Schrijf IP-adres en subnetmasker volledig binair uit.

2. **Netwerkadres bepalen**
   Zet alle **host-bits op 0**.

3. **Broadcastadres bepalen**
   Zet alle **host-bits op 1**.

4. **Aantal hosts**: `2^n - 2`


5. **Bruikbaar bereik**
Alle adressen tussen netwerk- en broadcastadres.

---

## Oefening 1

Analyseer dit netwerk:


IP: 192.168.1.45
Mask: 255.255.255.0


Wat moet je bepalen:

- Netwerkadres  
- Broadcastadres  
- Aantal bruikbare hosts  
- Bruikbaar bereik

---

## Oplossing Oefening 1

**Stap 1 – Binaire voorstelling**


IP: 11000000.10101000.00000001.00101101
Mask: 11111111.11111111.11111111.00000000


**Stap 2 – Netwerkadres**


11000000.10101000.00000001.00000000


Resultaat:


192.168.1.0


**Stap 3 – Broadcastadres**


11000000.10101000.00000001.11111111


Resultaat:


192.168.1.255


**Stap 4 – Hosts**


2^8 – 2 = 254


**Stap 5 – Bereik**


192.168.1.1 – 192.168.1.254


---

## Oefening 2


IP: 172.16.45.10
Mask: 255.255.240.0


Bepaal:

- Netwerkadres  
- Broadcastadres  
- Hosts  
- Bereik

---

## Oplossing Oefening 2

Netwerkadres:


172.16.32.0


Broadcastadres:


172.16.47.255


Hosts:


2^12 – 2 = 4094


Bereik:


172.16.32.1 – 172.16.47.254


---

## Oefening 3


IP: 192.168.3.222
Mask: 255.255.64.0


Bepaal opnieuw:

- Netwerkadres  
- Broadcastadres  
- Hosts  
- Bereik
