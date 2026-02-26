<section>

# Subnetting
</section>

<section>

## Wat is subnetting?
Subnetting = een groot netwerk opdelen in kleinere 'subnetten'
</section>

<section>

## Waarom Subnetting?

<div style="font-size: 1.8rem;">

| Efficiëntie | Beveiliging | Prestaties |
|-------------|------------|------------|
| Voorkomt verspilling van kostbare IP-adressen door netwerken precies op maat te maken. | Houdt verschillende afdelingen gescheiden. _Sales kan niet zomaar bij de servers van IT._ | Vermindert netwerkverkeer (broadcasts) door grote netwerken op te delen in kleinere stukjes. |

</div>
</section>

<section>

## Wat is een IP-adres?

<div style="text-align: left; border-left: 4px solid #00cfff; padding: 10px; margin-bottom: 1em;">

#### Digitale Identiteit
Een IP-adres is het **unieke adres** van een apparaat op een netwerk. Vergelijk het met een telefoonnummer: zonder dit adres kan een apparaat niet gevonden worden en geen data uitwisselen.
</div>

*⚠ Elke computer, smartphone en server heeft er één nodig om deel te nemen aan het internet.*
</section>

<section>

## De IPv4 Structuur

<div style="font-size:1.6rem; line-height:1.2;">

<div style="display:flex; gap:20px; text-align:center; margin-bottom:20px;">

<div style="flex:1; border: 2px solid #00cfff; padding:10px;">

**192**<br>`11000000`<br>_Octet 1_
</div>
<div style="display:flex; align-items:center; justify-content:center; width:20px; font-size:70px;">.</div>
<div style="flex:1; border: 2px solid #00cfff; padding:10px;">

**168**<br>`10101000`<br>_Octet 2_
</div>
<div style="display:flex; align-items:center; justify-content:center; width:20px; font-size:70px;">.</div>
<div style="flex:1; border: 2px solid #00cfff; padding:10px;">

**10**<br>`00001010`<br>_Octet 3_
</div>
<div style="display:flex; align-items:center; justify-content:center; width:20px; font-size:70px;">.</div>
<div style="flex:1; border: 2px solid #00cfff; padding:10px;">

**45**<br>`00101101`<br>_Octet 4_
</div>

</div>

<div style="display:flex; gap:20px;">
<div style="flex:1; border-left:4px solid #f1c40f; padding:10px;">

**32 Bits Totaal**
<div class="text-small">

Een IPv4-adres bestaat uit exact **32 bits**. Deze zijn verdeeld in 4 groepen van 8 bits (octetten).
</div>
</div>

<div style="flex:1; border-left:4px solid #f1c40f; padding:10px;">

**Punten als Scheiding**
<div class="text-small">

We gebruiken **punten** om de octetten te scheiden. Dit maakt het adres leesbaar voor mensen, zowel decimaal als binair.
</div>
</div>
</div>

*Samen vormen deze 4 blokken het volledige adres van een apparaat.*
</div>
</section>

<section>

## Netwerk vs. Host Gedeelte

<div style="font-size:1.8rem; line-height:1.2;">
  <div style="padding: 1em 1.4em; font-size: 0.85em; text-align: center; border-radius: 4px;">
    Elk IP-adres in een subnet bestaat altijd uit twee delen: 
    <div style="text-align: center;">	
      Een <span style="color: #00bcd4; font-weight: bold;">netwerkgedeelte</span> en een
      <span style="color: #e53935; font-weight: bold;">hostgedeelte</span>.
    </div>
  </div>

  <div style="display: flex; gap: 2em; margin-top: 1em;">
    <div style="flex: 1; border-left: 5px solid #f5a623;border-radius: 6px; padding: 1.2em; text-align: left; font-size: 0.75em;">
      <h2 style="color: #00bcd4; font-size: 1.1em; margin: 0 0 0.5em; text-transform: none;">Netwerk Gedeelte</h2>
      Identificeert het <strong>netwerk</strong> zelf. Alle apparaten in hetzelfde subnet hebben exact hetzelfde netwerkgedeelte.
    </div>
    <div style="flex: 1; border-left: 5px solid #f5a623;border-radius: 6px; padding: 1.2em; text-align: left; font-size: 0.75em;">
      <h2 style="color: #e53935; font-size: 1.1em; margin: 0 0 0.5em; text-transform: none;">Host Gedeelte</h2>
      Identificeert het <strong>unieke apparaat</strong> binnen dat netwerk. Dit moet voor elke host anders zijn.
    </div>
  </div>

  <table style="margin: 1.5em auto 0; width: 70%; border-collapse: collapse; font-size: 0.8em;">
    <tr>
      <td style="padding: 0.5em 1em; border-bottom: 1px solid #333; color: #aaa; text-align: right; text-transform: uppercase; letter-spacing: 0.1em; font-size: 0.85em;">IP-adres</td>
      <td style="padding: 0.5em 1em; border-bottom: 1px solid #333; color: #00bcd4; font-size: 1.4em; font-weight: bold;">192.168.10.<span style="color: #e53935;">45</span></td>
    </tr>
    <tr>
      <td style="padding: 0.5em 1em; color: #aaa; text-align: right; text-transform: uppercase; letter-spacing: 0.1em; font-size: 0.85em;">Subnetmasker</td>
      <td style="padding: 0.5em 1em; color: #00bcd4; font-size: 1.4em; font-weight: bold;">255.255.255.<span style="color: #e53935;">0</span></td>
    </tr>
  </table>
