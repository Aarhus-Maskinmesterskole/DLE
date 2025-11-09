# README – Dag 2: IO-Link & MQTT

## 📌 Formål
På denne dag lærer du at arbejde med IO-Link enheder og MQTT-kommunikation i industrielle IoT-systemer. Du får praktisk erfaring med opsætning af IO-Link master, forbindelse til MQTT-broker, og sikkerhed med TLS-kryptering.

## 🎯 Læringsmål
Efter denne dag kan du:
- **Opsætte og konfigurere** IO-Link master med ifm moneo
- **Forbinde** IO-Link sensorer og læse live processdata
- **Arbejde med MQTT** i Node-RED (publish/subscribe)
- **Parse og visualisere** JSON-data fra IO-Link enheder
- **Bruge MQTT Explorer** til debugging og monitorering
- **Forstå MQTT over TLS** og hvorfor sikkerhed er vigtig

## 📂 Mappestruktur

```
dag02 - io-link og mqtt/
├── README.md (denne fil)
├── Quiz/
│   └── quiz-dag2.md
└── Øvelser/
    ├── 01-kom-igang-med-io-link.md
    ├── 02-mqtt-io-link.md
    ├── 03-mqtt-explorer.md
    └── 04-mqtt-tls.md
```

## 📚 Øvelser

### 1️⃣ Kom godt i gang med IO-Link (01-kom-igang-med-io-link.md)
**Indhold:**
- Installation af ifm moneo | configure
- Netværksopsætning (PC ↔ IO-Link master)
- Scan og konfiguration af IO-Link enheder
- Porte og status-identifikation
- Live processdata i moneo og web-interface
- MQTT Subscription setup

**Vigtige trin:**
- Trin 1-2: Download og installer moneo
- Trin 3-4: Netværk og start moneo
- Trin 5-7: Scan netværk og opret forbindelse
- Trin 8-10: Se livedata og verificér i web-interface
- Trin 11: Konfigurér MQTT broker og topic

**Forudsætninger:**
- Windows-PC med administratorrettigheder
- IO-Link master (fx ifm AL13xx/AL19xx)
- Mindst én IO-Link sensor
- 24V forsyning og netværkskabel

---

### 2️⃣ MQTT & IO-Link i Node-RED (02-mqtt-io-link.md)
**Indhold:**
- Forbindelse til MQTT-broker i Node-RED
- Subscribe og publish til MQTT topics
- Parse JSON-data fra IO-Link enheder
- Metadata-validering (timestamp, deviceId, status)
- Simulering af IO-Link data

**Opgaver:**
1. Opret MQTT forbindelse (test.mosquitto.org eller lokal broker)
2. Parse og vis IO-Link data i Dashboard
3. Valider metadata og statusinformation
4. Simuler IO-Link data med Inject-node

---

### 3️⃣ MQTT Explorer (03-mqtt-explorer.md)
**Indhold:**
- Installation af MQTT Explorer
- Forbindelse til MQTT-broker
- Monitorering af alle topics
- Publicering af testbeskeder
- Integration med Node-RED

**Trin:**
1. Download og installer MQTT Explorer
2. Forbind til `test.mosquitto.org:1883`
3. Publicér besked til `aams/test`
4. Verificér beskeder fra Node-RED

**Formål:**
- Debugging af MQTT-kommunikation
- Se alle beskeder i realtid (ingen kryptering synlig!)
- Teste topics og payloads

---

### 4️⃣ MQTT over TLS (04-mqtt-tls.md)
**Indhold:**
- Hvad er TLS (Transport Layer Security)?
- Hvorfor er sikkerhed vigtig i IoT?
- MITM-angreb (Man-in-the-Middle)
- Certifikater og kryptering

**Vigtige koncepter:**
- **Uden TLS:** Data sendes i klartekst (kan læses af alle)
- **Med TLS:** Data krypteres (kun afsender og modtager kan læse)
- **Certifikater:** CA-certifikat til autentificering
- **Port 1883:** Ukrypteret MQTT
- **Port 8883:** MQTT over TLS

