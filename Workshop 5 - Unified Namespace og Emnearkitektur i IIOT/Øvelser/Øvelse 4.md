# 🧪 Øvelse 4: Mapping af OPC UA-data til Unified Namespace (UNS)

## 🎯 Formål
I denne øvelse skal du omsætte din teoretiske UNS-struktur fra Øvelse 3 til praksis ved at mappe realtidsmålinger fra en OPC UA-server ind i det emnehierarki, du selv har designet. Dette er en central færdighed i ethvert moderne IIOT-projekt, hvor man ønsker at skabe en fælles, semantisk rig datastruktur på tværs af forskellige systemer og protokoller.

Ved at arbejde med faktiske datapunkter fra en OPC UA-server vil du:
- Få praktisk erfaring med dataudtræk via OPC UA-klienter
- Træne konvertering og berigelse af rå data med metadata
- Øve integration og formatering af data i henhold til en UNS
- Validere hvorvidt din UNS-struktur er brugbar, skalerbar og forståelig

Denne øvelse er fundamentet for at kunne opbygge et solidt og genanvendeligt datagrundlag i produktionsmiljøer og for at skabe forbindelse mellem edge, automation og it-systemer.

---

## 🛠️ Forudsætninger
- Du har afsluttet Øvelse 3 og har en dokumenteret UNS-struktur
- Du har adgang til en aktiv OPC UA-server, f.eks. Prosys, NodeOPCUA, CODESYS, eller PLCsim Advanced
- Node-RED er installeret, og `node-red-contrib-opcua` er tilføjet og testet
- Du har grundlæggende erfaring med inject-, debug- og function-noder i Node-RED

---

## 🧩 Trin-for-trin opgave

### 1. Etabler forbindelse til OPC UA-server
- Start din OPC UA-server og tjek, at den er tilgængelig (fx via UAExpert)
- Konfigurer en `opcua-client`-node i Node-RED
  - Endpoint URI: fx `opc.tcp://localhost:4840` eller IP-adresse hvis ekstern
  - Sæt klienten til at læse værdier kontinuerligt (poll fx hvert 5. sekund)
- Brug `inject`-node til manuelt at trigge dataudtræk for test
- Brug `debug`-node til at se raw output i Node-RED

### 2. Udvælg datapunkter
- Find mindst 3 relevante `NodeId`’er i dit OPC UA-serverhierarki
  - Fx: `ns=2;s=Sensorenhed/Temperatur`, `ns=4;s=Tankniveau`, `ns=3;s=Ventil/Status`
- Notér for hver:
  - NodeId
  - Måleparameter (temperatur, tryk, status, m.m.)
  - Enhed (°C, %, boolean, etc.)
  - Typisk opdateringsinterval

### 3. Map data til din UNS
- For hvert datapunkt:
  - Opret en `function`-node der modtager OPC UA output og omskriver det til dit UNS-format
  - Brug dit emnehierarki fra Øvelse 3 som skabelon

Eksempel på mapping:
```javascript
msg.payload = {
  topic: "fabrik_alpha/hal2/linje1/plc_main/temp_supply/value",
  value: msg.payload.value.value,
  unit: "°C",
  timestamp: new Date().toISOString(),
  source: "opcua"
};
return msg;
```
- Tilføj evt. yderligere metadata såsom deviceID, statusflag, eller kvalitetsmærkning, hvis det findes i OPC UA-outputtet

### 4. Visualisér i dashboard og dokumentér
- Tilføj `ui_text`, `ui_gauge` eller `ui_chart`-noder til at vise dine UNS-mappede målinger
- Skab en logisk inddeling i dashboardet efter linjer, områder eller datakilde
- Gem følgende som dokumentation:
  - Screenshots af dashboard med realtidsdata
  - Udsnit af dine function-noder og flow-opbygning
  - Kort beskrivelse af hvilke datapunkter du mappede, og hvorfor du valgte dem

---

## 📋 Refleksion
Skriv en refleksion over arbejdet, hvor du adresserer:
- Hvordan oplevede du processen med at mappe OPC UA-data til dit eget emnehierarki?
- Hvor let eller svært var det at matche UNS-strukturen med OPC UA’s node-struktur?
- Skulle du ændre i din UNS, og hvad betød det for din forståelse af struktur og navngivning?
- Hvad har du lært om praktisk integration af semantik i datakommunikation?
- Hvordan vil du fremadrettet dokumentere og genbruge denne type integration?

> 💡 Husk at gemme hele dit flow og de `function`-noder du har lavet. Du skal bruge dem i næste øvelse, hvor du skal gøre det samme med data fra Sparkplug B og sammenligne integrationen.
