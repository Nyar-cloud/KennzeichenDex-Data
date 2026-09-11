# Lizenzen der Rohdatenquellen

Wird von `data/sources/README.md` referenziert. Gehoert in den
Info-Bildschirm der App, sobald es einen gibt (noch nicht gebaut).

## Wikipedia (Kennzeichen-Daten)

Alle Quellen unter `data/sources/README.md` (Listen der Kfz-Kennzeichen,
Diplomatenkennzeichen), Lizenz **CC BY-SA 4.0**. Autoren: die jeweiligen
Wikipedia-Artikel und ihre Versionsgeschichte auf de.wikipedia.org.

## VG250 (Kreisgeometrie)

Verwaltungsgebiete 1:250.000, Bundesamt fuer Kartographie und Geodaesie
(BKG), Lizenz **Datenlizenz Deutschland - Namensnennung 2.0**
(dl-de/by-2-0). Namensnennung:

> © GeoBasis-DE / BKG (Jahr der Datenausgabe)

Bezug: `https://daten.gdz.bkg.bund.de/produkte/vg/vg250_ebenen_0101/`

## vegvesen.no (Kennzeichen-Daten Norwegen)

Erster Fall im Projekt, der nicht von Wikipedia kommt (siehe
docs/decisions.md E47). Statens vegvesen (norwegische
Straßenverkehrsbehörde) schreibt in seinem Copyright-Hinweis
(`https://www.vegvesen.no/en/about-us/about-the-organisation/about-vegvesen.no/about-the-website/`,
Stand 01.09.2026) **kein NLOD oder CC**, sondern nur Namensnennung vor:

> Copying, making contents available to the general public, and other
> utilisation beyond what follows from the Copyright Act, is allowed as
> long as the NPRA is acknowledged as the source.

NLOD gilt laut derselben Quelle nur für Daten aus der Nasjonal
Vegdatabank (NVDB), nicht für normale Inhaltsseiten wie die hier
verwendete "Number plate series"-Seite. Namensnennung: **Statens
vegvesen (Norwegian Public Roads Administration)**.

## Eurostat GISCO (Kantonsgeometrie Schweiz, Pilot fuer weitere Laender)

NUTS-Grenzen (Nomenclature of Territorial Units for Statistics), Eurostat
GISCO. Lizenz **CC BY 4.0**, Copyright-Hinweis
(`https://ec.europa.eu/eurostat/help/copyright-notice`, Stand 02.09.2026):

> you can re-use the content provided you acknowledge the source and
> indicate any changes you have made

Namensnennung: **© EuroGeographics fuer die Verwaltungsgrenzen** (so von
Eurostat selbst fuer NUTS-Geodaten vorgegeben). Bezug (seit der
Kartenpolitur 03.09.2026, E69, vorher 1:20 Millionen):
`https://gisco-services.ec.europa.eu/distribution/v2/nuts/geojson/NUTS_RG_03M_2024_4326_LEVL_3.geojson`.

Dieselbe Lizenz und Namensnennung gilt fuer GISCOs LAU-Ebene (Gemeinden),
seit Kroatien (E60) genutzt: `https://gisco-services.ec.europa.eu/distribution/v2/lau/geojson/LAU_RG_01M_2023_4326.geojson`.

## KBA FZ 1 (Fahrzeugbestand)

Bestand an Kraftfahrzeugen nach Zulassungsbezirken, Kraftfahrt-Bundesamt
(KBA). Auf der Downloadseite steht nur "© Kraftfahrt-Bundesamt, Flensburg",
**keine erkennbare offene Datenlizenz** wie bei VG250 (Datenlizenz
Deutschland). Amtliche Statistik, in der Praxis breit weiterverwendet;
siehe docs/decisions.md fuer die Einordnung, warum sie trotzdem aufgenommen
wurde. Bezug: `https://www.kba.de/DE/Statistik/Produktkatalog/produkte/Fahrzeuge/fz1_b_uebersicht.html`

