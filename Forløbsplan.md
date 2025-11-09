# Forløbsplan for IIoT baseret Dataopsamling

## 📅 Oversigt

| Dag | Dato | Formiddag | Eftermiddag |
|-----|------|-----------|-------------|
| **Dag 1** | 10. nov | Node-RED intro | Node-RED intro |
| **Dag 2** | 11. nov | MQTT intro | MQTT intro |
| **Dag 3** | 12. nov | Tjørring Case | Tjørring Case |
| **Dag 4** | 13. nov | Tjørring Case | Tjørring Case |
| **Dag 5** | 14. nov | Tjørring Case | Tjørring Case |
| **Dag 6** | 24. nov | Sanity checks | Sanity checks |
| **Dag 7** | 25. nov | Sanity checks (tidlig) + Intro til Digital Twins (sen) | Tjørring Case |
| **Dag 8** | 26. nov | Sanity checks + Digital Twin | Præsentation: Prissætte løsning til Tjørring Case |
| **Dag 9** | 27. nov | Ekstern indlæg | Ekstern indlæg |
| **Dag 10** | 01. dec | Lagring og trafik | Pris, hvad skal lagres, historik, hvordan skal det gøres |
| **Dag 11** | 02. dec | Ny præsentation: Tjørring Case løsning | Cloud og services integration |
| **Dag 12** | 03. dec | Digital Twin | Digital Twin |
| **Dag 13** | 04. dec | Digital Twin | Digital Twin |
| **Dag 14** | 05. dec | Evaluering | Evaluering |

---

## 📚 Uge 1: Byg en dataservice (10-14 november 2025)

### Dag 1: Mandag 10. november - Node-RED intro
- **Formiddag:** Node-RED introduktion
  - Installation og opsætning
  - Basale noder (Inject, Debug, Function, Change, Switch)
  - Flow-struktur og deployment
  - Dashboard introduktion
- **Eftermiddag:** Node-RED intro (fortsat)
  - Avancerede noder (CSV, JSON, Split, Join)
  - File håndtering (Read/Write)
  - Praktiske øvelser
  - Quiz

### Dag 2: Tirsdag 11. november - MQTT intro
- **Formiddag:** MQTT introduktion
  - Hvad er MQTT? (Pub/Sub protokol)
  - MQTT-broker forbindelse
  - Topics og payload
  - MQTT-in og MQTT-out noder
- **Eftermiddag:** MQTT intro (fortsat)
  - IO-Link og MQTT integration
  - MQTT Explorer installation og brug
  - MQTT over TLS (sikkerhed)
  - MITM-angreb forståelse
  - Praktiske øvelser
  - Quiz

### Dag 3-5: Onsdag 12. - Fredag 14. november - Tjørring Case
- **Formiddag:** Tjørring Case arbejde
  - Analyse af ABR case
  - Systemdesign og arkitektur
  - Implementering af dataflow
  - Node-RED flows til case
- **Eftermiddag:** Tjørring Case arbejde (fortsat)
  - Datahåndtering
  - Visualisering i Dashboard
  - Test og validering
  - Dokumentation

---

## 🔍 Uge 2: Overvåg drift og vedligehold (24-27 november 2025)

### Dag 6: Mandag 24. november - Sanity checks
- **Formiddag:** Sanity checks introduktion
  - Hvad er sanity checks?
  - Range checks (min/max værdier)
  - Plausibility checks (logisk kontrol)
  - Validering af sensordata
  - Fejldetektion
- **Eftermiddag:** Sanity checks (fortsat)
  - Implementering i Node-RED
  - Watchdog/heartbeat mekanismer
  - Alarm og notifikationer
  - Praktiske øvelser

### Dag 7: Tirsdag 25. november - Sanity checks + Digital Twins intro + Tjørring Case
- **Tidlig formiddag:** Sanity checks afslutning
  - Komplekse valideringer
  - Error handling
  - Logging af fejl
- **Sen formiddag:** Introduktion til Digital Twins
  - Hvad er en digital tvilling?
  - Anvendelse i IIoT
  - Realtid vs. historisk data
  - Simulering og prediktion
- **Eftermiddag:** Tjørring Case arbejde
  - Integration af sanity checks
  - Implementering af validering
  - Forbedring af løsning

### Dag 8: Onsdag 26. november - Sanity checks + Digital Twin + Præsentation
- **Formiddag:** Videre arbejde med Sanity checks og Digital Twin
  - Sanity checks i praksis
  - Digital Twin model design
  - Datasynkronisering
  - Real-time opdatering
- **Eftermiddag:** Præsentation - Prissætte løsning til Tjørring Case
  - Hardwareomkostninger (sensorer, IO-Link master, etc.)
  - Softwareomkostninger (licenser, cloud services)
  - Implementeringsomkostninger (arbejdstimer, installation)
  - Driftsomkostninger (vedligehold, support, hosting)
  - ROI-beregning (Return on Investment)
  - Værdiproposition for kunden

### Dag 9: Torsdag 27. november - Ekstern indlæg
- **Formiddag:** Ekstern indlæg
  - Ondsindet ekstern online indtrængen
  - Cybersecurity i IIoT
  - Trusler og sårbarheder
  - Sikkerhedsmekanismer
- **Eftermiddag:** Ekstern indlæg (fortsat)
  - Best practices
  - Firewall og netværkssikkerhed
  - TLS/SSL certifikater
  - Autentificering og autorisering

---

## 💾 Uge 3: Lagring, cloud og digital twins (01-05 december 2025)

