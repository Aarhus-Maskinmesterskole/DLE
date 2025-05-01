# 🧪 Øvelse 1: Introduktion til interoperabilitet og semantik

## 🎯 Formål
Formålet med denne første øvelse i Workshop 4 er at give dig en grundlæggende og dybdegående forståelse for, hvad **interoperabilitet** og **semantisk datamodellering** betyder i industrielle IIOT-systemer. Du skal arbejde med teoretiske begreber og begynde at anvende dem på konkrete eksempler, så du bliver i stand til at forklare, hvorfor systemintegration kræver mere end bare datatransport – det kræver en fælles forståelse for betydningen af data.

Vi introducerer forskellen mellem **rå data** og **semantisk berigede data**, og du kommer til at analysere hvordan protokoller som MQTT, OPC UA og Sparkplug B understøtter eller ikke understøtter semantik. Øvelsen lægger fundamentet for de efterfølgende øvelser, hvor du skal implementere datamodeller og udveksle information på tværs af systemer.

---

## 📖 Teori (læses og anvendes)

### 🔗 Interoperabilitet
**Interoperabilitet** handler om, at systemer skal kunne tale sammen – ikke kun i form af, at data rent fysisk sendes og modtages, men at de også **forstår og fortolker data på samme måde**. Det er afgørende i miljøer hvor komponenter kommer fra forskellige leverandører, og hvor der bruges forskellige teknologier.

Man taler normalt om:
- **Syntaktisk interoperabilitet**: Der er enighed om struktur og format (f.eks. JSON eller XML), men ikke nødvendigvis betydning.
- **Semantisk interoperabilitet**: Systemerne forstår også hvad data **betyder** (f.eks. “23.4” som en temperatur i °C fra en bestemt sensor).

### 📦 Rå data vs. semantisk data
Forestil dig at en PLC sender `23.4` ud. Hvis modtageren ikke ved hvad det er, har vi kun rå data.

- **Rå data:** `23.4`
- **Semantisk beriget data:**
```json
{
  "value": 23.4,
  "unit": "°C",
  "device": "Vex350_3",
  "type": "temperature",
  "source": "AirSensor_1"
}
```

Ved at tilføje metadata, navngivning og struktur, får vi et datasæt som både mennesker og maskiner kan forstå uden at have kendskab til den specifikke kontekst.

### 🌐 Protokoller og semantik
| Protokol           | Syntaks | Indbygget semantik | Typisk brug |
|--------------------|--------|---------------------|-------------|
| MQTT               | ✔      | ❌ (kræver strukturering manuelt) | Let, pub/sub, fleksibel |
| OPC UA             | ✔      | ✔ (fuld datamodel og hierarki)   | Industriel automation |
| MQTT Sparkplug B   | ✔      | ✔ (foruddefineret payload og metadata) | Standardiseret MQTT IIOT |

---

## 🔄 Aktivitet
1. **Undersøg og beskriv forskelle**:
   - Find mindst to artikler, websider eller whitepapers som forklarer forskellen mellem syntaktisk og semantisk interoperabilitet.
   - Lav et lille sammendrag i dine egne ord med fokus på IIOT-kontexten.

2. **Eksempler på interoperabilitetsproblemer**:
   - Beskriv to realistiske situationer, hvor interoperabilitet fejler pga. manglende semantik. Fx: En temperaturværdi bliver tolket forkert fordi enheden er anderledes.
   - Giv forslag til hvordan semantisk berigelse (metadata, hierarki, struktur) kan løse problemet.

3. **Kort refleksion**:
   - Hvad forstår du ved begrebet **semantisk interoperabilitet**?
   - Hvorfor tror du det bliver vigtigere i takt med at flere systemer kobles sammen i IIOT?
   - Hvordan relaterer det sig til de sikkerheds- og kommunikationsproblemer du har arbejdet med i tidligere workshops?

---

## 📋 Aflevering (for denne øvelse)
Du skal aflevere en kort skriftlig refleksion (8–12 linjer) med:
- Din forklaring på forskellen mellem syntaktisk og semantisk interoperabilitet
- Et eller to eksempler på hvordan manglende semantik kan føre til fejl
- En vurdering af hvilken protokol du tror har størst fremtid i IIOT og hvorfor

Du må gerne supplere med figurer, tabeller eller egne illustrationer hvis du har lyst.

> 💡 Det du lærer her, bliver grundlag for de praktiske øvelser i Workshop 4, hvor du selv skal opbygge datamodeller og arbejde med interoperable protokoller som OPC UA og Sparkplug B.

