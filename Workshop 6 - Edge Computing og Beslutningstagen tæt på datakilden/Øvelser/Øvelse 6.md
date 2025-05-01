# 🧪 Øvelse 6: Anomali-detektion med glidende gennemsnit på Edge

## 🎯 Formål
Denne øvelse har til formål at introducere og implementere en effektiv metode til **anomali-detektion direkte på edge-enheder**, uden brug af cloud. Ved hjælp af en simpel statistisk teknik – **glidende gennemsnit (moving average)** – kan du identificere målinger, der afviger markant fra et forventet mønster, og dermed aktivere lokale alarmer og handlinger.

I moderne IIOT-systemer er hurtig og lokal detektion af unormale hændelser afgørende for både sikkerhed, kvalitet og effektivitet. Når det kombineres med edge computing, bliver det muligt at reagere i realtid – selv ved netværksfejl.

### Fordele ved lokal anomali-detektion:
- Hurtig reaktionstid uden netværksafhængighed
- Reduktion af datamængde, der skal sendes til cloud
- Øget systemrobusthed og selvstændighed
- Tidlig varsling om potentielle fejl eller uregelmæssigheder i proces eller udstyr

---

## 🧰 Forudsætninger
- Du har gennemført Øvelse 3–5 og har adgang til realtidsmålinger i dit edge-flow
- Du er fortrolig med brug af Node-RED og `function`-noder, `flow.set/get`, `switch`, `ui_`-komponenter
- Du har et dashboard oprettet og kan visualisere målinger
- Du har forståelse for hvad glidende gennemsnit er og hvordan det anvendes i signalbehandling og overvågning

---

## 🧩 Trin-for-trin opgave

### 1. Opret glidende gennemsnit (moving average)
- Brug en `function`-node til at holde styr på de sidste N målinger (fx 5–10 værdier)
- Beregn gennemsnittet og gem det i `msg.payload.avg`
- Husk at bruge `flow.get("buffer")` og `flow.set("buffer")`

```javascript
let buffer = flow.get("buffer") || [];
buffer.push(msg.payload.value);
if (buffer.length > 5) buffer.shift();
let avg = buffer.reduce((a, b) => a + b, 0) / buffer.length;
msg.payload.avg = avg;
flow.set("buffer", buffer);
return msg;
```

### 2. Sammenlign mod afvigelse fra gennemsnit
- Brug en ny `function`-node til at tjekke om målingen afviger med mere end fx 20 % fra gennemsnittet
- Hvis den gør, tilføjes `msg.payload.anomaly = true`

```javascript
let delta = Math.abs(msg.payload.value - msg.payload.avg);
let threshold = msg.payload.avg * 0.2;
msg.payload.delta = delta;
msg.payload.anomaly = delta > threshold;
return msg;
```

### 3. Visualisér anomali i dashboard
- Tilføj to kurver i `ui_chart`:
  - Blå for rå måling
  - Grøn for gennemsnit
- Tilføj `ui_led` eller `ui_icon`:
  - Grøn ved normal
  - Rød hvis `anomaly == true`
- Brug `ui_toast`-notifikation med tekst: "⚠ Anomali opdaget ved [værdi] °C!"

### 4. Log hændelser lokalt
- Brug `switch`-node til kun at sende videre, hvis `anomaly == true`
- Brug `file`-node til at gemme:
  - `timestamp,value,avg,delta,status`
- Gem som CSV i append mode, fx i `anomali_log.csv`

Eksempel på CSV-output:
```
2024-06-02T12:45:33Z,34.8,28.6,6.2,anomaly
```

### 5. (Bonus) Udvid logik med dynamisk tærskel
- Udregn standardafvigelse (std) på værdierne og erstat `0.2 * avg` med `1.5 * std`
- Brug `Math.sqrt()` til beregning:
```javascript
let std = Math.sqrt(buffer.map(x => Math.pow(x - avg, 2)).reduce((a,b) => a + b) / buffer.length);
```
- Eller eksperimentér med alternative teknikker:
  - Z-score
  - EWMA (Exponential Weighted Moving Average)
  - Min/max-registrering over tid

---

## 📋 Refleksion
- Hvor følsom var din algoritme – og hvor mange falske alarmer opstod?
- Hvor hurtigt kunne anomalien detekteres?
- Hvilken fordel giver det, at denne logik ligger på edge fremfor cloud?
- Hvornår er simple heuristikker nok – og hvornår kræves maskinlæring?
- Hvordan ville du kommunikere en anomali fra edge til operatør eller cloud?
- Hvordan kan du bruge denne teknik i din fremtidige praksis, fag eller branche?

> 💡 Husk: selv simple regler kan redde processer og maskiner, hvis de ligger tæt på datakilden. Brug denne øvelse som trædesten til mere avancerede edge-analysemodeller i dit næste projekt!

