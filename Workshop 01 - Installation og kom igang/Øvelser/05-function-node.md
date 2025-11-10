# 🔧 Function Node - Opgaver

Function-noden i Node-RED giver dig mulighed for at skrive JavaScript-kode til at behandle, transformere og træffe beslutninger baseret på dine data. Her er 10 opgaver, der træner dig i logik og databehandling.

---

## 1️⃣ Opgave 1: Simpel Temperaturkonvertering

**Formål:** Konverter Celsius til Fahrenheit

**Opgave:**
- Opret en Inject-node der sender et tal (fx 25) som repræsenterer grader Celsius
- Brug en Function-node til at konvertere til Fahrenheit med formlen: `F = (C × 9/5) + 32`
- Vis resultatet i en Debug-node

**Forventet output:**  
Input: `25` → Output: `77`

**Hjælp:**
```javascript
var celsius = msg.payload;
var fahrenheit = (celsius * 9/5) + 32;
msg.payload = fahrenheit;
return msg;
```

---

## 2️⃣ Opgave 2: Grænseværdi Alarm

**Formål:** Trigger en alarm hvis en værdi overskrider en grænse

**Opgave:**
- Opret en Inject-node der sender forskellige tal (fx 15, 35, 50)
- Brug en Function-node til at tjekke om værdien er over 30
- Hvis værdien er over 30, sæt `msg.payload = "ALARM: Temperatur for høj!"`
- Hvis værdien er under 30, sæt `msg.payload = "OK: Temperatur normal"`
- Vis resultatet i Debug

**Hjælp:**
```javascript
var temp = msg.payload;

if (temp > 30) {
    msg.payload = "ALARM: Temperatur for høj!";
} else {
    msg.payload = "OK: Temperatur normal";
}

return msg;
```

---

## 3️⃣ Opgave 3: Minimum, Maximum og Gennemsnit

**Formål:** Beregn statistik fra et array af tal

**Opgave:**
- Opret en Inject-node der sender et array: `[10, 25, 30, 15, 20]`
- Brug en Function-node til at beregne:
  - Minimum værdi
  - Maximum værdi
  - Gennemsnit
- Returner et objekt med alle tre værdier

**Forventet output:**
```json
{
  "min": 10,
  "max": 30,
  "average": 20
}
```

**Hjælp:**
```javascript
var values = msg.payload;

var min = Math.min(...values);
var max = Math.max(...values);
var sum = values.reduce((a, b) => a + b, 0);
var average = sum / values.length;

msg.payload = {
    min: min,
    max: max,
    average: average
};

return msg;
```

---

## 4️⃣ Opgave 4: Tidsstempling

**Formål:** Tilføj timestamp og metadata til data

**Opgave:**
- Opret en Inject-node der sender en temperatur (fx 23.5)
- Brug en Function-node til at tilføje:
  - Nuværende timestamp (ISO format)
  - Enhed (°C)
  - Sensor ID (fx "TEMP_SENSOR_01")
- Returner et komplet objekt

**Forventet output:**
```json
{
  "value": 23.5,
  "unit": "°C",
  "timestamp": "2025-11-10T14:30:00.000Z",
  "sensorId": "TEMP_SENSOR_01"
}
```

**Hjælp:**
```javascript
var temperature = msg.payload;

msg.payload = {
    value: temperature,
    unit: "°C",
    timestamp: new Date().toISOString(),
    sensorId: "TEMP_SENSOR_01"
};

return msg;
```

---

## 5️⃣ Opgave 5: Filtrering af Outliers

**Formål:** Fjern urealistiske målinger (sanity check)

**Opgave:**
- Opret en Inject-node der sender forskellige temperaturer (fx 22, 150, -50, 25)
- Brug en Function-node til at filtrere værdier:
  - Kun accepter værdier mellem 0 og 50 grader
  - Hvis værdien er ugyldig, returner `null` eller en fejlbesked
  - Hvis værdien er gyldig, returner den originale værdi