### Dag 10: Mandag 1. december - Lagring og trafik
- **Formiddag:** Lagring og trafik
  - Databaser (SQL vs. NoSQL)
  - Time-series databaser (InfluxDB, TimescaleDB)
  - Cloud storage løsninger
  - On-premise vs. Cloud
- **Eftermiddag:** Strategiske overvejelser
  - **Pris:** Lagringskostomkostninger, båndbredde
  - **Hvad skal lagres:** Rå data vs. aggregeret data, metadata
  - **Historik:** Hvor længe skal data gemmes? Arkivering
  - **Hvordan skal det gøres:** Backup, redundans, skalering

### Dag 11: Tirsdag 2. december - Ny præsentation på Tjørring Case løsning
- **Formiddag:** Ny præsentation - Tjørring Case løsning
  - Revision af tidligere løsning
  - Integration af cloud services
  - Skalering og fleksibilitet
  - Omkostningsoptimering
- **Eftermiddag:** Cloud og services integration
  - Azure/AWS IoT services
  - MQTT cloud brokers
  - Data processing i cloud
  - Visualization services (Grafana, Power BI)
  - Edge computing vs. Cloud computing
  - Hybrid løsninger

### Dag 12-13: Onsdag 3. - Torsdag 4. december - Digital Twin
- **Formiddag:** Digital Twin udvikling
  - Design af digital tvilling for Tjørring Case
  - Data mapping (sensor → digital model)
  - Simulering og scenarie-test
  - Predictive maintenance
- **Eftermiddag:** Digital Twin (fortsat)
  - Machine Learning integration
  - Anomaly detection
  - Performance optimization
  - Visualisering af digital tvilling
  - Real-time synchronization
  - Testing og validering

---

## 🎯 Dag 14: Fredag 5. december - Evaluering

### Evaluering
- **Formiddag:** Evaluering
  - Portfolio gennemgang
  - Refleksion over forløbet
  - Peer review
  - Feedback session
- **Eftermiddag:** Evaluering (fortsat)
  - Afsluttende quiz
  - Certificering
  - Opsamling og næste skridt
  - Aflevering af portfolio

---

## 🎓 Læringsmål

Efter forløbet kan den studerende:

### Tekniske kompetencer
- **Designe og implementere** IIoT dataservices med Node-RED
- **Anvende** MQTT til sikker kommunikation med TLS
- **Implementere** sanity checks og data validering
- **Udvikle** digital twins til overvågning og prediktion
- **Integrere** cloud services i IIoT løsninger
- **Vurdere** lagringsstrategi og omkostninger

### Sikkerhed
- **Forstå** cybersecurity trusler i IIoT
- **Implementere** TLS kryptering og firewall
- **Håndtere** ondsindet online indtrængen
- **Anvende** best practices for sikkerhed

### Økonomi og forretning
- **Prissætte** IIoT løsninger (hardware, software, drift)
- **Beregne** ROI for industrielle investeringer
- **Vurdere** cloud vs. on-premise omkostninger
- **Præsentere** tekniske løsninger for stakeholders

### Digital Twin
- **Designe** digital tvilling modeller
- **Anvende** Machine Learning til anomaly detection
- **Implementere** predictive maintenance
- **Synkronisere** real-time data med digital model

---

## 📦 Portfolio krav

**Portfolio** skal indeholde:

### 1. Node-RED & MQTT
- Dokumentation af flows
- MQTT opsætning med TLS
- Screenshots og forklaringer

### 2. Tjørring Case
- Systemarkitektur diagram
- Implementering beskrivelse
- Sanity checks dokumentation
- Test resultater

### 3. Økonomisk analyse
- Prissætning af løsning (hardware, software, drift)
- ROI-beregning
- Cloud vs. on-premise sammenligning
- Værdiproposition

### 4. Digital Twin
- Design og koncept
- Implementering
- ML integration (hvis relevant)
- Test og validering

### 5. Sikkerhed
- Trusselanalyse
- Implementerede sikkerhedsforanstaltninger
- TLS/firewall dokumentation
- Refleksion over ekstern indlæg

### 6. Lagring & Cloud
- Lagringsstrategi
- Cloud service integration
- Omkostningsanalyse
- Skaleringsplan

### 7. Refleksion
- Hvad har du lært?
- Udfordringer og løsninger
- Næste skridt i læring

**Deadline:** Dag 14 (5. december 2025) kl. 15:00

---

## 📋 Tjekliste

### Uge 1
- [ ] Node-RED installeret og konfigureret
- [ ] Alle basale og avancerede noder afprøvet
- [ ] MQTT broker forbindelse etableret
- [ ] MQTT Explorer installeret
- [ ] TLS/SSL forstået
- [ ] Tjørring Case analyse påbegyndt
- [ ] Quiz dag 1 og 2 gennemført

### Uge 2
- [ ] Sanity checks implementeret
- [ ] Watchdog/heartbeat mekanisme
- [ ] Digital Twin koncept forstået
- [ ] Præsentation 1: Prissætning udarbejdet
- [ ] Ekstern indlæg gennemført
- [ ] Sikkerhedsforståelse opdateret

### Uge 3
- [ ] Lagringsstrategi defineret
- [ ] Cloud services udforsket
- [ ] Præsentation 2: Cloud integration udarbejdet
- [ ] Digital Twin implementeret
- [ ] ML integration (hvis relevant)
- [ ] Portfolio næsten færdig

### Dag 14
- [ ] Portfolio komplet
- [ ] Alle quiz gennemført
- [ ] Peer review udført
- [ ] Aflevering klar

---

**Bemærk:** Denne forløbsplan er den endelige version baseret på undervisers specifikationer. Husk at holde dig opdateret via løbende kommunikation!