</div>
</section>

<section>

## Het Subnetmasker

<div style="border-left: 5px solid #00bcd4; padding: 1em 1.4em; font-size: 0.85em; text-align: left; border-radius: 4px; margin-bottom: 1em;">
Het subnetmasker is de <span style="color: #00bcd4; font-weight: bold;">scheidsrechter</span>. Het vertelt de computer welk deel van het IP-adres bij het netwerk hoort en welk deel bij de host.
</div>

<div style="border-left: 5px solid #00bcd4; padding: 1em 1.4em; font-size: 0.85em; text-align: left; border-radius: 4px; margin-bottom: 1.5em;">
Zonder masker is een IP-adres slechts een getal. Het masker geeft de <span style="color: #00bcd4; font-weight: bold;">context</span> die nodig is om te routeren.
</div>

<div style="border-radius: 6px; padding: 1em; text-align: center;">
<strong style="font-size: 1.4em;">Voorbeeld: /24 → 255.255.255.0</strong>
</div>
</section>
<section>

## Het Hostgedeelte
<div style="font-size:1.6rem; line-height:1.2;">

<div style="border: 2px solid #e53935; padding: 1em; border-radius: 6px; margin-bottom: 1em;">
<div style="font-size:2rem;font-weight:bold">
IP-ADRES: <span style="color: #00bcd4;">192.168.1.</span><span style="color: #e53935;">45</span>
</div>
<div style="font-family: monospace; font-size: 1.4em; color: #00bcd4;">
11000000 . 10101000 . 00000001 . <span style="color: #e53935;">00101101</span>
</div>
<br/>
<div style="font-size:2rem;font-weight:bold">
SUBNETMASKER: <span style="color: #00bcd4;">255.255.255.</span><span style="color: #e53935;">0</span>
</div>
<div style="font-family: monospace; font-size: 1.4em; color: #00bcd4;">
11111111 . 11111111 . 11111111 . <span style="color: #e53935;">00000000</span>
</div>
</div>

<div style="border-left: 4px solid #e53935; padding: 0.8em 1.2em; border-radius: 4px;">

De <span style="color: #e53935;">rode '0'-bits</span> in het subnetmasker geven het hostgedeelte aan.
In dit voorbeeld zijn dat de laatste 8 bits van het IP-adres.

Deze bits kunnen elk getal van 1 tot 254 aannemen (0 = netwerk, 255 = broadcast en tellen daarom niet mee), waardoor elk apparaat in hetzelfde netwerk een uniek IP-adres krijgt van:
192.168.1.1 t.e.m 192.168.1.254
</div>
</div>
</section>
<section>

## Het Netwerkgedeelte
<div style="font-size:1.6rem; line-height:1.2;">

<div style="border: 2px solid #e53935; padding: 1em; border-radius: 6px; margin-bottom: 1em;">
<div style="font-size:2rem;font-weight:bold">
IP-ADRES: <span style="color: #00bcd4;">192.168.1.</span><span style="color: #e53935;">45</span>
</div>
<div style="font-family: monospace; font-size: 1.4em; color: #00bcd4;">
11000000 . 10101000 . 00000001 . <span style="color: #e53935;">00101101</span>
</div>
<br/>
<div style="font-size:2rem;font-weight:bold">
SUBNETMASKER: <span style="color: #00bcd4;">255.255.255.</span><span style="color: #e53935;">0</span>
</div>
<div style="font-family: monospace; font-size: 1.4em; color: #00bcd4;">
11111111 . 11111111 . 11111111 . <span style="color: #e53935;">00000000</span>
</div>

</div>

<div style="border-left: 4px solid #e53935; padding: 0.8em 1.2em; border-radius: 4px;">

De <span style="color: #00bcd4;">blauwe '1'-bits</span> in het subnetmasker bepalen welk deel van het IP-adres bij het <span style="color: #00bcd4;">netwerk</span> hoort.
In dit voorbeeld zijn dat de eerste 24 bits (192.168.1).

Deze bits blijven voor alle apparaten gelijk in hetzelfde netwerk, zodat ze tot hetzelfde netwerk behoren. Alleen het hostgedeelte (de rode 0-bits) verandert per apparaat.

</div>
</div>
</section>
<section>

## Cruciale Adressen
<div style="font-size:1.2rem; line-height:1.2;">

<div style="border: 2px solid #f5a623; border-radius: 8px; text-align: center; padding: 0.7em 1em; margin-bottom: 1.5em; font-size: 1.4rem; font-weight: 700;">
  <span style="color: #000000;">Voorbeeld Netwerk: </span><span style="color: #f5a623;">192.168.1.0 / 24</span>
</div>

