# 🧪 Øvelse 5: Mapping af Sparkplug B-data til Unified Namespace (UNS)

## 🎯 Formål
I denne øvelse skal du lære at integrere og strukturere **Sparkplug B-data** i det **Unified Namespace (UNS)**, du designede i Øvelse 3. Ligesom i Øvelse 4, hvor du mappede OPC UA-data, skal du nu håndtere Sparkplug B’s struktur, så alle datapunkter bliver omformateret, beriget med metadata og placeret korrekt i dit navngivningshierarki.

Sparkplug B bygger på MQTT, men tilføjer en vigtig semantisk ramme omkring datapunkter – og gør det muligt at sende og modtage strukturerede meddelelser om devices, fødsler, død og realtidsdata (DDATA). Du skal i denne øvelse:

- Forstå og håndtere Sparkplug B’s emne- og payloadstruktur
- Udtrække metrikker fra en `DDATA`-besked
- Omstrukturere data til din egen UNS-arkitektur med konsistens og metadata
- Visualisere resultatet i Node-RED dashboard og sammenligne med tidligere OPC UA-mapping

Dette er central viden, hvis du skal arbejde med moderne edge-arkitektur, MQTT-kommunikation eller semantisk integration i industrielle netværk.

---

## 🛠️ Forudsætninger
Før du går i gang, skal du sikre at:

- Du har adgang til en Sparkplug B-kompatibel publisher (fx simulator, Node-RED publisher, eller edge-device)
- Du har en MQTT-broker, som du kan forbinde til (fx Mosquitto eller HiveMQ)
- Node-RED er installeret og har `mqtt-in`, `json`, `function` og `dashboard`-noder klar
- Du har gemt og dokumenteret din UNS-struktur fra Øvelse 3

---

## 🧩 Trin-for-trin opgave

### 1. Opret forbindelse og modtag Sparkplug B-data
- Opret en `mqtt-in` node og sæt den op til at abonnere på:
  - `spBv1.0/demo/DDATA/#` eller et mere specifikt device
- Forbind til din MQTT-broker på fx `mqtt://localhost:1883`
- Tilføj en `debug`-node og tjek at du modtager en `DDATA`-besked
- Bemærk:
  - Emneformatet: `spBv1.0/<group>/DDATA/<edge_node>/<device>`
  - Payload indeholder array af `metrics`

### 2. Identificér og udpak relevante metrikker
- Brug en `json`- eller `protobuf`-node, afhængigt af din dataformat
- Find i `msg.payload.metrics[]` de datapunkter du skal bruge
  - Fx: temperatur, tryk, ventilstatus
- For hver metric:
  - Notér navn, værdi, datatype, enhed og evt. timestamp

### 3. Transformér til UNS-format
- Opret en `function`-node, der transformerer hver metric til dit UNS-format

Eksempel:
```javascript
msg.payload = {
  topic: "fabrik_beta/hal1/linje3/plc01/temp_inlet/value",
  value: msg.payload.metrics[0].value,
  unit: "°C",
  timestamp: new Date().toISOString(),
  source: "sparkplug_b"
};
return msg;
```
- Hvis du arbejder med flere metrics:
  - Brug `switch`- eller `change`-noder til at håndtere hver metric individuelt
  - Eller lav en `forEach`-loop i function-node til at generere flere UNS-beskeder

### 4. Visualisér i dashboard og dokumentér arbejdet
- Brug følgende dashboard-noder:
  - `ui_text`, `ui_gauge`, `ui_table`, `ui_chart`
- Lav minimum 2 forskellige visualiseringer:
  - En måling (fx temperatur i °C)
  - En statusindikator (fx motor_status on/off)
- Gem:
  - Screenshot af dashboard
  - Dit Node-RED flow i `.json`
  - Eksempel på raw Sparkplug B og omformateret UNS payload

---

## 📋 Refleksion
- Hvordan adskiller Sparkplug B sig fra OPC UA med hensyn til emnestruktur og payload?
- Hvilke fordele og begrænsninger oplevede du med Sparkplug B?
- Passede dine emner og device-data godt ind i din UNS?
- Hvad var let, og hvad var vanskeligt ved at mappe Sparkplug?
- Hvordan ville du dokumentere og standardisere denne type integration i en virksomhed?

> 💡 Gem dine flows og noter. I næste øvelse skal du samle både OPC UA og Sparkplug B i ét samlet UNS-dashboard og evaluere, hvordan din UNS-struktur fungerer i praksis.

