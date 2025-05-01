# 🧪 Øvelse 3: Design af eget topic-hierarki (UNS)

## 🎯 Formål
I denne øvelse skal du anvende din viden fra de foregående øvelser til at designe en fuldstændig **Unified Namespace (UNS)** for et fiktivt produktionssystem. Denne aktivitet styrker dine kompetencer i struktureret emnearkitektur, konsistent navngivning og semantisk klarhed. Ved at omsætte fysiske og funktionelle elementer fra et teknisk system til en emnestruktur lærer du, hvordan data bliver både læsbart, meningsfuldt og skalerbart i praksis.

Formålet er at:
- Opbygge en emnestruktur, der afspejler den fysiske virkelighed i et anlæg
- Træne ensartet navngivning, brug af hierarki og semantisk tydelighed
- Forstå hvordan en god UNS gør integration, fejlfinding og systemudvidelse lettere
- Skabe en dokumenterbar model, som kan bruges i både drift og udvikling

Denne øvelse forbereder dig på opgaver som kravspecifikation, dataintegration og standardisering i rigtige IIOT-projekter – og bliver fundamentet for næste øvelse, hvor UNS’en skal bruges med konkrete data.

---

## 🛠️ Forudsætninger
- Du har gennemført Øvelse 1 og 2 og har erfaring med emnehierarkier
- Du har arbejdet med både MQTT/Sparkplug og OPC UA i Workshop 4
- Du kender principperne for UNS og har reflekteret over struktur og semantik

---

## 🧩 Opgave – Trin-for-trin

### 1. Vælg eller få tildelt et fiktivt anlæg
Vælg en af følgende casetyper (eller brug en case fra dit projekt):
- 🏭 En pakkeproces med transportbånd, vægt og stempel
- 🌬️ Et ventilationsanlæg med temperatur, lufttryk og CO₂-målinger
- 💧 Et tankanlæg med flowmåler, væskeniveau og pumpecontroller

Lav evt. en kort beskrivelse af, hvad anlægget gør, og hvor det kunne befinde sig (fx "hal 1 i fabrik alpha").

### 2. Identificér det fysiske hierarki
Tænk som en systemarkitekt og lav et logisk hierarki, der dækker:
- Site (lokation eller virksomhed)
- Area (bygning, hal, zone)
- Line (maskinrække, ventilationszone, tanklinie)
- Cell (enkeltmaskine, PLC, sensorpakke)
- Device (målepunkter og aktuatorer)

Tegn det op med pen og papir, draw.io eller andet diagramværktøj. 
Overvej hvordan du ville forklare det for en nyansat eller en ekstern leverandør.

### 3. Navngiv alle datapunkter
For hvert device skal du:
- Identificere mindst 2–3 relevante målepunkter
- Beskrive:
  - Sensor/aktuator-type (temperatur, motorstatus, flow)
  - Datatype (float, int, bool)
  - Enhed (°C, %, L/min, Pa, etc.)
  - Målepunktets funktion og kontekst
- Omsætte det til en UNS-emnestruktur

Eksempel:
```
fabrik_alpha/hal2/line1/plc_main/temp_supply/value
```
- Hvor:
  - `fabrik_alpha` = site
  - `hal2` = område
  - `line1` = maskinlinje
  - `plc_main` = controller
  - `temp_supply` = datapunkt

Gentag dette for mindst 6 datapunkter i din løsning.

### 4. Dokumentér emnestrukturen visuelt
Vælg én af disse metoder (eller flere):
- Tegn det i draw.io, Visio, Lucidchart eller lignende
- Lav en tabel med kolonner: *Topic*, *Beskrivelse*, *Datatype*, *Enhed*, *Bruger*
- Udarbejd en JSON-lignende emnestruktur, hvor du viser hierarkiet i kodeform

Din dokumentation skal vise:
- Hele hierarkiet fra site til datapunkt
- Hvilken information der er gemt i emnet
- Hvilke funktioner eller roller bruger det (drift, udvikling, ledelse, IT)

---

## 📋 Refleksion
Skriv en refleksion på 10–15 linjer (eller bullet points):
- Hvordan opbyggede du hierarkiet, og hvad inspirerede dig?
- Hvilke navnekonventioner brugte du – og hvorfor?
- Hvad var den største udfordring undervejs?
- Hvordan kan din UNS-struktur bidrage til fejlfinding, dokumentation og systemudvidelse?
- Hvordan ville du dokumentere og kommunikere denne UNS til et team?

> 💡 Gem din dokumentation – den skal bruges i Øvelse 4 og 5, hvor vi mapper virkelige data fra OPC UA og Sparkplug ind i dit UNS-design og visualiserer det i Node-RED.

