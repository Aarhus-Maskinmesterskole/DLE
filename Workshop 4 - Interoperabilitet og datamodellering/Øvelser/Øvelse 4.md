# 🧪 Øvelse 4: Design din egen semantiske datamodel

## 🎯 Formål
I denne øvelse skal du anvende din viden fra de foregående øvelser til at **designe en komplet semantisk datamodel** for et IIOT-system. Du skal kombinere strukturelle principper fra OPC UA og den standardiserede payloadstruktur fra Sparkplug B for at skabe en datamodel, der både er teknisk robust, semantisk klar og let at integrere på tværs af forskellige systemer.

Formålet er at:
- Træne dig i at tænke hierarkisk og semantisk i opbygning af systemer.
- Forstå hvordan emnestruktur og metadata påvirker genanvendelighed og interoperabilitet.
- Udvikle evnen til at specificere og dokumentere datastrømme klart og entydigt.

Din datamodel vil fungere som et blueprint, der i princippet kan implementeres i både OPC UA namespace og som Sparkplug B-metrics.

---

## 🛠️ Forudsætninger
Inden du går i gang, skal du have:
- Gennemført Øvelse 1 (interoperabilitet og semantik)
- Arbejdet med OPC UA i Øvelse 2 og set hvordan tags og nodes opbygges
- Arbejdet med Sparkplug B i Øvelse 3 og forstået emnestruktur og payloadindhold
- Grundlæggende forståelse for datatyper, enheder, og hierarkier i tekniske systemer

---

## 🔧 Praktisk – Trin-for-trin

### 1. Vælg kontekst og use-case
- Beslut hvilket type IIOT-system du vil modellere. Det kan fx være:
  - Et varmeanlæg med tre temperatursensorer og en styret ventil
  - En ventilationsenhed med tryk-, fugt- og CO₂-sensorer
  - Et mindre procesanlæg med flowmåling og tankniveau

Formålet er at vælge et overskueligt, men realistisk eksempel, hvor man kan demonstrere brug af både semantik og hierarki.

### 2. Opbyg din enhedshierarki (struktur)
- Definér den fysiske og logiske struktur:
  - Bygning, lokation eller procesområde
  - System (varme, ventilation, proces)
  - Undersystem eller enhed (sensor, aktuator)

Eksempelstruktur:
```
Bygning A
├── Etage 2
│   └── Teknikrum 4
│       └── Ventilation
│           ├── CO2Sensor_1
│           ├── TempSensor_2
│           └── DamperActuator_1
```
Du må gerne tegne som skitse eller strukturdiagram.

### 3. Specificér datapunkter og metadata (semantik)
For hvert datapunkt (sensor eller aktuator), angiv følgende:
- Navn (f.eks. "co2_level")
- Enhed (ppm, °C, %, Pa, etc.)
- Datatype (int, float, bool, string)
- Beskrivelse (hvad måler den?)
- Evt. kategori (måling, styring, alarm)
- DeviceID og lokaliseringsreference hvis relevant

Lav en tabel eller JSON-struktur der beskriver 3–5 datapunkter.

### 4. Design Sparkplug B-kompatibel payload
Opret et JSON-eksempel på et `DDATA` payload med flere metrics:
```json
{
  "metrics": [
    {
      "name": "co2_level",
      "value": 425,
      "type": "int",
      "unit": "ppm",
      "description": "CO2 i mødelokale A"
    },
    {
      "name": "temp_supply",
      "value": 21.7,
      "type": "float",
      "unit": "°C",
      "description": "Indblæsningstemperatur"
    },
    {
      "name": "damper_position",
      "value": 88,
      "type": "int",
      "unit": "%",
      "description": "Spjældåbning"
    }
  ],
  "seq": 5,
  "timestamp": 1685512345000
}
```
Forklar hvilke enheder og datatyper du har valgt og hvorfor.

### 5. Visualisér model og navngivning
- Udarbejd enten en UML-diagram, en JSON-schema, en tabelformat eller visuel skitse
- Fokusér på:
  - Topic-struktur eller Node-hierarki
  - Konsistens i navngivning og enhedsvalg
  - Relation mellem fysisk verden og datamodellen

---

## 📋 Refleksion
Besvar følgende spørgsmål i en kort tekst eller bullet points:
- Hvordan valgte du struktur og navngivning?
- Hvordan adskiller din model sig fra rå JSON eller ad hoc-MQTT?
- Hvilke data er vigtige at dokumentere som metadata?
- Hvad skal der til for at din model kan bruges både i OPC UA og i Sparkplug?
- Hvordan vil din model understøtte genanvendelighed, fejlsøgning og visualisering?

> 💡 I næste øvelse skal du sammenligne protokoller og strukturer: Hvad fungerer bedst hvornår, og hvordan understøtter forskellige standarder forskellige behov?

