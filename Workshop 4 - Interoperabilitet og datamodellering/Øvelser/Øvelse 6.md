# 🧪 Øvelse 6: Visualisering af data fra interoperable systemer

## 🎯 Formål
I denne øvelse skal du designe og opbygge et dashboard i Node-RED, der integrerer og visualiserer data fra både **OPC UA** og **MQTT/Sparkplug B**. Formålet er at vise, hvordan man i praksis kan samle og præsentere data fra forskellige industrielle protokoller i ét samlet overblik, hvilket er centralt i enhver IIOT-løsning, der arbejder med interoperabilitet.

Ved at arbejde med realtidsvisualisering fra flere kilder opnår du:
- Bedre forståelse af dataintegration og harmonisering
- Erfaring med databerigelse og præsentation i dashboardform
- Indsigt i hvordan visualisering kan understøtte drift, vedligeholdelse og beslutningsstøtte

Du kommer til at bygge et dashboard, der tydeligt viser målinger, status og metadata for mindst to forskellige protokolkilder og visualiserer det i et overskueligt format, der kan bruges af både teknikere og ledere.

---

## 🛠️ Forudsætninger
For at få fuldt udbytte af øvelsen, skal du have:
- Opsat et fungerende flow i Node-RED med både OPC UA-klient og MQTT/Sparkplug B-modtagelse
- Forståelse for hvordan payloads fra begge protokoller er struktureret
- Installeret og testet `node-red-dashboard`
- Forståelse for JSON-formatering og hvordan man tilpasser data med `function`-noder

---

## 🔧 Praktisk – Trin-for-trin

### 1. Forbered dine datakilder
- Sørg for at dit **OPC UA-flow** læser fx `ns=2;s=Dynamic/RandomFloat` fra din server
- Sørg for at dit **Sparkplug-flow** modtager `DDATA`-beskeder via `mqtt-in`
- Brug evt. `debug`-noder til at sikre, at begge flows virker korrekt

### 2. Berig data med metadata
Tilføj en `function`-node på hver datakilde, som omformer rå payload til struktureret format som:
```javascript
msg.payload = {
  value: msg.payload.value.value,
  unit: "°C",
  source: "OPCUA_Ventilation",
  status: "OK",
  timestamp: new Date().toISOString()
};
return msg;
```
Sparkplug-data kan parses tilsvarende, afhængigt af din `metrics[]` struktur. Vælg én metric pr. datapunkt og pak den ud med navn, værdi og metadata.

### 3. Design dashboardet
- Brug `ui_tab` og `ui_group` til at opdele visning af OPC UA- og Sparkplug-data
- Tilføj følgende komponenter:
  - `ui_text` eller `ui_value` til talvisning
  - `ui_gauge` til visning af sensorværdier (temperatur, CO2, tryk)
  - `ui_led`, `ui_icon` eller `ui_colored_indicator` til status (grøn, gul, rød)
  - `ui_table` eller `ui_chart` til visning over tid eller listeform
- Brug `ui_control` til at tilpasse visningen live

### 4. Kombinér og sammenlign datakilder (avanceret)
- Brug `join` node til at samle datapunkter i ét samlet `msg.payload`
- Vis hele systemstatus som samlet view – fx en tabel eller oversigt
- Lav evt. farvekoder eller ikoner der viser om datakilderne er aktive eller fejler

---

## 📋 Refleksion
Skriv en kort refleksion hvor du overvejer:
- Hvordan adskiller data fra OPC UA og Sparkplug B sig i struktur og metadata?
- Hvilke udfordringer stødte du på med at forene forskellige datakilder i samme dashboard?
- Hvordan påvirkede format, opdateringsfrekvens eller manglende enheder visualiseringen?
- Hvad ville du ændre i visualiseringen, hvis:
  - Det skulle vises for en tekniker?
  - Det skulle vises for en afdelingsleder?
  - Det skulle eksporteres til en rapport?

---

## 📤 Aflevering
- Lav screenshots af dit dashboard
- Vis mindst ét målepunkt fra hver protokolkilde (OPC UA + Sparkplug)
- Beskriv kort hvad du har visualiseret, og hvorfor det er meningsfuldt
- Gem dit Node-RED-flow som `.json` og aflever det som bilag

> 💡 Du er nu klar til Øvelse 7, hvor du dokumenterer og samler alt dit arbejde og refleksion i en samlet portefølje og afsluttende præsentation.

