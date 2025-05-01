# 🧪 Øvelse 2: OPC UA – Opsætning af server og klient

## 🎯 Formål
Denne øvelse introducerer dig til praktisk brug af **OPC UA**, som er en af de mest udbredte industrielle kommunikationsstandarder med indbygget semantik og sikkerhed. Målet er at give dig erfaring med at:
- Starte og konfigurere en OPC UA-server
- Udforske serverens strukturerede datamodeller
- Forbinde og læse data fra en OPC UA-klient

Du kommer til at se forskellen på rå og semantisk data i praksis, og får indblik i hvordan OPC UA understøtter hierarkier, metadata og datatyper direkte i protokollen.

---

## 🛠️ Forudsætninger
- Du har læst og arbejdet med Øvelse 1
- Du har Node-RED installeret med `node-red-contrib-opcua`
- Du har adgang til en OPC UA-simulationsserver (fx Prosys Simulation Server, Node-OPCUA, eller en lokal docker-container)

---

## 🔧 Praktisk (step-by-step)

### 1. Start en OPC UA-server
- Brug fx Prosys OPC UA Simulation Server eller en docker-container
- Notér serverens adresse (URI), fx:
  - `opc.tcp://localhost:4840`
  - eller `opc.tcp://192.168.1.100:4840`

### 2. Udforsk serverens struktur
- Brug Prosys eller Unified Automation UAExpert til at browse serverens namespace
- Find en simpel node: fx `ns=2;s=Dynamic/RandomInt32`
- Bemærk:
  - NodeId
  - DisplayName
  - DataType
  - Description

### 3. Forbind fra Node-RED
- Tilføj en `opcua-client` node
- Konfigurer endpoint og vælg "read"-mode
- Brug `inject` node til at trigge læsning (fx hver 5 sekunder)
- Brug `debug` eller `function` node til at vise output

### 4. Berig output
- Tilføj metadata som:
```javascript
msg.payload = {
  value: msg.payload.value.value,
  timestamp: new Date().toISOString(),
  source: "OPCUA_Simulator",
  node: "Dynamic/RandomInt32"
};
return msg;
```

### 5. Dokumentér
- Gem screenshot af:
  - OPC UA-browser med namespace
  - Node-RED flow og output

---

## 📋 Refleksion
- Hvad er forskellen på dette og at læse data via MQTT?
- Hvilken information får du “gratis” med OPC UA?
- Hvordan understøtter OPC UA semantisk interoperabilitet?

> 💡 Du kommer til at bruge OPC UA-output i senere øvelser, hvor du kombinerer det med Sparkplug B og visualisering.

