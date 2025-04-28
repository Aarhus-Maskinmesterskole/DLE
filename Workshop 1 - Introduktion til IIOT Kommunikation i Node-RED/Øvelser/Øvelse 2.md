
# 📝 Øvelse 2: Modbus TCP/IP kommunikation i Node-RED

## 🌟 Formål
Formålet med denne øvelse er at give de studerende en grundlæggende forståelse af Modbus TCP/IP-protokollen, som stadig er en hjørnesten i mange industrielle anlæg. Fokus er på at opsætte en funktionel kommunikation mellem Node-RED og en Modbus TCP server, aflæse registre og håndtere data korrekt. Derudover introduceres metoder til fejlregistrering og driftssikring.

---
## 📖 Teori (læs først)

**Hvad er Modbus TCP/IP?**
- Modbus er en ældre kommunikationsprotokol, oprindeligt udviklet i 1979 af Modicon (nu Schneider Electric), specielt designet til industriel automatisering. Den blev hurtigt en industristandard pga. sin enkelhed og robusthed.
- Modbus TCP/IP er en moderne version, hvor de oprindelige Modbus-protokolbeskeder transporteres over et Ethernet-netværk ved brug af TCP/IP som transportlag.
- Dette muliggør kommunikation mellem industrielle enheder over standardnetværk uden behov for specialiseret hardware.

**Hvordan fungerer Modbus TCP/IP?**
- En Modbus TCP klient (også kaldet master) initierer alle kommunikationer ved at sende forespørgsler til en Modbus TCP server (også kaldet slave).
- Serveren besvarer hver forespørgsel med den efterspurgte data eller en fejlmeddelelse.
- Der anvendes en veldefineret PDU (Protocol Data Unit), som pakkes ind i en TCP-ramme.
- TCP sikrer, at data leveres korrekt og i den rigtige rækkefølge.

**Grundbegreber:**
- **Master (Client):** Den enhed, som aktivt sender forespørgsler. Eksempler: PLC, HMI, SCADA systemer.
- **Slave (Server):** Den enhed, der venter på forespørgsler og leverer svar. Eksempler: sensorer, aktuatorer.
- **Coils:** Binære (0/1) outputs, f.eks. tænd/sluk af en motor.
- **Discrete Inputs:** Binære (0/1) inputs, f.eks. aflæsning af en endestopkontakt.
- **Input Registers:** 16-bit read-only registre, typisk brugt til at aflæse målinger.
- **Holding Registers:** 16-bit læse-/skrive-registre, anvendt til at sætte værdier som f.eks. setpoints.

**Datatransport og adressering:**
- Modbus TCP anvender en adresseringsstruktur, hvor coils og registre identificeres med offset-adresser.
- Typiske adresser:
  - Coils: 00001-
  - Discrete Inputs: 10001-
  - Input Registers: 30001-
  - Holding Registers: 40001-
- Adresserne i beskeder er dog "0-based" i TCP (f.eks. 40001 i dokumentation svarer til adresse 0 i protokollen).

**Hvorfor bruge Modbus TCP/IP i IIOT?**
- **Enkel implementering:** Kræver minimale ressourcer at implementere i enheder.
- **Standardprotokol:** Støttes af stort set alle industrielle leverandører.
- **Netværksintegration:** Muliggør nem integration med eksisterende IT-infrastruktur.
- **Skalerbarhed:** Muliggør kommunikation mellem alt fra enkelte sensorer til komplekse SCADA-systemer.
- **Kosteffektivitet:** Udnytter eksisterende Ethernet-hardware og kabling.

**Begrænsninger ved Modbus TCP/IP:**
- Begrænset sårbarhed over usikre netværk (ingen indbygget kryptering).
- Simpel protokol uden avancerede funktioner som session management eller prioritering.
- Høj belastning ved mange samtidige forbindelser sammenlignet med moderne protokoller som OPC UA.

**Eksempler på brug:**
- Overvågning af temperatur- og tryksensorer i store procesanlæg, hvor mange dataindsamlingspunkter skal koordineres over et lokalt netværk.
- Fjernstyring af motorer, ventiler og andre aktuatorer i produktionsmiljøer via SCADA-systemer.
- Integration af ældre udstyr med moderne cloud-platforme gennem gateways, der oversætter Modbus TCP data til nyere IIOT-protokoller som MQTT.

---

## 🔧 Forudsætninger

For at kunne gennemføre denne øvelse, skal følgende være installeret og klar:

- Node-RED installeret lokalt eller i Docker.
- En Modbus TCP server installeret:
  - Brug en simulator som **ModbusPal** eller en Docker-baseret Modbus server.
  - IP-adresse typisk `127.0.0.1` og port `502` (standard).

- Node-RED Modbus noder installeret:
  - Gå til "Manage Palette" > "Install".
  - Installer `node-red-contrib-modbus`.

---

## 🔄 Praktisk (step-by-step)

### 1. Start Modbus TCP server
- Start serveren lokalt.
- Definer nogle åbne registre (f.eks. Holding Register 0).

### 2. Start Node-RED
- Start Node-RED og åbn det i din browser (`http://localhost:1880`).

### 3. Opsæt Read-flow
- Træk en `modbus-read` node ind på arbejdsfladen.
- Konfigurer serverindstillinger:
  - IP: `127.0.0.1`
  - Port: `502`
- Konfigurer `modbus-read` node:
  - Function Code: "Read Holding Registers"
  - Address: `0`
  - Quantity: `1`
  - Polling Interval: 5000 ms (5 sekunder).

- Tilføj en `function` node:
  - Navn: "Format data med timestamp"
  - Funktion:
    ```javascript
    msg.payload = {
      værdi: msg.payload.data[0],
      timestamp: new Date().toISOString()
    };
    return msg;
    ```

- Træk en `debug` node ind og forbind.
- Flow: `modbus-read` -> `function` -> `debug`.

### 4. Deploy flowet
- Klik "Deploy" for at gemme og starte dit flow.

### 5. Test kommunikationen
- Åbn debug-vinduet:
  - Kontroller at aflæste værdier samt tidsstempler modtages korrekt hvert 5. sekund.

### 6. Fejlhåndtering
- Hvis ingen data modtages:
  - Kontrollér IP-adresse og port.
  - Kontrollér at Modbus serveren er aktiv og korrekt konfigureret.
  - Brug "status" nodes for at overvåge forbindelser.

### 7. Gem arbejdet
- Eksporter flowet som en `.json`-fil via "Export" i Node-RED.

### 8. Bonus: Watchdog på Modbus Data (valgfri)
- Implementér en `trigger` node, som sender alarm, hvis ingen nye data modtages indenfor f.eks. 10 sekunder.
- Brug output til Dashboard eller Debug for at indikere tabt kommunikation.

---

# 💡 Noter
- Husk at alle data skal være **tidsstemplet** for senere analyse.
- Dokumentér eventuelle problemer og hvordan de blev løst.
- Overvej at sammenligne responstider mellem MQTT og Modbus TCP/IP.

---

# 🎉 Klar til næste øvelse!
Når denne øvelse er gennemført, fortsæt til Øvelse 3: HTTP/REST API kommunikation, hvor vi arbejder med integration mod webservices.