**Hjælp:**
```javascript
var temp = msg.payload;

// Tjek om temperaturen er realistisk
if (temp < 0 || temp > 50) {
    msg.payload = {
        error: "Outlier detected",
        value: temp,
        reason: "Temperature out of range (0-50°C)"
    };
} else {
    msg.payload = {
        status: "OK",
        value: temp
    };
}

return msg;
```

---

## 6️⃣ Opgave 6: Tæller og Status Tracker

**Formål:** Tæl antal gange en knap er trykket

**Opgave:**
- Opret en Inject-node der kan trykkes gentagne gange
- Brug en Function-node til at:
  - Tælle antal tryk (brug `context` til at gemme tæller)
  - Vise antal tryk i payload
  - Nulstil tæller hvis værdien når 10

**Hjælp:**
```javascript
// Hent tæller fra context (husker mellem kald)
var count = context.get('buttonCount') || 0;

// Increment tæller
count = count + 1;

// Nulstil ved 10
if (count >= 10) {
    count = 0;
}

// Gem tæller tilbage i context
context.set('buttonCount', count);

msg.payload = {
    clicks: count,
    status: count >= 8 ? "Warning: Almost at limit" : "OK"
};

return msg;
```

---

## 7️⃣ Opgave 7: Multi-Sensor Data Kombination

**Formål:** Kombiner data fra flere sensorer

**Opgave:**
- Opret en Inject-node der sender et objekt med flere sensorer:
  ```json
  {
    "temp1": 22,
    "temp2": 24,
    "temp3": 23
  }
  ```
- Brug en Function-node til at:
  - Beregne gennemsnitstemperatur
  - Finde den højeste temperatur
  - Markere hvis nogen sensor afviger mere end 3 grader fra gennemsnittet

**Hjælp:**
```javascript
var sensors = msg.payload;

// Hent alle værdier
var temps = Object.values(sensors);

// Beregn gennemsnit og max
var average = temps.reduce((a, b) => a + b, 0) / temps.length;
var max = Math.max(...temps);

// Tjek for afvigelser
var warnings = [];
for (var key in sensors) {
    if (Math.abs(sensors[key] - average) > 3) {
        warnings.push(key + " afviger fra gennemsnit");
    }
}

msg.payload = {
    average: average.toFixed(2),
    max: max,
    warnings: warnings.length > 0 ? warnings : "Ingen afvigelser"
};

return msg;
```

---

## 8️⃣ Opgave 8: Besked Routing (Multiple Outputs)

**Formål:** Send data til forskellige outputs baseret på værdi

**Opgave:**
- Opret en Inject-node der sender et tal (fx 15, 35, 55)
- Brug en Function-node med **3 outputs** til at route beskeder:
  - Output 1: Hvis værdi < 30 (LAV)
  - Output 2: Hvis værdi 30-50 (NORMAL)
  - Output 3: Hvis værdi > 50 (HØJ)
- Tilslut hver output til en Debug-node med forskellig navn

**Konfiguration:**
- I Function-node settings, sæt "Outputs" til `3`

**Hjælp:**
```javascript
var value = msg.payload;

if (value < 30) {
    // Send til output 1
    msg.payload = "LAV: " + value;
    return [msg, null, null];
} else if (value >= 30 && value <= 50) {
    // Send til output 2
    msg.payload = "NORMAL: " + value;
    return [null, msg, null];
} else {
    // Send til output 3
    msg.payload = "HØJ: " + value;
    return [null, null, msg];
}
```

---

## 9️⃣ Opgave 9: Tidsforsinkelse Detektor

**Formål:** Beregn tid mellem to hændelser

**Opgave:**
- Opret en Inject-node der kan trykkes to gange
- Brug en Function-node til at:
  - Gemme tidspunktet for første tryk
  - Ved andet tryk, beregn tiden mellem de to tryk
  - Vis tid i sekunder