<div style="border-radius: 10px; padding: 1.2em 1.8em; margin-bottom: 1.5em;">

  <div style="display: flex; align-items: center; gap: 2em; padding: 0.8em 0; border-bottom: 1px solid #cccccc;">
    <span style="font-weight: 700; color: #000000; min-width: 180px;">Subnetmasker</span>
    <span style="color: #00bcd4; font-weight: 700; font-size: 1.1rem; min-width: 160px;">255.255.255.<span style="color: #e53935; font-weight: 700; font-size: 1.1rem; min-width: 160px;">0</span></span>
    <span style="font-family: monospace; font-size: 0.95rem;">
      <span style="color: #00bcd4;">11111111.11111111.11111111.</span><span style="color: #e53935;">00000000</span>
    </span>
  </div>

  <div style="display: flex; align-items: center; gap: 2em; padding: 0.8em 0; border-bottom: 1px solid #cccccc;">
    <span style="font-weight: 700; color: #000000; min-width: 180px;">Netwerkadres</span>
    <span style="color: #00bcd4; font-weight: 700; font-size: 1.1rem; min-width: 160px;">192.168.1.<span style="color: #e53935; font-weight: 700; font-size: 1.1rem; min-width: 160px;">0</span></span>
    <span style="font-family: monospace; font-size: 0.95rem;">
      <span style="color: #00bcd4;">11000000.10101000.00000001.</span><span style="color: #e53935;">00000000</span>
    </span>
  </div>

  <div style="display: flex; align-items: center; gap: 2em; padding: 0.8em 0; border-bottom: 1px solid #cccccc;">
    <span style="font-weight: 700; color: #000000; min-width: 180px;">Broadcastadres</span>
    <span style="color: #00bcd4; font-weight: 700; font-size: 1.1rem; min-width: 160px;">192.168.1.<span style="color: #e53935; font-weight: 700; font-size: 1.1rem; min-width: 160px;">255</span></span>
    <span style="font-family: monospace; font-size: 0.95rem;">
      <span style="color: #00bcd4;">11000000.10101000.00000001.</span><span style="color: #e53935;">11111111</span>
    </span>
  </div>

  <div style="display: flex; align-items: center; gap: 2em; padding: 0.8em 0;">
    <span style="font-weight: 700; color: #000000; min-width: 180px;">Bruikbaar Bereik</span>
    <span style="font-weight: 700; font-size: 1.1rem; min-width: 160px;">192.168.1.1 t/m 192.168.1.254</span>
    <span style="font-family: monospace; font-size: 0.95rem;">
      <span style="color: #aaaaaa;">....</span><span style="color: #4caf50;">00000001</span>
      <span style="color: #000000; font-weight: bold; margin: 0 0.4em;">t/m</span>
      <span style="color: #aaaaaa;">....</span><span style="color: #4caf50;">11111110</span>
    </span>
  </div>

  <div style="display: flex; align-items: center; gap: 2em; padding: 0.8em 0;">
    <span style="font-weight: 700; color: #000000; min-width: 180px;">Aantal hosts</span>
    <span style="font-weight: 700; font-size: 1.1rem; min-width: 160px;">2^n - 2 (n = host bits)</span>
    <span style="font-family: monospace; font-size: 0.95rem;">
      <span style="color: #f5a623;">2^8 - 2 = 256 - 2 = 254</span>
    </span>
  </div>

</div>

<div style="display: flex; gap: 2em;">

  <div style="flex: 1; border-top: 3px solid #00bcd4; padding-top: 0.8em;">
    <div style="color: #00bcd4; font-weight: 700; margin-bottom: 0.3em;">Netwerkadres</div>
    <div style="font-size: 0.9rem; color: #000000;">Alle host-bits op <span style="color: #e53935;">0</span>. Identificeert de groep.</div>
  </div>

  <div style="flex: 1; border-top: 3px solid #e53935; padding-top: 0.8em;">
    <div style="color: #e53935; font-weight: 700; margin-bottom: 0.3em;">Broadcastadres</div>
    <div style="font-size: 0.9rem; color: #000000;">Alle host-bits op <span style="color: #e53935;">1</span>. Bereikt iedereen.</div>
  </div>

  <div style="flex: 1; border-top: 3px solid #4caf50; padding-top: 0.8em;">
    <div style="color: #4caf50; font-weight: 700; margin-bottom: 0.3em;">Bruikbaar Bereik</div>
    <div style="font-size: 0.9rem; color: #000000;">Alles <span style="color: #4caf50;">tussenin</span> is voor je apparaten.</div>
  </div>
  <div style="flex: 1; border-top: 3px solid #f5a623; padding-top: 0.8em;">
    <div style="color: #f5a623; font-weight: 700; margin-bottom: 0.3em;">Aantal hosts</div>
    <div style="font-size: 0.9rem; color: #000000;"><span style="color: #f5a623;">Aantal</span> IP-adressen in je bruikbaar bereik</div>
  </div>
