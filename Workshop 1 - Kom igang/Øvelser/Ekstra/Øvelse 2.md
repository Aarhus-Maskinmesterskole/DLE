
# 📝 Øvelse 2: Modbus TCP/IP kommunikation i Node-RED

## 🌟 Formål
Formålet med denne øvelse er at give de studerende en grundlæggende forståelse af Modbus TCP/IP-protokollen, som stadig er en hjørnesten i mange industrielle anlæg. Fokus er på at opsætte en funktionel kommunikation mellem Node-RED og en Modbus TCP server, aflæse registre og håndtere data korrekt. Derudover introduceres metoder til fejlregistrering og driftssikring.

---
## 📖 Modbus TCP/IP – Teori og Function Codes

### Hvad er Modbus TCP/IP?

Modbus er en af de ældste og mest udbredte protokoller i industriel automatisering (oprindeligt fra 1979, Modicon/Schneider Electric). **Modbus TCP/IP** er den moderne variant, hvor Modbus‑rammen pakkes i TCP/IP og transporteres over Ethernet, så man kan bruge standard‑netværksudstyr i stedet for specialiseret seriel hardware.

**Grundprincip**
En **Modbus TCP‑klient** (master) initierer alle forespørgsler; en **Modbus TCP‑server** (slave) svarer. Hver udveksling består af en request/response‐PDU, som TCP sørger for leveres fejlfrit og i korrekt rækkefølge.

| Begreb                | Forklaring                                       |
| --------------------- | ------------------------------------------------ |
| **Client/Master**     | Enhed der sender forespørgsler (PLC, HMI, SCADA) |
| **Server/Slave**      | Enhed der svarer (sensor, aktuator, gateway)     |
| **Coils**             | Binære outputs  (00001‑)                         |
| **Discrete Inputs**   | Binære inputs   (10001‑)                         |
| **Input Registers**   | 16‑bit read‑only registre (30001‑)               |
| **Holding Registers** | 16‑bit read/write registre (40001‑)              |

> **Adresse‑note:** I dokumentation er adresser ofte 1‑baserede (40001), mens protokollen bruger 0‑baseret offset (så 40001 ⇒ 0 i PDU).

### Hvorfor bruge Modbus TCP/IP i IIoT?

* **Enkel implementering** og lav overhead
* **Bred leverandør‑understøttelse** (de‑facto standard)
* **Netværksintegration** med eksisterende IT‑infrastruktur
* **Skalerbarhed** fra få sensorer til komplette SCADA‑systemer
* **Kosteffektivitet** via standard Ethernet‑hardware

**Begrænsninger**

* Ingen indbygget kryptering / authentication
* Ingen QoS eller prioritering
* Kan belaste CPU/net ved mange samtidige forbindelser sammenlignet med nyere protokoller (OPC UA, MQTT)

### Typiske anvendelser

* Overvågning af temperatur‑ og tryksensorer i procesanlæg
* Fjernstyring af motorer, ventiler og aktuatorer via SCADA
* Gateway‑oversættelse til cloud (Modbus TCP → MQTT / OPC UA)

---

### 🛠️ Function Codes (FC) – Hurtigt overblik

| FC (hex) | Navn                          | Beskrivelse kort                       | Adgang | Datatype        |
| -------- | ----------------------------- | -------------------------------------- | ------ | --------------- |
| **01**   | Read Coils                    | Læs status af multiple coils           | R      | Coils           |
| **02**   | Read Discrete Inputs          | Læs status af multiple digitale inputs | R      | Discrete Inputs |
| **03**   | Read Holding Registers        | Læs én eller flere holding‑registre    | R      | Holding Reg.    |
| **04**   | Read Input Registers          | Læs én eller flere input‑registre      | R      | Input Reg.      |
| **05**   | Write Single Coil             | Sæt/tøm én coil                        | W      | Coils           |
| **06**   | Write Single Register         | Skriv én holding‑register (16‑bit)     | W      | Holding Reg.    |
| **0F**   | Write Multiple Coils          | Skriv flere coils i én pakke           | W      | Coils           |
| **10**   | Write Multiple Registers      | Skriv flere holding‑registre           | W      | Holding Reg.    |
| **17**   | Read/Write Multiple Registers | Kombineret læs+skriv i samme telegram  | R/W    | Holding Reg.    |

> **Tip:**
> ‑ FC 0x2B/0x0E kan bruges til **diagnostic og identification** (Read Device Identification).
> ‑ FC 0x08 tillader **diagnostic kommandoer**, f.eks. loopback‑test.

### 📌 Hurtige tommelfingerregler

* Brug **FC 03/06/10** ved styring af setpoints og konfigurationer (Holding Registers).
* Brug **FC 01/02/05/0F** til binær on/off‑kontrol.
* Sørg for korrekt byte‑order (Big‑Endian) og énhedskonvertering, især ved floating‑point data (ofte 32‑bit, kræver 2 registre).
* Husk TCP‑timeout/retry‑strategi – Modbus har ingen indbygget keep‑alive.

---

## 🔧 Forudsætninger

For at kunne gennemføre denne øvelse, skal følgende være installeret og klar:

- Node-RED installeret lokalt eller i Docker.
- Installer paletten `node-red-contrib-modbus`
- Læs omkring opsætning af Modbus TCP server
  - IP-adresse typisk `localhost` og port `502` (standard).

Modbus TCP Serveren skal konfigureres for at det er muligt at hente data og sende data fra client.   
Bemærkning: Det er muligt at modtage live data fra IP: `172.24.0.5`, PORT: `4999`. OBS! normalt er default PORT `502` men fordi i DLE anvendes docker så har hver maskine interne docker IP og PORT.

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

