# 📝 Øvelse 1: Dataopsamling fra mindst 2 forskellige protokoller

## 🌟 Formål

Denne øvelse fokuserer på at etablere en stabil og fleksibel dataopsamlingsstruktur ved at integrere data fra mindst to forskellige IIOT-protokoller. Vi øger kompleksiteten og sikrer, at jeres systemer kan håndtere multikilde-data.

---

## 📖 Teori (læs først)

**Hvorfor opsamle data fra flere protokoller?**

- I virkelige IIOT-miljøer kommer data sjældent fra kun én kilde.
- Ved at integrere flere protokoller øges robustheden og anvendeligheden af systemet.
- Det giver mulighed for at sammenligne, validere og berige data på tværs af systemer.

**Eksempler på protokoller:**

- **MQTT:** Bruges til letvægts pub/sub kommunikation.
- **Modbus TCP/IP:** Bruges til dataudveksling med klassisk industriel hardware.
- **OPC UA:** Bruges til sikker og struktureret maskindataudveksling.
- **HTTP/REST API:** Bruges til at hente data fra eksterne webservices.
- **AMQP:** Bruges til pålidelig beskedudveksling via message brokers.

**Metadata er obligatorisk:** Alle datapakker skal indeholde:

- **Timestamp** (ISO 8601 format)
- **Enhed** (fx °C, %, bar)
- **Kilde** (hvilken sensor eller system)
- **Status** (OK, Warning, Error)

Dette sikrer, at data kan anvendes effektivt i efterfølgende øvelser til fejlhåndtering, logging og beslutningsstøtte.

---

# 🔄 Praktisk (udvidet step-by-step)

## 📖 Kontekst for datastrømmen

I denne øvelse opsamler vi **måledata fra to forskellige industrielle kilder**. Eksempler på datastrømme:
- **Sensorstrøm 1:** Temperaturmålinger fra en produktionslinje (MQTT eller HTTP API).
- **Sensorstrøm 2:** Trykmålinger fra en kompressor (Modbus TCP/IP eller OPC UA).

Formålet er at simulere en realistisk IIOT-situation, hvor flere forskellige typer sensorer rapporterer til et centralt system.

## 📖 Hvem er modtageren af datastrømmene?

- **Operatører:** Visualiserer live status via Node-RED dashboard.
- **Systemet:** Udfører sanity-checks, overvågning og beslutningsstøtte baseret på data.
- **Vedligeholdelsesteam:** Bruger logfiler og historik til fejlanalyse.

## 💪 Datastrømmenes rolle i det samlede system

- Alle indsamlede data skal beriges med metadata (unit, source, timestamp, status).
- Datastrømmene bruges senere til:
  - Driftsovervågning (sanity-checks og watchdogs)
  - Logging i CSV (for udfordring brug SQLite)
  - Visualisering og alarmering på dashboard
  - Automatisk beslutningsstøtte på baggrund af analyserede data

---

# 📕 Step-by-Step Guide

## 1. Start Node-RED
- Start Node-RED serveren lokalt eller i Docker.
- Åbn din browser og navigér til `http://localhost:1880`.
- Kontroller at Node-RED kører korrekt uden fejl.

## 2. Opret datastrøm 1
- Vælg en af følgende protokoller:
  - **MQTT, Modbus TCP/IP, OPC UA, HTTP/REST eller AMQP**.
- Træk relevant input-node ind (fx mqtt in, modbus-read, http request, amqp in).
- Parse payload, hvis nødvendigt:
  - Hvis data modtages som JSON string, brug en `json` node eller `function` node til parsing.

## 3. Opret datastrøm 2
- Vælg en anden protokol end datastrøm 1.
- Gentag opsætningen:
  - Input-node for den valgte protokol.
  - Parsing af payload hvis påkrævet.

## 4. Berig begge datastrømme med metadata
- Tilføj en `function` node lige efter hver parsing.
- Eksempel på metadata-berigelse:
    ```javascript
    msg.payload = {
      vaerdi: msg.payload,
      unit: "°C",          // Enhed for målingen
      source: "Sensor_1",   // Kildebeskrivelse
      status: "OK",         // Data status (OK/Warning/Error)
      timestamp: new Date().toISOString() // Tidsstempel
    };
    return msg;
    ```
- Tilpas `unit` og `source` for hver datastrøm.

## 5. Saml datastrømmene
- Hvis begge datastrømme skal behandles samlet:
  - Brug en `join` node:
    - Mode: Manual
    - Antal beskeder: 2 (en fra hver strøm)
- Hvis datastrømmene behandles separat:
  - Hold flows adskilte, men anvend samme metadata struktur.

## 6. Test
- Brug `debug` nodes efter hver `function` node.
- Kontroller i debug-vinduet:
  - At payloads er korrekt struktureret som objekter.
  - At alle metadatafelter er til stede.
  - At begge datastrømme leverer data uden fejl.

## 7. Gem arbejdet
- Gem flowet i Node-RED.
- Eksportér flows:
  - Åbn "hamburger-menuen" (øverst til højre) > Export > Clipboard.
  - Gem som `.json`-fil i din portfolio.

**Navngivning:**
- Brug en klar struktur fx: `workshop2_oevelse1_dataopsamling.json`

---

# 💡 Tips og ekstraudfordring
- Brug en "inject" node som midlertidig data-generator, hvis en datastrøm ikke virker.
- Simulér datapauser eller out-of-range værdier for at forberede sanity-checks.
- Forbered flows til integration med watchdogs, logging og alarmer i de kommende øvelser.

---

# 🎉 Klar til næste øvelse!
Når dataopsamlingen fungerer korrekt, går vi videre til at bygge sanity-checks og avancerede watchdog flows.

Efter denne øvelse er I klar til at implementere sanity-checks og watchdog flows på jeres datastrømme.