</div>
</div>
</section>
<section>
  <h2>Stappenplan</h2>

  <!-- Steps grid -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.8rem;margin-bottom:.8rem;">
    <div style="border-left:4px solid #e53935;border-radius:6px;padding:1rem 1.2rem;display:flex;gap:1rem;align-items:flex-start;text-align:left;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.8rem;font-weight:700;color:#e53935;min-width:36px;line-height:1;">01</div>
      <div>
        <div style="font-family:'Rajdhani',sans-serif;font-size:1.1rem;font-weight:700;color:#00cfff;margin-bottom:.3rem;text-transform:uppercase;letter-spacing:1px;">Binaire Voorstelling</div>
        <div style="font-size:1rem;line-height:1.5">Schrijf zowel het <strong>IP-adres</strong> als het <strong>subnetmasker</strong> volledig binair uit (32 bits).</div>
      </div>
    </div>
    <div style="border-left:4px solid #e53935;border-radius:6px;padding:1rem 1.2rem;display:flex;gap:1rem;align-items:flex-start;text-align:left;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.8rem;font-weight:700;color:#e53935;min-width:36px;line-height:1;">02</div>
      <div>
        <div style="font-family:'Rajdhani',sans-serif;font-size:1.1rem;font-weight:700;color:#00cfff;margin-bottom:.3rem;text-transform:uppercase;letter-spacing:1px;">Netwerkadres</div>
        <div style="font-size:1rem;line-height:1.5">Behoud alle bits in het netwerkgedeelte. Zet <strong>alle bits in het hostgedeelte op 0</strong>.</div>
      </div>
    </div>
    <div style="border-left:4px solid #e53935;border-radius:6px;padding:1rem 1.2rem;display:flex;gap:1rem;align-items:flex-start;text-align:left;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.8rem;font-weight:700;color:#e53935;min-width:36px;line-height:1;">03</div>
      <div>
        <div style="font-family:'Rajdhani',sans-serif;font-size:1.1rem;font-weight:700;color:#00cfff;margin-bottom:.3rem;text-transform:uppercase;letter-spacing:1px;">Broadcastadres</div>
        <div style="font-size:1rem;line-height:1.5">Behoud het netwerkgedeelte. Zet nu <strong>alle bits in het hostgedeelte op 1</strong>.</div>
      </div>
    </div>
    <div style="border-left:4px solid #e53935;border-radius:6px;padding:1rem 1.2rem;display:flex;gap:1rem;align-items:flex-start;text-align:left;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.8rem;font-weight:700;color:#e53935;min-width:36px;line-height:1;">04</div>
      <div>
        <div style="font-family:'Rajdhani',sans-serif;font-size:1.1rem;font-weight:700;color:#00cfff;margin-bottom:.3rem;text-transform:uppercase;letter-spacing:1px;">Aantal Hosts</div>
        <div style="font-size:1rem;line-height:1.5">Formule: <strong style="color:#e53935;">2<sup>n</sup> – 2</strong>. We trekken er 2 af omdat het netwerk- en broadcastadres niet bruikbaar zijn voor hosts.</div>
      </div>
    </div>

  </div>
  <div style="width:50%;margin-bottom:.8rem;">
    <div style="border-left:4px solid #e53935;border-radius:6px;padding:1rem 1.2rem;display:flex;gap:1rem;align-items:flex-start;text-align:left;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.8rem;font-weight:700;color:#e53935;min-width:36px;line-height:1;">05</div>
      <div>
        <div style="font-family:'Rajdhani',sans-serif;font-size:1.1rem;font-weight:700;color:#00cfff;margin-bottom:.3rem;text-transform:uppercase;letter-spacing:1px;">Bruikbaar Bereik</div>
        <div style="font-size:1rem;line-height:1.5">Alle adressen <strong>tussen</strong> het netwerkadres en het broadcastadres zijn bruikbaar voor hosts.</div>
      </div>
    </div>
  </div>
  <div style="display:flex;border:1.5px dashed #f5a623;border-radius:6px;overflow:hidden;">
    <div style="flex:1;padding:.6rem 1rem;text-align:center;border-right:1px solid #2e3a50;">
      <div style="color:#f5a623;font-weight:700;font-size:.75rem;letter-spacing:.1em;margin-bottom:.2rem;">TIP 1</div>
      <div style="font-size:1rem">Het masker bepaalt de grens.</div>
    </div>
    <div style="flex:1;padding:.6rem 1rem;text-align:center;border-right:1px solid #2e3a50;">
      <div style="color:#f5a623;font-weight:700;font-size:.75rem;letter-spacing:.1em;margin-bottom:.2rem;">TIP 2</div>
      <div style="font-size:1rem">Netwerkadres = Eerste adres.</div>
    </div>
    <div style="flex:1;padding:.6rem 1rem;text-align:center;">
      <div style="color:#f5a623;font-weight:700;font-size:.75rem;letter-spacing:.1em;margin-bottom:.2rem;">TIP 3</div>
      <div style="font-size:1rem">Broadcastadres = Laatste adres.</div>
    </div>
  </div>
</section>
<section>

  <!-- Title with dashed bottom border -->
  <div>
    <h2>Oefening 1</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Analyseer dit netwerk:</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        IP: <span style="color:#00cfff;">192.168.1.45</span>
      </div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;">
        Mask: <span style="color:#00cfff;">255.255.255.0</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Wat moet je bepalen?</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Netwerkadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Broadcastadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Aantal bruikbare hosts</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Het bruikbare bereik</li>
      </ul>
    </div>

  </div>

  <!-- Tip -->
  <p style="margin-top:1.5rem;font-style:italic;color:#8899aa;font-size:1.45rem;">Tip: Gebruik het stappenplan uit de vorige slides!</p>

</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 1</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 192.168.1.45: <span style="color:#00cfff;">11000000.10101000.00000001.</span><span style="color:#e53935;">00101101</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.255.255.0: <span style="color:#00cfff;">11111111.11111111.11111111.</span><span style="color:#e53935;">00000000</span>
    </div>
  </div>

  <!-- Stap 2 + 3: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;margin-bottom:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 2: Netwerkadres</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">11000000.10101000.00000001.</span><span style="color:#e53935;">00000000</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#00cfff;">192.168.1.0</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 3: Broadcastadres</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">11000000.10101000.00000001.</span><span style="color:#e53935;">11111111</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#e53935;">192.168.1.255</strong></div>
    </div>

  </div>

  <!-- Stap 4 + 5: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 4: Aantal Hosts</div>
      <div style="text-align:left;font-size:1.3rem">8 host-bits → 2<sup>8</sup> – 2 = <strong>254 hosts</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 5: Bruikbaar Bereik (Range)</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>192.168.1.1 t/m 192.168.1.254</strong>
      </div>
    </div>

  </div>