## Tailte Éireann (Countygeometrie Irland)

"Counties - National Statutory Boundaries - Ungeneralised", Tailte
Éireann (vormals Ordnance Survey Ireland, OSi). Lizenz **CC BY 4.0**, so
von OSi/Tailte Éireann fuer als Open Data veroeffentlichte Inhalte
durchgehend vorgegeben. Copyright-Feld der ArcGIS-FeatureServer-Quelle
(Stand 02.09.2026):

> © National Mapping Division of Tailte Éireann

Bezug: `https://data-osi.opendata.arcgis.com/datasets/dc24df2a5ce84ee9a38d9afe8431ee9b`
(ArcGIS Open Data, siehe `data/build/geometrie-ie.mjs` fuer die
Download-URL des GeoJSON-Exports).

## GUGiK PRG (Powiatgeometrie Polen)

Państwowy Rejestr Granic (PRG), Główny Urząd Geodezji i Kartografii
(GUGiK), bezogen ueber den WFS-Dienst `AdministrativeBoundaries`
(`mapy.geoportal.gov.pl`). **Keine erkennbare formale CC-Lizenz fuer den
Datensatz selbst** (anders als VG250 oder GISCO) - die Bereitstellung
ohne Gebuehr stuetzt sich auf Art. 40a Abs. 2 des polnischen Gesetzes
Prawo geodezyjne i kartograficzne (Geodaesie- und Kartographiegesetz),
bestaetigt durch den WFS-Capabilities-Eintrag `<ows:Fees>Brak opłat</ows:Fees>`
("keine Gebuehren"). Die gov.pl-Webseite selbst nennt als Standardlizenz
fuer Inhalte **CC BY-SA 4.0** ("Creative Commons: uznanie autorstwa - na
tych samych warunkach 4.0"), ohne das ausdruecklich auf PRG-Geodaten zu
beziehen - dieselbe Grauzone wie bei vegvesen.no (siehe oben), deshalb
vorsichtshalber mit Namensnennung statt einer behaupteten Lizenz
uebernommen. Namensnennung: **Główny Urząd Geodezji i Kartografii
(GUGiK)**. Bezug: `https://www.geoportal.gov.pl/en/data/national-register-of-boundaries/`

## geoBoundaries (Gemeindegeometrie Serbien, Montenegro)

**Erste Quelle im Projekt, die nicht CC BY 4.0 ist.** geoBoundaries
selbst vergibt fuer sein kuratiertes Gesamtprojekt CC BY 4.0, die
konkreten Serbien/Montenegro-Datensaetze fuehren in ihren eigenen
Metadaten aber ausdruecklich eine andere Lizenz (Stand 03.09.2026,
`https://www.geoboundaries.org/api/current/gbOpen/SRB/ADM2/` bzw.
`.../MNE/ADM1/`):

> "boundaryLicense": "Open Data Commons Open Database License 1.0",
> "boundarySource": "OpenStreetMap, Wambacher",
> "licenseSource": "www.openstreetmap.org/copyright"

Die Geometrie stammt also letztlich aus OpenStreetMap (per
Wambacher-Grenzenextrakt, `wambachers-osm.website/boundaries/`), Lizenz
**ODbL 1.0**: Namensnennung noetig, und eine veroeffentlichte
"Derivative Database" muss unter derselben oder einer kompatiblen Lizenz
stehen (Share-Alike fuer die Datenbank, nicht fuer daraus erzeugte
einzelne Werke wie ein Kartenbild). Namensnennung: **© OpenStreetMap
contributors**. Bezug: `https://www.geoboundaries.org/`, konkrete
GeoJSON-Downloadlinks ueber die API-Metadaten der jeweiligen
Landesseite, siehe `data/build/geometrie-rs.mjs` und
`data/build/geometrie-me.mjs`.

Grund fuer die andere Quelle: GISCO (sonst die Standardquelle seit der
Schweiz) fehlt Montenegro komplett, und liefert fuer Serbien
nachweislich fehlerhafte Ortsnamen (docs/decisions.md E61).

**Ukraine nutzt dieselbe Wambacher/OSM-Quelle, dieselbe ODbL-1.0-Lizenz**
(E66) - GISCO fehlt auch der Ukraine (fehlt komplett in der
NUTS-2024-Ausgabe, kein EU-Kandidat vor 2022).

**Russland ebenfalls dieselbe Wambacher/OSM-Quelle, ODbL 1.0** (E68) -
sechs umstrittene Gebiete (Krim, Sewastopol, vier ukrainische Oblaste)
bewusst nicht kartiert, siehe docs/decisions.md E68 (Nutzerentscheidung,
keine Lizenzfrage).

**Moldawien nutzt geoBoundaries ebenfalls (E65), aber eine ANDERE
zugrundeliegende Quelle:** die geoBoundaries-Metadaten fuer
`MDA/ADM1` nennen `"boundarySource": "UNHCR, OCHA FISS"` und
`"boundaryLicense": "Creative Commons Attribution 3.0 Intergovernmental
Organisations (CC BY 3.0 IGO)"` (Stand 03.09.2026) - NICHT OpenStreetMap/
ODbL wie bei Serbien, Montenegro und der Ukraine. geoBoundaries buendelt
also nicht durchgehend dieselbe Lizenz, jedes Land muss einzeln gegen
seine eigenen API-Metadaten geprueft werden. Namensnennung fuer Moldawien:
**UNHCR/OCHA, ueber geoBoundaries**.

**Weissrussland nutzt geoBoundaries mit einer VIERTEN Lizenzvariante**
(E67): `BLR/ADM1`-Metadaten nennen `"boundarySource": "CIESIN"`
(Center for International Earth Science Information Network, Columbia
University) und `"boundaryLicense": "Creative Commons Attribution 3.0
License"` - CC BY 3.0 OHNE den "IGO"-Zusatz Moldawiens, eine eigene
Lizenzvariante. Namensnennung: **CIESIN, Columbia University, ueber
geoBoundaries**.

## Nominatim (Punktgeometrie Slowenien, Grossbritannien, Norwegen)

Dieselbe Quelle wie geoBoundaries oben, direkt aus OpenStreetMap statt
ueber einen kuratierten Grenzendatensatz: Nominatim
(`nominatim.openstreetmap.org`) loest Ortsnamen zu Koordinaten auf, fuer
Laender ohne eigene Flaeche zum Abgleichen (E64). **Lizenz ODbL 1.0**,
Namensnennung **© OpenStreetMap contributors**. Nutzungsbedingungen
(`https://operations.osmfoundation.org/policies/nominatim/`) verlangen
zusaetzlich hoechstens eine Anfrage pro Sekunde und einen eigenen
User-Agent - beides in `data/build/nominatim.mjs` eingehalten, Ergebnisse
werden pro Land gecached (`data/sources/nominatim-<land>.json`) statt bei
jedem Lauf erneut abgefragt.

## Natural Earth (Basiskarte der Kartenseite)

`ne_50m_admin_0_countries`, `ne_10m_admin_0_countries`,
`ne_10m_admin_1_states_provinces_lines`, `ne_50m_lakes`,
`ne_10m_populated_places` und `ne_50m_geography_marine_polys`, bezogen
ueber `raw.githubusercontent.com/nvkelso/natural-earth-vector` (E78).
Daraus entsteht `web/public/karte/basiskarte.json`: Landflaechen, Grenzen,
Seen und die deutschen Namen fuer Laender, Orte und Meere.

**Lizenz: Public Domain.** Natural Earth verzichtet ausdruecklich auf jede
Namensnennung ("no permission needed", `naturalearthdata.com/about/terms-of-use`).
Die Karte nennt die Quelle trotzdem im Nachweis unten rechts
("Kartengrundlage: Natural Earth") - das kostet nichts und sagt dem
naechsten Leser, woher die Umrisse kommen.
