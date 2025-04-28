# 📝 Øvelse 3: HTTP/REST API kommunikation i Node-RED

## 🌟 Formål
Formålet med denne øvelse er at introducere de studerende til anvendelse af HTTP/REST API'er til dataopsamling i IIOT-systemer. Fokus er på at sende forespørgsler til eksterne API'er, modtage svar, parse data og integrere informationen i Node-RED-flows.

---

## 📖 Teori (læs først)

**Hvad er HTTP/REST?**
- **HTTP (Hypertext Transfer Protocol)** er en af de ældste og mest anvendte protokoller til overførsel af information på internettet.
- **REST (Representational State Transfer)** er en arkitekturstil, der anvender HTTP til at hente eller sende data.
- REST API'er tilbyder et standardiseret måde at kommunikere mellem enheder og systemer på ved brug af HTTP-metoder som GET, POST, PUT og DELETE.

**Grundbegreber:**
- **Client:** Den enhed, der sender en forespørgsel (fx Node-RED).
- **Server:** Den tjeneste, der leverer svar på forespørgsler.
- **GET:** Bruges til at hente data.
- **POST:** Bruges til at sende nye data.
- **JSON:** Det mest almindelige dataformat for svar.

**Hvorfor bruge HTTP/REST i IIOT?**
- Muliggør adgang til et væld af åbne og private datakilder.
- Understøtter integration med cloud-tjenester og eksterne databaser.
- Standardiseret og velunderstøttet protokol.

**Eksempler på brug:**
- Hente vejrdata til energistyringssystemer.
- Hente driftsdata fra eksterne services.
- Kommunikere med cloudbaserede IoT-platforme.

---

## 🔧 Forudsætninger

For at kunne gennemføre denne øvelse, skal følgende være klar:

- Node-RED installeret og adgang til internettet.
- En API-tjeneste der tillader offentlige forespørgsler, eksempelvis:
  - OpenWeatherMap (vejrdata)
  - jsonplaceholder.typicode.com (testdata)

Ingen API-nøgle er nødvendig for standard GET-anmodninger i denne øvelse.

---

## 🔄 Praktisk (step-by-step)

### 1. Start Node-RED
- Start Node-RED og åbn `http://localhost:1880` i din browser.

### 2. Opsæt HTTP Request-flow
- Træk en `inject` node ind.
- Konfigurer `inject` node:
  - Payload: **timestamp**
  - Interval: fx hvert 5. minut.

- Træk en `http request` node ind.
- Konfigurer `http request` node:
  - URL: Eksempelvis `https://api.open-meteo.com/v1/forecast?latitude=55.6761&longitude=12.5683&current_weather=true`
  - Method: GET

- Tilføj en `json` node (hvis nødvendig) for at parse JSON-responsen.

- Tilføj en `function` node til at hente specifik data:
  - Navn: "Udtræk temperatur"
  - Funktion:
    ```javascript
    let weather = JSON.parse(msg.payload);
    msg.payload = {
      temperatur: weather.current_weather.temperature,
      timestamp: new Date().toISOString()
    };
    return msg;
    ```

- Træk en `debug` node ind og forbind.
- Flow: `inject` -> `http request` -> `json` (hvis nødvendig) -> `function` -> `debug`

### 3. Deploy flowet
- Klik "Deploy" for at starte flowet.

### 4. Test kommunikationen
- Tjek debug-vinduet:
  - Bekræft at du modtager temperatur og timestamp korrekt.

### 5. Fejlhåndtering
- Hvis ingen data modtages:
  - Kontrollér URL.
  - Kontrollér internetforbindelse.
  - Se efter fejlbeskeder i debug-vinduet.

### 6. Gem arbejdet
- Eksporter flowet som en `.json`-fil til aflevering.

### 7. Bonus: Variabel URL (valgfri)
- Udvid flowet med en `template` node til dynamisk at ændre URL baseret på brugerinput (f.eks. anden by).

---

# 💡 Noter
- Data skal altid være **tidsstemplet**.
- Husk at API'er kan ændre deres struktur, så vær fleksibel i din parsing.
- Dokumentér hvordan du testede flowet, og hvilke fejl der evt. opstod.
- Overvej hvordan realtidsdata fra API'er kan bruges i beslutningsstøttesystemer i IIOT.

---

# 🎉 Klar til næste øvelse!
Når denne øvelse er gennemført, fortsæt til Øvelse 4: CoAP kommunikation, hvor vi arbejder med en let protokol beregnet til små enheder i IIOT-systemer.
