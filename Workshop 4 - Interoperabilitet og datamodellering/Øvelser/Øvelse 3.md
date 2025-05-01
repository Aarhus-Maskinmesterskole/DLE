# 🧪 Øvelse 3: MQTT Sparkplug B – Opsætning og publish/subscribe

## 🎯 Formål
Formålet med denne øvelse er at give dig en grundig og praktisk introduktion til **MQTT Sparkplug B**, en industriel kommunikationsstandard som bygger oven på MQTT og tilføjer vigtig semantik, struktur og metadata. Hvor almindelig MQTT kun definerer transporten af data, sikrer Sparkplug B, at alle parter også forstår dataens betydning – dvs. semantisk interoperabilitet.

Denne øvelse vil give dig:
- Indblik i, hvordan Sparkplug B skaber en mere robust og struktureret måde at sende og modtage data på i IIOT-miljøer
- Praktisk erfaring med opsætning af en Sparkplug-kompatibel MQTT-broker
- Evnen til at publicere og abonnere på Sparkplug-topics med korrekt emnehierarki og payload-struktur
- Træning i at analysere og fortolke strukturerede Sparkplug-payloads og identificere enheder, sensorer, datatyper og metadata

---

## 🛠️ Forudsætninger
Før du går i gang, skal du have:
- Gennemført Øvelse 1 og 2 og have forståelse for MQTT og OPC UA
- Installeret Docker **eller** adgang til en MQTT-broker med Sparkplug B-understøttelse (fx HiveMQ, Chariot, Mosquitto med Sparkplug-support)
- En MQTT-klient klar – fx Node-RED, MQTT.fx eller Sparkplug-kompatible scripts

---

## 📦 Hvad er Sparkplug B?
Sparkplug B er en standard, udviklet af Eclipse Foundation, som strukturerer MQTT-topics og payloads med:
- Faste topic-formater
- Indlejret metadata
- Automatisk identifikation af devices og metrics
- Anvendelse af fødsels-/dødsbeskeder (birth/death)

Et typisk Sparkplug-topic ser sådan ud:
```
spBv1.0/<GroupID>/<MessageType>/<EdgeNodeID>/<DeviceID>
```

### 📋 Typer af Sparkplug-meddelelser
- `NBIRTH`: Node er online og sender initial konfiguration
- `DBIRTH`: Device er online og sender initial data
- `DDATA`: Almindelig datameddelelse (periodisk eller event-drevet)
- `NDEATH` / `DDEATH`: Signalerer at node eller device er offline

Payload består typisk af:
```json
{
  "metrics": [
    {
      "name": "temperature",
      "value": 22.4,
      "type": "float",
      "unit": "°C"
    }
  ],
  "seq": 1,
  "timestamp": 1685500000000
}
```

---

## 🔧 Praktisk – Trin-for-trin

### 1. Start en Sparkplug-kompatibel broker
Hvis du ikke har en broker kørende:
```bash
docker run -it -p 1883:1883 -p 9001:9001 eclipse/mosquitto
```
Hvis du har adgang til HiveMQ eller anden broker med Sparkplug-plugin, brug denne.

### 2. Udforsk Sparkplug-topics og payloads
- Brug MQTT.fx eller MQTT Explorer til at abonnere på:
```
spBv1.0/#
```
- Observer hvordan emnerne er struktureret og hvordan data organiseres som `metrics`
- Brug JSON Viewer til at læse payloads – bemærk `unit`, `type`, `source`, `seq` og `timestamp`

### 3. Simulér NBIRTH-meddelelse i Node-RED
- Lav en `inject` node, der sender følgende JSON-payload:
```json
{
  "metrics": [
    { "name": "temperature", "value": 22.4, "type": "float", "unit": "°C" },
    { "name": "humidity", "value": 58, "type": "int", "unit": "%" }
  ],
  "seq": 1,
  "timestamp": 1685500000000
}
```
- Brug en `JSON` node og forbind den til `mqtt out`
- Udfyld emne som: `spBv1.0/demo/NBIRTH/Edge_1/Device_A`

### 4. Opbyg dit eget Sparkplug-flow
- Brug `function` node til at danne struktureret Sparkplug-payload dynamisk
- Kombinér med `inject` og evt. `random`-generator til at simulere sensor-data
- Udfyld `mqtt-out` emne med korrekt format: `spBv1.0/demo/DDATA/Edge_1/Device_A`
- Tilføj `debug` og evt. `ui_table` til at visualisere modtagne metrics

### 5. Valgfrit: Kombinér med tidligere OPC UA-data
- Brug output fra Øvelse 2 og pak det om i Sparkplug-format
- Det viser hvordan interoperabilitet mellem OPC UA og Sparkplug kan se ud

---

## 📋 Refleksion
- Hvordan adskiller Sparkplug B sig fra almindelig MQTT?
- Hvilke fordele ser du ved fast struktur og standardiserede payloads?
- Hvordan understøtter Sparkplug interoperabilitet og forståelighed i større IIOT-systemer?
- Kunne du forestille dig at bruge dette i praksis – og i så fald, hvor?

> 💡 Du kommer i næste øvelse til at designe din egen datamodel baseret på den erfaring du får her – og vælge, hvorda
