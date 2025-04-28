# 📝 Øvelse 1: MQTT kommunikation i Node-RED

## 🌟 Formål
Formålet med denne øvelse er at give de studerende en grundlæggende forståelse af MQTT-protokollen og dens anvendelse i IIOT-systemer. Fokus er på at opsætte en komplet datastrøm i Node-RED, hvor data publiceres, abonneres, tidsstemples og monitoreres korrekt. Derudover introduceres grundlæggende fejlhåndteringsteknikker for at sikre pålidelig drift.

---

## 📖 Teori (læs først)

**Hvad er MQTT?**
- MQTT (Message Queuing Telemetry Transport) er en ekstremt letvægtsprotokol udviklet til effektiv og pålidelig kommunikation i netværk med begrænset båndbredde og høje latensforhold.
- Den anvender et **publish/subscribe**-mønster, hvilket betyder, at enheder ikke kommunikerer direkte, men via en central broker.

**Nøglekomponenter:**
- **Broker:** Hovedserveren, der modtager beskeder fra publishers og distribuerer dem til subscribers.
- **Client:** Enhver enhed, der enten sender (publisher) eller modtager (subscriber) beskeder.

**Fordele ved MQTT:**
- Minimal netværksbelastning
- Hurtig og pålidelig levering af beskeder
- Skalerbar til tusindvis af enheder
- Understøtter "Last Will and Testament" for fejlhåndtering

**Eksempler på brug:**
- Fjernovervågning af energiforbrug
- Live rapportering fra sensorer i produktionsanlæg
- Smart City applikationer (trafiklys, miljøsensorer)

---

## 🔧 Forudsætninger

For at kunne gennemføre denne øvelse, skal følgende software være installeret og køreklar:

- Node-RED installeret lokalt på PC eller i Docker.
- MQTT broker installeret:
  - Installér **Mosquitto** lokalt:
    - Linux: `sudo apt install mosquitto mosquitto-clients`
    - Windows: Brug Mosquitto Windows installer fra Eclipse hjemmeside.
    - Docker: `docker run -it -p 1883:1883 eclipse-mosquitto`
  - Alternativ: Brug en offentlig MQTT broker (eks. `test.mosquitto.org`).

---

## 🔄 Praktisk (step-by-step)

### 1. Start Node-RED
- Start Node-RED-tjenesten.
- Åbn browser og gå til `http://localhost:1880`.

### 2. Opsæt Publish-flow
- Træk en `inject` node ind på arbejdsfladen.
- Konfigurer `inject` node:
  - Payload type: **string**
  - Værdi: eksempelvis `25`
  - Interval: Hvert 5. sekund.

- Tilføj en `function` node:
  - Navn: "Tilføj timestamp"
  - Funktion:
    ```javascript
    msg.payload = {
      temperatur: msg.payload,
      timestamp: new Date().toISOString()
    };
    return msg;
    ```

- Træk en `mqtt out` node ind:
  - Konfigurer med broker information.
  - Topic: eksempelvis `sensor/temperatur`.

- Forbind `inject` -> `function` -> `mqtt out`.

### 3. Opsæt Subscribe-flow
- Træk en `mqtt in` node ind.
- Konfigurer til samme broker.
- Lyt på topic `sensor/temperatur`.

- Træk en `debug` node ind og forbind til `mqtt in` node.

### 4. Deploy flowet
- Klik på "Deploy" for at gemme ændringerne og starte flows.

### 5. Test kommunikationen
- Monitorer debug-vinduet:
  - Bekræft modtagelse af JSON-objekter indeholdende temperatur og tidsstempel.

### 6. Fejlhåndtering
- Hvis ingen beskeder modtages:
  - Kontrollér, at broker IP og port er korrekte.
  - Kontrollér, at topic-navne matcher eksakt (case-sensitive).
  - Brug "status" nodes for at spore forbindelsesproblemer.

### 7. Gem arbejdet
- Eksporter flowet som en `.json`-fil:
  - Brug "Export" > "Clipboard" i Node-RED menuen.
  - Gem til en lokal fil for aflevering.

### 8. Bonus: Tilføj Heartbeat/Watchdog (valgfri)
- Lav en ekstra `inject` node som sender "alive" besked hvert 10. sekund til topic `sensor/heartbeat`.
- Brug en `trigger` node til at alarmere, hvis heartbeat ikke modtages rettidigt.

---

# 💡 Noter
- Data skal altid være **tidsstemplet**.
- Der skal implementeres **grundlæggende fejlhåndtering**.
- Dokumentér testforløbet:
  - Hvordan du testede flows.
  - Eventuelle fejl og løsninger.
- Reflektér over fordelene ved at bruge MQTT i driftssikre IIOT-systemer.

---

# 🎉 Klar til næste øvelse!
Når denne øvelse er gennemført, fortsæt til Øvelse 2: Modbus TCP/IP kommunikation, hvor vi arbejder med direkte registerkommunikation mellem enheder.