**Sikkerhedsgevinster:**
- ✅ Kryptering af data
- ✅ Autentificering af broker og klient
- ✅ Beskyttelse mod MITM-angreb
- ✅ Dataintegritet (opdager manipulation)

---

## 🔧 Værktøjer og Software

| Værktøj | Formål | Download |
|---------|--------|----------|
| **ifm moneo** | IO-Link konfiguration | [moneo downloads](https://www.ifm.com/dk/da/shared/moneo-downloads) |
| **Node-RED** | MQTT flows og databehandling | Indbygget i installation |
| **MQTT Explorer** | MQTT debugging | [mqtt-explorer.com](https://mqtt-explorer.com/) |

---

## 💡 Tips og Tricks

### IO-Link Troubleshooting
- ✅ Tjek 24V forsyning til master
- ✅ Verificér PC og master er i samme subnet
- ✅ Brug netværksscan i moneo | configure
- ✅ Tjek firewall indstillinger
- ✅ Verificér port status (IO-Link aktiv)

### MQTT Troubleshooting
- ✅ Tjek broker IP og port (1883 ukrypteret, 8883 TLS)
- ✅ Verificér topic syntax (case-sensitive!)
- ✅ Brug MQTT Explorer til at se alle beskeder
- ✅ Tjek at Client ID er unik
- ✅ Verificér certifikater hvis TLS bruges

### Node-RED Best Practices
- 🟢 Brug Debug-noder flittigt
- 🟢 Navngiv noder beskrivende
- 🟢 Gruppér relaterede noder
- 🟢 Tilføj kommentarer til komplekse flows
- 🟢 Husk at deploye efter ændringer

---

## 📋 Tjekliste for Dag 2

### IO-Link Setup
- [ ] moneo | configure installeret
- [ ] Master og PC i samme subnet
- [ ] IO-Link sensor forbundet og konfigureret
- [ ] Live processdata synlig i moneo
- [ ] Web-interface viser samme data
- [ ] MQTT subscription konfigureret

### Node-RED MQTT
- [ ] MQTT-broker forbindelse oprettet
- [ ] Kan subscribe til topics
- [ ] Kan publicere beskeder
- [ ] JSON parsing fungerer
- [ ] Dashboard viser IO-Link data
- [ ] Metadata validering implementeret

### MQTT Explorer
- [ ] MQTT Explorer installeret
- [ ] Forbundet til broker
- [ ] Kan se beskeder fra Node-RED
- [ ] Kan publicere testbeskeder

### MQTT Sikkerhed
- [ ] Forstår forskellen mellem port 1883 og 8883
- [ ] Ved hvad TLS/SSL er
- [ ] Forstår MITM-angreb
- [ ] Kan forklare hvorfor TLS er vigtig

---

## 🎓 Quiz

Test din viden med quizzen i `Quiz/quiz-dag2.md`!

Quizzen dækker:
- IO-Link opsætning og konfiguration
- MQTT grundlæggende (topics, publish, subscribe)
- MQTT Explorer brug
- MQTT over TLS sikkerhed
- Praktiske scenarier fra øvelserne

---

## 🔗 Videre Læring

Efter denne dag kan du udforske:
- MQTT QoS (Quality of Service) niveauer
- Retained messages i MQTT
- MQTT Will/Testament beskeder
- Avancerede TLS setups med client certifikater
- MQTT broker opsætning (Mosquitto, HiveMQ)
- Integration med cloud IoT platforms

---

## ❓ Problemer?

Hvis du støder på problemer:
1. **Tjek tjeklisterne** ovenfor
2. **Brug MQTT Explorer** til debugging
3. **Se i Debug-vinduet** i Node-RED
4. **Verificér netværk** (ping, subnet)
5. **Spørg underviser** hvis stuck

---

**Held og lykke med dag 2! 🚀**