</section>
<section>

  <!-- Title with dashed bottom border -->
  <div>
    <h2>Oefening 2</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Analyseer dit netwerk:</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        IP: <span style="color:#00cfff;">172.16.45.10</span>
      </div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;">
        Mask: <span style="color:#00cfff;">255.255.240.0</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Wat moet je bepalen?</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Netwerkadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Broadcastadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Aantal bruikbare hosts</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Het bruikbare bereik</li>
      </ul>
    </div>

  </div>

  <!-- Tip -->
  <p style="margin-top:1.5rem;font-style:italic;color:#8899aa;font-size:1.45rem;">Tip: Gebruik het stappenplan uit de vorige slides!</p>

</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 2</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 172.16.45.10: <span style="color:#00cfff;">10101100.00010000.0010</span><span style="color:#e53935;">1101.00001010</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.255.240.0: <span style="color:#00cfff;">11111111.11111111.1111</span><span style="color:#e53935;">0000.00000000</span>
    </div>
  </div>

  <!-- Stap 2 + 3: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;margin-bottom:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 2: Netwerkadres</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">10101100.00010000.0010</span><span style="color:#e53935;">0000.00000000</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#00cfff;">172.16.32.0</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 3: Broadcastadres</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">10101100.00010000.0010</span><span style="color:#e53935;">1111.11111111</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#e53935;">172.16.47.255</strong></div>
    </div>

  </div>

  <!-- Stap 4 + 5: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 4: Aantal Hosts</div>
      <div style="text-align:left;font-size:1.3rem">12 host-bits → 2<sup>12</sup> – 2 = <strong>4094 hosts</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 5: Bruikbaar Bereik (Range)</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>172.16.32.1 t/m 172.16.47.254</strong>
      </div>
    </div>

  </div>

</section>
<section>

  <!-- Title with dashed bottom border -->
  <div>
    <h2>Oefening 3</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Analyseer dit netwerk:</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        IP: <span style="color:#00cfff;">192.168.3.222</span>
      </div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;">
        Mask: <span style="color:#00cfff;">255.255.64.0</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Wat moet je bepalen?</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Netwerkadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Broadcastadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Aantal bruikbare hosts</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Het bruikbare bereik</li>
      </ul>
    </div>

  </div>

  <!-- Tip -->
  <p style="margin-top:1.5rem;font-style:italic;color:#8899aa;font-size:1.45rem;">Tip: Gebruik het stappenplan uit de vorige slides!</p>

</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 3</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 192.168.3.222: 11000000.10101000.00000011.11011110
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.255.64.0: <span style="color:#00cfff;">11111111.11111111.</span><span style="color:#e53935;"><u>0</u></span><span style="color:#00cfff;">1</span><span style="color:#e53935;">000000.00000000</span>
    </div>
  </div>

  <!-- Stap 2 + 3: two columns -->
  <div style="display:grid;grid-template-columns:1fr;gap:.7rem;margin-bottom:.7rem;">
    <div style="border-left:4px solid #e53935;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#e53935;font-size:1.3rem;margin-bottom:.5rem;">Conclusie: Ongeldig!!</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        Een subnetmasker moet <b><u>altijd</u></b> een ononderbroken reeks van <span style="color:#00cfff;">1-en</span> zijn, gevolgd door een ononderbroken reeks van <span style="color:#e53935;">0-en</span>.
      </div>
      <div style="text-align:left;font-size:1.3rem;">In dit masker staat er een <strong style="color:#e53935;">0</strong> tussen de <span style="color:#00cfff;">1-en</span> in het derde octet. Dit kan technisch niet!!</div>
    </div>
  </div>
  </div>

</section>
<section>
  <div>
    <h2>Oefening 4: Validatie</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Is dit een geldig netwerkadres?</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        IP: <span style="color:#00cfff;">192.168.10.16</span>
      </div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;">
        Mask: <span style="color:#00cfff;">255.255.255.240</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Wat moet je bepalen?</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Schrijf ip en subnetmask binair</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Controleer of host-bits in ip adres op 0 staan</li>
      </ul>
    </div>

  </div>

  <!-- Tip -->
  <p style="margin-top:1.5rem;font-style:italic;color:#8899aa;font-size:1.45rem;">Tip: Gebruik het stappenplan uit de vorige slides!</p>

</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 4</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 192.168.10.16: <span style="color:#00cfff;">11000000.10101000.00001010.0001</span><span style="color:#e53935;">0000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.255.255.240: <span style="color:#00cfff;">11111111.11111111.11111111.1111</span><span style="color:#e53935;">0000</span>
    </div>
  </div>
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 2: Controleer of host-bits op 0 staan</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        Het subnetmasker heeft <span style="color:#e53935;">28  netwerk-bits</span>. De laatste <span style="color:#e53935;"> 4 bits</span> zijn voor de hosts. Deze bits staan allemaal op 0 in het IP 192.168.10.16.
      </div>
      <div style="text-align:left;font-size:1.3rem;">Conclusie: <strong style="color:#4caf50;">Dit is een geldig netwerkadres!</strong></div>
    </div>