**Hjælp:**
```javascript
// Hent sidste timestamp fra context
var lastTime = context.get('lastClickTime');
var currentTime = Date.now();

if (lastTime === undefined) {
    // Første tryk
    context.set('lastClickTime', currentTime);
    msg.payload = "Første tryk registreret. Tryk igen for at måle tid.";
} else {
    // Andet tryk - beregn forskel
    var timeDiff = (currentTime - lastTime) / 1000; // Konverter til sekunder
    
    msg.payload = {
        message: "Tid mellem tryk",
        seconds: timeDiff.toFixed(2),
        milliseconds: currentTime - lastTime
    };
    
    // Nulstil for næste måling
    context.set('lastClickTime', undefined);
}

return msg;
```

---

## 🔟 Opgave 10: Data Buffer og Batch Processing

**Formål:** Saml flere målinger og send som batch

**Opgave:**
- Opret en Inject-node der sender temperaturer med interval (fx hvert 2. sekund)
- Brug en Function-node til at:
  - Opsamle de sidste 5 målinger i et array
  - Når 5 målinger er samlet, send dem videre som et batch
  - Beregn gennemsnit af batchen

**Hjælp:**
```javascript
// Hent buffer fra context
var buffer = context.get('dataBuffer') || [];

// Tilføj ny måling
buffer.push(msg.payload);

// Tjek om vi har 5 målinger
if (buffer.length >= 5) {
    // Beregn gennemsnit
    var sum = buffer.reduce((a, b) => a + b, 0);
    var average = sum / buffer.length;
    
    msg.payload = {
        batch: buffer,
        count: buffer.length,
        average: average.toFixed(2),
        timestamp: new Date().toISOString()
    };
    
    // Nulstil buffer
    context.set('dataBuffer', []);
    
    return msg;
} else {
    // Gem buffer og vent på flere målinger
    context.set('dataBuffer', buffer);
    
    // Return null = send ingen besked videre
    msg.payload = "Buffer: " + buffer.length + "/5 målinger";
    return msg;
}
```

---

## 🎯 Bonusopgave: Kombiner Det Hele!

**Udfordring:**  
Lav et komplet flow der:
1. Modtager sensordata (temperatur)
2. Tilføjer timestamp og metadata
3. Filtrerer outliers (0-50°C)
4. Opsamler 5 målinger i buffer
5. Beregner statistik (min, max, average)
6. Router data baseret på gennemsnit (<30, 30-50, >50)
7. Sender alarm hvis gennemsnit > 40

**Tips:**
- Du kan bruge flere Function-noder efter hinanden
- Eller kombiner alt logikken i én Function-node
- Brug comments i koden til at strukturere

---

## 📚 Vigtige JavaScript Koncepter

### Context Storage
```javascript
// Gem værdi (husker mellem kald)
context.set('variabelNavn', værdi);

// Hent værdi
var værdi = context.get('variabelNavn');

// Hent med default værdi
var værdi = context.get('variabelNavn') || 0;
```

### Multiple Outputs
```javascript
// Return array med besked til hver output
return [msg1, msg2, msg3];

// null = ingen besked til den output
return [msg, null, null];
```

### Array Metoder
```javascript
// Reducer (sum)
var sum = array.reduce((a, b) => a + b, 0);

// Map (transformer)
var doubled = array.map(x => x * 2);

// Filter
var filtered = array.filter(x => x > 10);

// Min/Max
var min = Math.min(...array);
var max = Math.max(...array);
```

### Timestamp
```javascript
// ISO format
new Date().toISOString()

// Unix timestamp (millisekunder)
Date.now()

// Formateret
new Date().toLocaleString('da-DK')
```

---

## ✅ Tjekliste

Efter at have gennemført alle opgaver kan du:
- [ ] Skrive JavaScript i Function-node
- [ ] Bruge if/else logik
- [ ] Arbejde med arrays og objekter
- [ ] Gemme data med context
- [ ] Håndtere multiple outputs
- [ ] Tilføje timestamps
- [ ] Filtrere og validere data
- [ ] Beregne statistik
- [ ] Buffer og batch data
- [ ] Kombinere kompleks logik

---

**Held og lykke! 🚀 Når du mestrer Function-node, kan du lave næsten alt i Node-RED!**
