# KennzeichenDex Data

Maschinenlesbare Liste der Kfz-Unterscheidungszeichen von 24
europaeischen Laendern: **3509 Zeichen**, je Land eine JSON-Datei.

*Machine-readable list of vehicle registration prefixes for 24
European countries. Field names and place names are German; the format is
described below.*

## Bestand

| Land | ISO | Datei | Zeichen | aktuell | nicht mehr vergeben |
| --- | --- | --- | ---: | ---: | ---: |
| Bulgarien | `BG` | [plates/bg.json](plates/bg.json) | 32 | 32 | 0 |
| Deutschland | `DE` | [plates/de.json](plates/de.json) | 1068 | 1009 | 59 |
| Griechenland | `GR` | [plates/gr.json](plates/gr.json) | 183 | 183 | 0 |
| Großbritannien | `GB` | [plates/gb.json](plates/gb.json) | 467 | 467 | 0 |
| Irland | `IE` | [plates/ie.json](plates/ie.json) | 29 | 29 | 0 |
| Italien | `IT` | [plates/it.json](plates/it.json) | 107 | 107 | 0 |
| Kosovo | `XK` | [plates/xk.json](plates/xk.json) | 7 | 7 | 0 |
| Kroatien | `HR` | [plates/hr.json](plates/hr.json) | 34 | 34 | 0 |
| Moldawien | `MD` | [plates/md.json](plates/md.json) | 42 | 42 | 0 |
| Montenegro | `ME` | [plates/me.json](plates/me.json) | 27 | 25 | 2 |
| Nordmazedonien | `MK` | [plates/mk.json](plates/mk.json) | 35 | 33 | 2 |
| Norwegen | `NO` | [plates/no.json](plates/no.json) | 414 | 414 | 0 |
| Österreich | `AT` | [plates/at.json](plates/at.json) | 111 | 103 | 8 |
| Polen | `PL` | [plates/pl.json](plates/pl.json) | 427 | 422 | 5 |
| Rumänien | `RO` | [plates/ro.json](plates/ro.json) | 42 | 42 | 0 |
| Russland | `RU` | [plates/ru.json](plates/ru.json) | 141 | 135 | 6 |
| Schweiz | `CH` | [plates/ch.json](plates/ch.json) | 26 | 26 | 0 |
| Serbien | `RS` | [plates/rs.json](plates/rs.json) | 74 | 74 | 0 |
| Slowakei | `SK` | [plates/sk.json](plates/sk.json) | 74 | 74 | 0 |
| Slowenien | `SI` | [plates/si.json](plates/si.json) | 11 | 11 | 0 |
| Tschechien | `CZ` | [plates/cz.json](plates/cz.json) | 14 | 14 | 0 |
| Türkei | `TR` | [plates/tr.json](plates/tr.json) | 81 | 81 | 0 |
| Ukraine | `UA` | [plates/ua.json](plates/ua.json) | 55 | 55 | 0 |
| Weißrussland | `BY` | [plates/by.json](plates/by.json) | 8 | 8 | 0 |

## Aufbau einer Datei

```jsonc
{
  "land":   { "iso2": "CZ", "nameDe": "Tschechien", "plateLetter": "CZ", "continent": "europa" },
  "quelle": "Kfz-Kennzeichen (Tschechien)",   // Titel des Wikipedia-Artikels
  "lizenz": "CC BY-SA 4.0",
  "erzeugt": "2026-09-08",
  "anzahl": 14,
  "plates": [
    {
      "code": "A",                       // das Unterscheidungszeichen
      "scope": "region",                 // region | state | federal | diplomatic | country
      "status": "aktuell",               // aktuell | auslaufend | historisch
      "gebiete": ["Hlavní město Praha"], // Kreise oder Behoerde im Klartext
      "derivation": "Hauptstadt Prag",   // woher das Zeichen kommt
      "gueltigAb": null,                 // ISO-Datum oder null
      "gueltigBis": null,                // gesetzt, wenn aufgehoben
      "bundeslaender": [],               // nur bei Deutschland und Polen belegt
      "varianten": []
    }
  ]
}
```

Ein Zeichen kann zu mehreren Gebieten gehoeren, wenn Stadt und Landkreis es
sich teilen oder wenn es nach einer Liberalisierung in mehreren Kreisen
wieder ausgegeben wird. Deshalb ist `gebiete` immer eine Liste.

## Wie das hier entsteht

Erzeugt aus Wikipedia-Schnappschuessen durch die Generatoren von
KennzeichenDex, einmal die Woche automatisch hierher geschoben. Die Dateien
werden dabei vollstaendig neu geschrieben.

**Deshalb keine Pull Requests auf die JSON-Dateien**: sie waeren beim
naechsten Lauf wieder weg. Fehler und Luecken bitte als Issue melden, dann
wird die Ursache im Generator behoben und die Korrektur haelt.

## Bekannte Luecken

Fuer einige Laender ist der Bestand kleiner als das, was Sammler-Apps
zaehlen. Erklaerbar ist das bei Polen: dort bekommt ein Powiat ein zweites
Zeichen, wenn der Nummernvorrat des ersten erschoepft ist, und keine der
geprueften Quellen fuehrt diese Zweitzeichen vollstaendig. Geraten wird
nicht, deshalb fehlen sie lieber.

## Lizenz

Die Daten stammen aus der Wikipedia und stehen unter **CC BY-SA 4.0**.
Namensnennung, Quellenangaben und die Lizenzen der uebrigen verwendeten
Quellen stehen in [QUELLEN-UND-LIZENZEN.md](QUELLEN-UND-LIZENZEN.md). Wer
die Daten weitergibt, gibt sie unter denselben Bedingungen weiter.