</section>
<!-- Title with dashed bottom border -->
<section>
  <div>
    <h2>Oefening 5: Validatie</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Is dit een geldig netwerkadres?</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        IP: <span style="color:#00cfff;">10.0.0.128</span>
      </div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;">
        Mask: <span style="color:#00cfff;">255.255.255.192</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Wat moet je bepalen?</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Schrijf ip en subnetmask binair</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Controleer of host-bits in ip adres op 0 staan</li>
      </ul>
    </div>

  </div>

  <!-- Tip -->
  <p style="margin-top:1.5rem;font-style:italic;color:#8899aa;font-size:1.45rem;">Tip: Gebruik het stappenplan uit de vorige slides!</p>

</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 5</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 10.0.0.128: <span style="color:#00cfff;">00001010.00000000.00000000.10</span><span style="color:#e53935;">000000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.255.255.192: <span style="color:#00cfff;">11111111.11111111.11111111.11</span><span style="color:#e53935;">000000</span>
    </div>
  </div>
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 2: Controleer of host-bits op 0 staan</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        Het subnetmasker heeft <span style="color:#e53935;">26  netwerk-bits</span>. De laatste <span style="color:#e53935;"> 6 bits</span> zijn voor de hosts. Deze bits staan allemaal op 0 in het IP 10.0.0.128.
      </div>
      <div style="text-align:left;font-size:1.3rem;"><strong>Conclusie: </strong><strong style="color:#4caf50;">Dit is een geldig netwerkadres!</strong></div>
    </div>

</section>
<!-- Title with dashed bottom border -->
<section>
  <div>
    <h2>Oefening 6: Validatie</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Is dit een geldig netwerkadres?</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        IP: <span style="color:#00cfff;">192.168.1.10</span>
      </div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;">
        Mask: <span style="color:#00cfff;">255.255.255.240</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Wat moet je bepalen?</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Schrijf ip en subnetmask binair</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Controleer of host-bits in ip adres op 0 staan</li>
      </ul>
    </div>

  </div>

  <!-- Tip -->
  <p style="margin-top:1.5rem;font-style:italic;color:#8899aa;font-size:1.45rem;">Tip: Gebruik het stappenplan uit de vorige slides!</p>

</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 6</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 192.168.1.10: <span style="color:#00cfff;">11000000.10101000.00000001.0000</span><span style="color:#e53935;">1010</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.255.255.240: <span style="color:#00cfff;">11111111.11111111.11111111.1111</span><span style="color:#e53935;">0000</span>
    </div>
  </div>
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 2: Controleer of host-bits op 0 staan</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        Het subnetmasker heeft <span style="color:#e53935;">28  netwerk-bits</span>. De laatste <span style="color:#e53935;"> 4 bits</span> zijn voor de hosts. Deze bits staan NIET allemaal op 0 in het IP 192.168.1.10.
      </div>
      <div style="text-align:left;font-size:1.3rem;"><strong>Conclusie: </strong><strong style="color:#e53935;">Dit is GEEN geldig netwerkadres!</strong></div>
    </div>

</section>
<section>
  <div>
    <h2>Oefening 7: Subnet Hiërarchie</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Is A een subnet van B</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        Netwerk A: <span style="color:#00cfff;">192.168.1.128 / 26</span>
      </div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;">
        Netwerk B: <span style="color:#00cfff;">192.168.1.0 / 24</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Stappenplan:</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">1</span>Vergelijk subnetmaskers. Indien aantal netwerk bits netwerk A >= aantal netwerk bits netwerk B, ga naar stap 2. Anders, GEEN SUBNET!</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">2</span>Bepaal het bereik van netwerk A</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">3</span>Bepaal het bereik van netwerk B.</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">4</span>Valt A volledig binnen B ? Dan is netwerk A een subnet van netwerk B. Anders niet!</li>
      </ul>
    </div>

  </div>
</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 7 (Deel 1)</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Vergelijk subnetmaskers of hostbits</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      Mask Netwerk A: /26: <span style="color:#00cfff;">11111111.11111111.11111111.11</span><span style="color:#e53935;">000000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask Netwerk B: /24: <span style="color:#00cfff;">11111111.11111111.11111111.</span><span style="color:#e53935;">00000000</span>
    </div>
    <div style="text-align:left;font-size:1.3rem;"><strong>Conclusie: A is kleiner dan B (26 >= 24), dus we gaan naar stap 2.</strong></div>
  </div>
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 2: We berekenen bereik netwerk A: We nemen het subnetmasker van stap 1 over.</div>
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 192.168.1.128:  <span style="color:#00cfff;">11000000.10101000.00000001.10</span><span style="color:#e53935;">000000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.255.255.192: <span style="color:#00cfff;">11111111.11111111.11111111.11</span><span style="color:#e53935;">000000</span>
    </div>
  </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Netwerkadres netwerk A:</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">11000000.10101000.00000001.10</span><span style="color:#e53935;">000000</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#00cfff;">192.168.1.128</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Broadcastadres netwerk A</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">11000000.10101000.00000001.10</span><span style="color:#e53935;">111111</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#e53935;">192.168.1.191</strong></div>
    </div>
  </div>
  </div>

  <!-- Stap 4 + 5: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Aantal Hosts netwerk A</div>
      <div style="text-align:left;font-size:1.3rem">6 host-bits → 2<sup>6</sup> – 2 = <strong>62 hosts</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Bruikbaar Bereik (Range) Netwerk A</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>192.168.1.129 – 192.168.1.190</strong>
      </div>
    </div>

  </div>
