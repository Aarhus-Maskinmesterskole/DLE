# 🧪 Øvelse 6: Validering og visualisering af samlet Unified Namespace (UNS)

## 🎯 Formål
Denne øvelse har til formål at samle, konsolidere og evaluere alle dine tidligere resultater fra Workshop 5. Du skal integrere dine datastrømme fra både **OPC UA** og **Sparkplug B** ind i det samlede **Unified Namespace (UNS)**-hierarki, du har designet tidligere, og visualisere det i Node-RED på en brugervenlig, struktureret og informativ måde.

Formålet med øvelsen er at:
- **Validere** din UNS i praksis: Fungerer emnestrukturen, når flere datakilder og teknologier anvendes samtidigt?
- **Visualisere** data fra forskellige protokoller i ét ensartet overblik
- **Reflektere** over kvaliteten, læsbarheden og fremtidig vedligeholdelse af din UNS-struktur
- Skabe grundlag for den afsluttende dokumentation og præsentation

Ved at samle data i ét emnehierarki og præsentere det konsistent i et fælles dashboard, bliver det muligt at identificere styrker og svagheder i dit arkitekturbeslutning og forberede reelle implementeringer.

---

## 🛠️ Forudsætninger
- Du har færdiggjort Øvelse 4 og 5 og har:
  - Min. ét flow med OPC UA-data
  - Min. ét flow med Sparkplug B-data
- Du har opbygget en UNS-struktur i Øvelse 3, som emnerne nu skal mappes op imod
- Du har kendskab til dashboard-noder i Node-RED (`ui_*`)
- Din broker og/eller OPC UA-server er stadig aktiv og tilgængelig

---

## 🧩 Trin-for-trin opgave

### 1. Saml dine flows
- Kombinér `function`-noderne fra begge datastrømme (OPC UA og Sparkplug B) til ét samlet flow
- Sikr at alle output-noder indeholder følgende felter:
  - `msg.payload.topic` (UNS-emne)
  - `value` (måling eller status)
  - `timestamp` (genereres i Node-RED eller kommer med data)
  - `unit` (hvis tilgængelig)
  - `source` (fx “opcua” eller “sparkplug_b”)
- Brug `switch` eller `change`-noder hvis nødvendigt for at sikre korrekt mapping
- Brug `join`-node hvis du vil aggregere datapunkter i én besked

### 2. Design og opbyg dashboardet
- Del dashboardet op i **funktionelle sektioner** eller **geografiske områder** (fx hal 1, hal 2 / ventilation, varme / OPC UA, Sparkplug)
- Brug mindst 3 forskellige visningstyper:
  - `ui_gauge` til live målinger
  - `ui_table` til struktureret oversigt over alle datapunkter
  - `ui_led` eller `ui_icon` til statusindikatorer
  - `ui_chart` til historiske data
- Sæt tydelige labels, enheder og farvekoder for bedre læsbarhed

### 3. Validér emnestruktur og navngivning
- Kontrollér at alle emner matcher det du definerede i Øvelse 3
  - Har alle emner samme hierarkiske struktur (site/area/line/device/tag)?
  - Er navnene entydige, læsbare og logiske?
  - Er datatyper og enheder konsekvente?
  - Er “source” tydeligt nok angivet til at adskille protokoller?
- Brug evt. MQTT Explorer og/eller UAExpert til at sammenligne med rå emner

### 4. Dokumentér dit arbejde
- Gem screenshots af:
  - Hele dashboardet i Node-RED
  - Visualiseringer for mindst 2 forskellige datapunkter fra hver protokol
  - Debug-vinduet der viser payload-strukturen
- Gem dit samlede flow som `.json` og navngiv det fx `uns_visualisering.json`
- Lav en tabel eller tekstforklaring over:
  - Hvilke datapunkter vises
  - Hvordan emnerne er mappet til UNS
  - Hvilke UI-komponenter der bruges til hvilke formål

---

## 📋 Refleksion
Skriv en refleksion eller diskutér følgende spørgsmål:
- Hvordan fungerede integrationen mellem OPC UA og Sparkplug i praksis?
- Var det muligt at visualisere alt data i én logisk struktur?
- Hvor opstod der konflikter, uoverensstemmelser eller redundans?
- Hvordan vurderer du din UNS-struktur i forhold til:
  - **Skalerbarhed** – kan den udvides til 100+ datapunkter?
  - **Genkendelighed** – kan en kollega forstå den uden forklaring?
  - **Semantik** – er datapunkternes betydning entydig og tydelig?
- Hvis du skulle starte forfra, hvad ville du gøre anderledes i din UNS?

> 💡 I næste øvelse skal du samle al dokumentation og erfaring i en afsluttende portfolio og forberede en kort præsentation, der forklarer og forsvarer dit UNS-design. Dette bliver kulminationen på hele Workshop 5.
