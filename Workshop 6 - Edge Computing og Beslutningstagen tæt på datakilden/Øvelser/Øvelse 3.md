# 🧪 Øvelse 3: Pre-processing og filtrering af data på Edge

## 🎯 Formål
Denne øvelse fokuserer på at lære dig, hvordan du **forbehandler og filtrerer sensordata direkte på en edge-enhed**, inden data enten visualiseres, sendes til cloud eller lagres. I praksis betyder det, at du udvikler et lokalt flow, der reducerer unødig støj, fjerner ugyldige datapunkter og fremhæver kun de relevante informationer – og dermed **optimerer både båndbredde og beslutningskvalitet**.

Pre-processing på kanten (edge) gør det muligt at:
- Minimere belastningen på netværket
- Undgå overflødig datalagring
- Reagere hurtigt på afvigelser og mønstre
- Forbedre systemets skalerbarhed og robusthed

Du kommer til at arbejde med validering af data, filtrering på basis af ændringer, samt simplificerede statistiske teknikker som glidende gennemsnit og tærskelovervågning.

---

## 🧰 Forudsætninger
- Du har gennemført Øvelse 2 og har et fungerende flow i Node-RED
- Du modtager sensordata via `inject`, `mqtt-in`, eller fysisk sensor
- Du har installeret følgende noder: `function`, `switch`, `rbe`, `ui_`, `file`, `delay`
- Du har et aktivt dashboard og adgang til at gemme og læse flow-variabler (fx med `flow.set` og `flow.get`)

---

## 🧩 Trin-for-trin opgave

### 1. Valider og rens data
- Brug en `function`-node til at sikre, at data:
  - Indeholder en gyldig `value`
  - Ligger indenfor et forventet interval (fx 0–100)
  - Har en gyldig `timestamp` (kan tjekkes med `Date.parse()`)
- Eksempel på valideringsfunktion:
```javascript
if (!msg.payload.value || isNaN(msg.payload.value) || msg.payload.value < 0 || msg.payload.value > 100) {
  return null; // ugyldig data filtreres væk
}
msg.payload.valid = true;
return msg;
```

### 2. Anvend glidende gennemsnit (moving average)
- Brug `flow.set/get` til at opbevare de sidste 5–10 værdier
- Udregn gennemsnit og tilføj det som et nyt felt i payload
- Visualisér både den rå værdi og gennemsnittet i `ui_chart`

Eksempel:
```javascript
let buffer = flow.get("values") || [];
buffer.push(msg.payload.value);
if (buffer.length > 5) buffer.shift();
let avg = buffer.reduce((a, b) => a + b, 0) / buffer.length;
msg.payload.average = avg;
flow.set("values", buffer);
return msg;
```

### 3. Filtrér kun signifikante ændringer
- Brug `rbe` (report by exception) til kun at sende nyt output, hvis værdien har ændret sig markant
- Alternativ: opbyg en `function`, der kun sender videre, hvis forskellen til seneste værdi > 0.5

Eksempel:
```javascript
let previous = flow.get("last") || 0;
if (Math.abs(msg.payload.value - previous) > 0.5) {
  flow.set("last", msg.payload.value);
  return msg;
}
return null;
```

### 4. Visualisér forskellen mellem rå og filtreret data
- Opret en ny `ui_group` med to `ui_chart`-noder:
  - Én der viser rå data
  - Én der viser filtrerede eller pre-processerede data
- Brug farver, labels eller `ui_text` til at vise:
  - Om værdien er godkendt
  - Hvilket filter den passerede

### 5. (Bonus) Log filtrerede data til fil
- Brug en `file`-node i "append mode" til at logge kun validerede og pre-processerede datapunkter
- Formatér dem som CSV med `timestamp,value,average`

---

## 📋 Refleksion
Skriv en refleksion i 8–15 linjer omkring følgende spørgsmål:
- Hvad var den største forskel du bemærkede mellem rå og filtreret data?
- Hvilke datapunkter blev typisk fjernet – og hvorfor?
- Hvordan kunne dette filtreringsprincip anvendes i kritiske systemer (produktion, energi, sundhed)?
- Hvordan balancerer man mellem at filtrere støj og bevare nok information?
- Hvordan vil du sikre, at edge-logik altid er opdateret og dokumenteret korrekt?

> 💡 Husk at gemme dine `function`-noder og testresultater – i næste øvelse skal du implementere beslutningslogik baseret på thresholds og reagere automatisk, hvis noget går galt.