</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 7 (Deel 2)</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 3: We berekenen bereik netwerk B: We nemen het subnetmasker van stap 1 over.</div>
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 192.168.1.0:  <span style="color:#00cfff;">11000000.10101000.00000001.</span><span style="color:#e53935;">00000000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.255.255.0: <span style="color:#00cfff;">11111111.11111111.11111111.</span><span style="color:#e53935;">00000000</span>
    </div>
  </div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Netwerkadres netwerk B:</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">11000000.10101000.00000001.</span><span style="color:#e53935;">00000000</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#00cfff;">192.168.1.0</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Broadcastadres netwerk B</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">11000000.10101000.00000001.</span><span style="color:#e53935;">11111111</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#e53935;">192.168.1.255</strong></div>
    </div>

  </div>
  </div>
  <!-- Stap 4 + 5: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Aantal Hosts netwerk B</div>
      <div style="text-align:left;font-size:1.3rem">8 host-bits → 2<sup>8</sup> – 2 = <strong>254 hosts</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Bruikbaar Bereik (Range) Netwerk B</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>192.168.1.1 – 192.168.1.254</strong>
      </div>
    </div>

  </div>
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 4: Valt bereik A volledig binnen bereik B?</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        Bereik A: <strong>192.168.1.129 – 192.168.1.190</strong>
      </div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        Bereik B: <strong>192.168.1.1 – 192.168.1.254</strong>
      </div>
      <div style="text-align:left;font-size:1.3rem;"><strong>Conclusie: Bereik netwerk A valt binnen netwerk B:</strong><strong style="color:#4caf50;"> Netwerk A is een subnet van Netwerk B!</strong></div>
  </div>
</section>
<section>
  <div>
    <h2>Oefening 8: Subnet Hiërarchie</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Is A een subnet van B</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        Netwerk A: <span style="color:#00cfff;">172.32.0.0 / 16</span>
      </div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;">
        Netwerk B: <span style="color:#00cfff;">172.16.0.0 / 12</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Stappenplan:</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">1</span>Vergelijk subnetmaskers. Indien aantal netwerk bits netwerk A >= aantal netwerk bits netwerk B, ga naar stap 2. Anders, GEEN SUBNET!</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">2</span>Bepaal het bereik van netwerk A</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">3</span>Bepaal het bereik van netwerk B.</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">4</span>Valt A volledig binnen B ? Dan is netwerk A een subnet van netwerk B. Anders niet!</li>
      </ul>
    </div>

  </div>
</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 8 (Deel 1)</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Vergelijk subnetmaskers of hostbits</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      Mask Netwerk A: /16: <span style="color:#00cfff;">11111111.11111111.</span><span style="color:#e53935;">00000000.00000000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask Netwerk B: /12: <span style="color:#00cfff;">11111111.1111</span><span style="color:#e53935;">0000.00000000.00000000</span>
    </div>
    <div style="text-align:left;font-size:1.3rem;"><strong>Conclusie: A is kleiner dan B (16 >= 12), dus we gaan naar stap 2.</strong></div>
  </div>
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 2: We berekenen bereik netwerk A: We nemen het subnetmasker van stap 1 over.</div>
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 172.32.0.0:  <span style="color:#00cfff;">10101100.00100000.</span><span style="color:#e53935;">00000000.00000000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.255.0.0: <span style="color:#00cfff;">11111111.11111111.</span><span style="color:#e53935;">00000000.00000000</span>
    </div>
  </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Netwerkadres netwerk A:</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">10101100.00100000.</span><span style="color:#e53935;">00000000.00000000</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#00cfff;">172.32.0.0</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Broadcastadres netwerk A</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">10101100.00100000.</span><span style="color:#e53935;">11111111.11111111</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#e53935;">172.32.255.255</strong></div>
    </div>
  </div>
  </div>

  <!-- Stap 4 + 5: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Aantal Hosts netwerk A</div>
      <div style="text-align:left;font-size:1.3rem">16 host-bits → 2<sup>16</sup> – 2 = <strong>65534 hosts</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Bruikbaar Bereik (Range) Netwerk A</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>172.32.0.1 – 172.32.255.254</strong>
      </div>
    </div>

  </div>
</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 8 (Deel 2)</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 3: We berekenen bereik netwerk B: We nemen het subnetmasker van stap 1 over.</div>
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 172.16.0.0:  <span style="color:#00cfff;">10101100.0001</span><span style="color:#e53935;">0000.00000000.00000000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: 255.240.0.0: <span style="color:#00cfff;">11111111.1111</span><span style="color:#e53935;">0000.00000000.00000000</span>
    </div>
  </div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Netwerkadres netwerk B:</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">10101100.0001</span><span style="color:#e53935;">0000.00000000.00000000</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#00cfff;">172.16.0.0</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Broadcastadres netwerk B</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">10101100.0001</span><span style="color:#e53935;">1111.11111111.11111111</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#e53935;">172.31.255.255</strong></div>
    </div>

  </div>
  </div>
  <!-- Stap 4 + 5: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Aantal Hosts netwerk B</div>
      <div style="text-align:left;font-size:1.3rem">20 host-bits → 2<sup>20</sup> – 2 = <strong>1.048.574 hosts</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Bruikbaar Bereik (Range) Netwerk B</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>172.16.0.1 – 172.31.255.254</strong>
      </div>
    </div>

  </div>
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 4: Valt bereik A volledig binnen bereik B?</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        Bereik A: <strong>172.32.0.1 – 172.32.255.254</strong>
      </div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        Bereik B: <strong>172.16.0.1 – 172.31.255.254</strong>
      </div>
      <div style="text-align:left;font-size:1.3rem;"><strong>Conclusie: Bereik netwerk A valt NIET binnen netwerk B:</strong><strong style="color:#e53935;"> Netwerk A is GEEN subnet van Netwerk B!</strong></div>
  </div>
