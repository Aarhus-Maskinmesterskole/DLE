# 🧪 Øvelse 1: Metadata og semantik i UNS og payloads

## 🎯 Formål
Formålet med denne øvelse er at give dig en grundlæggende og praksisnær introduktion til, hvordan **metadata** og **semantik** anvendes i arbejdet med **Unified Namespace (UNS)** og datastrømme i IIOT-systemer. Du skal lære, hvordan data ikke kun transporteres – men også **beriges med information, der forklarer hvad det er, hvor det kommer fra, hvordan det skal tolkes og hvorfor det er vigtigt**.

Ved at arbejde med struktureret metadata og semantisk tydelighed i både emner (topics) og payloads, opnår du:
- Højere forståelse og klarhed på tværs af faggrupper og systemer
- Nem fejlfinding og vedligeholdelse i større løsninger
- Forberedelse til interoperabilitet og automatiseret systemforståelse (discovery)
- En praksisorienteret tilgang til **data governance** og kvalitetssikring

Denne øvelse danner fundamentet for resten af Workshop 7, hvor metadata og semantik løbende indgår som centrale principper.

---

## 📖 Teori
**Metadata** betyder helt grundlæggende "data om data" – altså information, der beskriver og kontekstualiserer rå måleværdier eller statustilstande. I en industriel sammenhæng kan metadata gøre det muligt for både mennesker og systemer at forstå:
- Hvad der måles
- Hvordan det måles
- Hvem der måler det
- Hvilket format det foreligger i
- Hvor aktuelt, troværdigt og relevant det er

### Eksempler på metadata:
- **Enhed**: °C, kPa, %, liter, etc.
- **Datatype**: float, int, string, bool
- **Beskrivelse**: hvad målingen repræsenterer
- **Sensor-ID eller kilde**: fx sensor_A1, PLC_02
- **Status / kvalitet**: valid, invalid, offline, estimated
- **Tidsstempel**: hvornår målingen blev taget

### UNS og metadata
I et godt designet UNS bør metadata være en integreret del af både **topic-strukturen** og **selve payload'en**:

**Eksempel på emne (topic):**
```
fabrik1/hal2/plc05/temperatur/value
```

**Eksempel på payload med metadata:**
```json
{
  "value": 23.7,
  "unit": "°C",
  "type": "float",
  "description": "Indetemperatur fra sensor A1",
  "source": "sensor_A1",
  "timestamp": "2024-06-03T09:45:00Z",
  "quality": "valid"
}
```
Metadata gør det ikke kun nemmere for systemet at forstå, hvad det modtager – det øger også **sporbarheden** og muligheden for automatisk fejl- og kvalitetskontrol.

---

## 🛠️ Praktisk opgave

### 1. Opret et flow med metadata
- Brug en `inject`-node som starter hvert 5 sekund
- Tilføj en `function`-node, hvor du genererer følgende struktur:
  - `value` (måling, fx 22.5)
  - `unit` (fx °C)
  - `type` (fx float)
  - `description` (fx “Temperatur fra luftindtag”) 
  - `source` (fx “sensor_LuftIndtag1”)
  - `timestamp` (brug `new Date().toISOString()`)
  - `quality` (fx “valid” eller “estimated”)

Eksempel:
```javascript
msg.payload = {
  value: Math.random() * 10 + 20,
  unit: "°C",
  type: "float",
  description: "Temperatur fra luftindtag",
  source: "sensor_LuftIndtag1",
  timestamp: new Date().toISOString(),
  quality: "valid"
};
return msg;
```

### 2. Visualisér metadata
- Brug `debug`-node til at vise hele payload'en
- Tilføj `ui_text`-noder, der viser:
  - Måling
  - Enhed
  - Kilde
  - Status
- Tilføj en `ui_table`, hvor hele objektet kan præsenteres som en oversigt
- Overvej at bruge `ui_icon` til at indikere `quality` (grøn = valid, rød = invalid)

### 3. Dokumentér og gem eksempel
- Gem dit flow som `.json` og tag et screenshot af:
  - Payload vist i debug
  - Dashboard med visualisering
- Skriv kort (5–10 linjer):
  - Hvilken værdi skabte metadata i dit flow?
  - Hvem får gavn af det – og hvornår?
  - Hvordan kan dette skaleres til 100+ emner i en fabrik?

---

## 📋 Refleksion
- Hvilke typer metadata er vigtigst for din branche, projekt eller case?
- Hvordan påvirker metadata samarbejdet mellem ingeniører, udviklere og analytikere?
- Kan man have for meget metadata – og hvordan holder man det balanceret?
- Hvad ville der ske, hvis metadata blev udeladt i en kritisk installation?
- Hvordan kan du bruge denne metode til at styrke datakvalitet, sikkerhed og dokumentation i fremtidige systemer?

> 💡 I næste øvelse skal du designe en fuldt dokumenteret UNS-struktur, hvor hvert datapunkt er beskrevet med metadata – både i topic og payload.

