
# 📝 Øvelse 1: MQTT kommunikation i Node-RED

## 🌟 Formål
Lære at etablere letvægts, pub/sub-baseret kommunikation mellem enheder via MQTT-protokollen. Fokus er på opsætning af en simpel datastrøm med korrekt tidsstempling og grundlæggende fejlhåndtering.

---

## 📖 Teori (læs først)

**Hvad er MQTT?**
- MQTT (Message Queuing Telemetry Transport) er en letvægtsprotokol designet til effektiv beskedudveksling over netværk med lav båndbredde.
- MQTT bruger et **publish/subscribe**-mønster:
  - En **publisher** sender beskeder til et bestemt **topic**.
  - En **subscriber** lytter til et topic og modtager beskeder.

**Grundbegreber:**
- **Broker:** En server, som håndterer modtagelse og videresendelse af beskeder.
- **Client:** En enhed, som enten publicerer eller subscriber til data.

**Hvorfor bruge MQTT i IIOT?**
- Lavt dataforbrug
- Hurtig kommunikation
- Robust mod netværksforstyrrelser
- Understøtter mange samtidige forbindelser

**Eksempler på brug:**
- Sensorer der sender temperaturdata til overvågningssystemer.
- Maskiner der rapporterer driftstilstand til en cloud-platform.

---

## 🔧 Forudsætninger

Før du kan gennemføre denne øvelse, skal følgende være installeret og klar:

- Node-RED installeret og kørende lokalt.
- En MQTT broker installeret:
  - Installér **Mosquitto** lokalt (anbefalet)
    - Linux: `sudo apt install mosquitto mosquitto-clients`
    - Windows: Installer via Mosquitto installer fra Eclipse hjemmeside.
    - Docker: `docker run -it -p 1883:1883 eclipse-mosquitto`
  - Alternativt brug en public MQTT broker (f.eks. test.mosquitto.org).

---

## 🔄 Praktisk (step-by-step)

### 1. Start Node-RED
- Start Node-RED og åbn det i din browser (`http://localhost:1880`).

### 2. Opsæt Publish-flow
- Træk en `inject` node ind på arbejdsfladen.
- Konfigurer `inject` node:
  - Payload type: **string**
  - Værdi: eksempelvis `25`
  - Repeat: Send hvert 5. sekund.

- Tilføj en `function` node:
  - Navn: "Tilføj timestamp"
  - Indhold:
    ```javascript
    msg.payload = {
      temperatur: msg.payload,
      timestamp: new Date().toISOString()
    };
    return msg;
    ```

- Træk en `mqtt out` node ind:
  - Forbind den til din MQTT broker.
  - Topic: fx `sensor/temperatur`.

- Forbind `inject` node til `function` node og videre til `mqtt out` node.

### 3. Opsæt Subscribe-flow
- Træk en `mqtt in` node ind.
- Konfigurer den:
  - Forbind til samme broker.
  - Topic: `sensor/temperatur`.

- Træk en `debug` node ind.
- Forbind `mqtt in` node til `debug` node.

### 4. Deploy flowet
- Klik på "Deploy" for at gemme og starte flowet.

### 5. Test kommunikationen
- Hold øje med debug-vinduet:
  - Du skal se beskeder med temperatur og timestamp komme hvert 5. sekund.

### 6. Fejlhåndtering
- Hvis ingen beskeder modtages:
  - Kontrollér broker-adresse og port.
  - Kontrollér topic-navne (de er case-sensitive).
  - Brug "status" nodes for at se forbindelsesstatus.

### 7. Gem arbejdet
- Eksporter flowet som en `.json`-fil, klar til aflevering.

---

# 💡 Noter
- Alle data skal være korrekt **tidsstemplet**.
- Fejlhåndtering er obligatorisk: sikre reaktion på manglende forbindelse.
- Dokumentér i din opsummering hvordan flowet blev testet og eventuelle problemer du stødte på.

---

# 🎉 Klar til næste øvelse!
Når denne øvelse er gennemført, fortsæt til Øvelse 2: Modbus TCP/IP kommunikation.