</section>
<section>

  <!-- Title -->
  <div>
    <h2>Oefening 9: Bytewaardes</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Met welke eerste bytewaardes (decimaal) kan volgend subnet beginnen?</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        IP: <span style="color:#00cfff;">10.0.0.0 / 8</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Wat moet je bepalen?</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Subnet Masker</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Netwerkadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Broadcastadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Het bruikbare bereik</li>
      </ul>
    </div>

  </div>

  <!-- Tip -->
  <p style="margin-top:1.5rem;font-style:italic;color:#8899aa;font-size:1.45rem;">Tip: Gebruik het stappenplan uit de vorige slides!</p>

</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 9</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 10.0.0.0: <span style="color:#00cfff;">00001010.</span><span style="color:#e53935;">00000000.00000000.00000000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: /8: <span style="color:#00cfff;">11111111.</span><span style="color:#e53935;">00000000.00000000.00000000</span>
    </div>
  </div>

  <!-- Stap 2 + 3: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;margin-bottom:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 2: Netwerkadres</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">00001010.</span><span style="color:#e53935;">00000000.00000000.00000000</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#00cfff;">10.0.0.0</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 3: Broadcastadres</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">00001010.</span><span style="color:#e53935;">11111111.11111111.11111111</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#e53935;">10.255.255.255</strong></div>
    </div>

  </div>

  <!-- Stap 4 + 5: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 4: Bruikbaar Bereik (Range)</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>10.0.0.1 t/m 10.255.255.254</strong>
      </div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 5: Bepaal mogelijke eerste bytewaardes (= eerste octet = eerste 8 bits) in bereik</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>10</strong>
      </div>
    </div>

  </div>

</section>
<section>
  
  <!-- Title -->
  <div>
    <h2>Oefening 10: Bytewaardes</h2>
  </div>

  <!-- Two columns -->
  <div style="display:flex;gap:2rem;align-items:flex-start;">
    <div style="flex:1.1;border:2px solid #00cfff;border-radius:6px;padding:1.8rem 2rem">
      <div style="font-size:1.6rem;font-weight:700;margin-bottom:1.5rem;">Met welke eerste bytewaardes (decimaal) kan volgend subnet beginnen?</div>
      <div style="font-family:'Share Tech Mono',monospace;font-size:1.4rem;margin-bottom:.6rem;">
        IP: <span style="color:#00cfff;">200.16.0.0 / 12</span>
      </div>
    </div>
    <div style="width:4px;border-radius:2px;align-self:stretch;min-height:180px;"></div>
    <div style="flex:1.3;padding-left:.5rem;">
      <div style="font-family:'Rajdhani',sans-serif;font-size:1.6rem;font-weight:700;color:#f5a623;margin-bottom:1rem;">Wat moet je bepalen?</div>
      <ul style="list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:.7rem;">
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Subnet Masker</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Netwerkadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Broadcastadres</li>
        <li style="display:flex;align-items:center;gap:.8rem;font-size:1.3rem"><span style="color:#00cfff;font-weight:700;">✓</span> Het bruikbare bereik</li>
      </ul>
    </div>

  </div>
</section>
<section>

  <!-- Title -->
  <h2>Oplossing Oefening 10</h2>

  <!-- Stap 1: full width -->
  <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;margin-bottom:.7rem;">
    <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 1: Binaire Voorstelling</div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.25rem;">
      IP: 200.16.0.0: <span style="color:#00cfff;">11001000.0001</span><span style="color:#e53935;">0000.00000000.00000000</span>
    </div>
    <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;">
      Mask: /12: <span style="color:#00cfff;">11111111.1111</span><span style="color:#e53935;">0000.00000000.00000000</span>
    </div>
  </div>

  <!-- Stap 2 + 3: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;margin-bottom:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 2: Netwerkadres</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">11001000.0001</span><span style="color:#e53935;">0000.00000000.00000000</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#00cfff;">200.16.0.0</strong></div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 3: Broadcastadres</div>
      <div style="text-align:left;font-family:'Share Tech Mono',monospace;font-size:1.3rem;margin-bottom:.4rem;">
        <span style="color:#00cfff;">11001000.0001</span><span style="color:#e53935;">1111.11111111.11111111</span>
      </div>
      <div style="text-align:left;font-size:1.3rem;">Resultaat: <strong style="color:#e53935;">200.31.255.255</strong></div>
    </div>
  </div>

  </div>
  <!-- Stap 4 + 5: two columns -->
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:.7rem;">
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 4: Bruikbaar Bereik (Range)</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>200.16.0.1 t/m 200.31.255.254</strong>
      </div>
    </div>
    <div style="border-left:4px solid #f5a623;border-radius:4px;padding:.8rem 1.2rem;">
      <div style="text-align:left;font-family:'Rajdhani',sans-serif;font-weight:700;color:#f5a623;font-size:1.3rem;margin-bottom:.5rem;">Stap 5: Bepaal mogelijke eerste 2 bytes (= eerste 2 octetten = eerste 16 bits) in bereik</div>
      <div style="text-align:left;font-size:1.3rem;color:#00cfff;">
        <strong>200.16 t/m 200.31</strong>
      </div>
    </div>

  </div>

</section>