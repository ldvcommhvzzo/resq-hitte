# ResQ – Hitteplan

Realtime hittebelastingsmonitor voor **Hulpverleningszone Zuid-Oost (HVZZO)**. De
applicatie toetst de actuele en verwachte **WBGT-waarde** (Wet Bulb Globe
Temperature) aan de wettelijke actiewaarden en werkregimes uit de **Codex over
het welzijn op het werk, boek V, titel 1**, en vertaalt die naar een concrete
kleurcode en werkregime-advies per kazerne en per type arbeid.

De volledige toepassing is één zelfstandig HTML-bestand
(`ResQ_-_Hitteplan_-_standalone.html`) dat in elke moderne browser draait, zonder
installatie, server of build-stap. Weer- en luchtkwaliteitsgegevens worden live
opgehaald bij Open-Meteo.

![Overzicht van de ResQ – Hitteplan-toepassing](screenshots/01-overview-full.png)

---

## Wat de tool doet

- **Live status per locatie** – voor de negen kazernes en posten van de zone toont
  ze temperatuur, luchtvochtigheid, wind, de berekende WBGT-waarde en de
  kleurcode per werktype (licht, halfzwaar, zwaar, zeer zwaar).
- **Advies op maat** – kies een functieprofiel, werktype en locatie en de tool
  geeft het toepasselijke werkregime (bv. 45′ werk / 15′ pauze) plus de bijhorende
  maatregelen.
- **7-daagse vooruitblik** – de hoogst verwachte WBGT per dag, met kleurcode, om
  planning en aflossing voor te bereiden.
- **Locatie opzoeken** – zoek elke Belgische gemeente of postcode op, bijvoorbeeld
  voor versterking of transport naar een andere zone.
- **Ozon-indicatie** – waarschuwt bij overschrijding van de informatiedrempel
  (180 µg/m³) en de alarmdrempel (240 µg/m³).
- **Referentiekaarten** – wat onder welk type werk valt, een symptomenkaart voor
  thermische overbelasting en de instructies bij interventie in warm weer.

## Kleurcode

| Kleur | Betekenis | Werkregime |
|-------|-----------|------------|
| 🟢 Groen | Onder de actiewaarde | Algemene maatregelen |
| 🟡 Geel | Actiewaarde bereikt | Gele maatregelen, nog geen pauze |
| 🟠 Oranje | Boven de actiewaarde | 45′ werk / 15′ pauze |
| 🔴 Rood | Ruim boven de actiewaarde | 30′ werk / 30′ pauze |

De actiewaarde verschilt per werktype; oranje en rood delen dezelfde maatregelen,
alleen het werkregime verschilt. De volledige logica staat in
[`Calculations.md`](Calculations.md).

## Snel starten

Open `ResQ_-_Hitteplan_-_standalone.html` in een browser (Chrome, Edge, Firefox of
Safari, recente versie). Er is verder niets nodig. Bij het openen haalt de tool
automatisch de actuele gegevens op en vult ze de kaarten in.

> Voor de weer-, lucht- en zoekgegevens is een internetverbinding vereist. Zonder
> verbinding blijven de kaarten in laadtoestand staan; met de knop **Opnieuw
> proberen** per kaart kan een mislukte ophaling herhaald worden.

## Belangrijk voorbehoud

De WBGT-waarde is **berekend, niet gemeten**. De berekening gebruikt de officiële
tabelmethode (Charbonneau) op basis van temperatuur, luchtvochtigheid en
windsnelheid, zoals aanvaard door de FOD WASO. Ze houdt geen rekening met directe
zonnestraling. De officiële hitte-waarschuwingen (code geel/oranje/rood en de
waarschuwingsfase) blijven een menselijke beoordeling van het KMI – controleer die
steeds rechtstreeks via [meteo.be](https://www.meteo.be/nl/weer/waarschuwingen/hitte).

## Documentatie

| Bestand | Inhoud |
|---------|--------|
| [`Architecture.md`](Architecture.md) | Technische opbouw, componenten en het architectuurdiagram |
| [`DataSources.md`](DataSources.md) | Externe API's, statische data en attributie |
| [`Calculations.md`](Calculations.md) | WBGT-berekening, kleurcode- en ozon-logica |
| [`UserGuide.md`](UserGuide.md) | Gebruikershandleiding per schermonderdeel |
| [`CHANGELOG.md`](CHANGELOG.md) | Versiehistoriek |
| [`LICENSE`](LICENSE) | Rechten en gebruiksvoorwaarden |

Schermafbeeldingen staan in [`screenshots/`](screenshots/); het
architectuurdiagram in [`docs/`](docs/).

## Rechten

© 2026 Hulpverleningszone Zuid-Oost. Alle rechten voorbehouden. Zie
[`LICENSE`](LICENSE). Weer- en luchtkwaliteitsdata © Open-Meteo, CC BY 4.0.
