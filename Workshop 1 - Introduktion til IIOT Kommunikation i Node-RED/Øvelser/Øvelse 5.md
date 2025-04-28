# 📝 Øvelse 5: OPC UA kommunikation i Node-RED

## 🌟 Formål

Formålet med denne øvelse er at introducere de studerende til OPC UA (Open Platform Communications Unified Architecture), som er en robust, sikker og platformsuafhængig kommunikationsstandard til industriel dataudveksling. Fokus er på at forbinde Node-RED som en OPC UA-klient til en server, læse data og integrere disse i et flow.

---

## 📖 Teori (læs først)

**Hvad er OPC UA?**
- OPC UA (Open Platform Communications Unified Architecture) er en standardiseret, platformsuafhængig kommunikationsprotokol designet til at muliggøre sikker og pålidelig dataudveksling i industrielle automationssystemer og IIOT.
- Protokollen blev udviklet for at forbedre og erstatte den oprindelige OPC Classic, som var afhængig af Microsoft Windows-teknologier som DCOM.
- OPC UA tilbyder en serviceorienteret arkitektur (SOA), der tillader systemer at udveksle komplekse datastrukturer på en standardiseret måde, samtidig med at der understøttes adgangskontrol, datakryptering og certificeringsmekanismer.

**Hvordan fungerer OPC UA i forhold til OSI-modellen?**
- **Applikationslaget (Layer 7):** OPC UA definerer en række tjenester (Services) som læsning, skrivning, browsing, historiske forespørgsler og abonnementer på dataændringer. Disse services gør det muligt for klienter at interagere med serveres informationsmodeller.
- **Præsentationslaget (Layer 6) og Session management:** OPC UA håndterer datapræsentation, kodning (binær og XML/JSON), komprimering og sessionhåndtering direkte. Det sikrer, at data formidles konsistent på tværs af platforme.
- **Transportlaget (Layer 4):** OPC UA anvender typisk TCP som transportprotokol. Det sikrer pålidelig overførsel af data mellem klient og server.
- **Netværkslaget (Layer 3):** IP-protokollen anvendes til routing af datagrammer mellem enheder.
- **Datalink- og fysisk lag (Layer 2 og 1):** Standard Ethernet anvendes ofte til fysisk forbindelse og overførsel.

**Kommunikationsstakke i OPC UA:**
- **UA TCP/Binary:** Hurtig og effektiv kommunikation. OPC UA anvender sin egen binære protokol ovenpå TCP for høj ydeevne.
- **SOAP/HTTP Web Services:** Understøtter interoperability med webbaserede applikationer. Data transporteres via HTTP med XML som kodningsformat.
- **MQTT (nyt i moderne OPC UA):** OPC UA kan også arbejde ovenpå MQTT for cloud-integration.

**Sikkerhed i OPC UA:**
- Indbygget brugergodkendelse (username/password, certifikater).
- Datakryptering og signering.
- Sessionstidsstyring og adgangskontrol til individuelle noder.

**Hvorfor bruge OPC UA i IIOT?**
- **Pålidelighed:** Konstant overvågning af forbindelser og automatisk genopretning ved fejl.
- **Sikkerhed:** Kryptering, autentificering og autorisering er en del af protokollen.
- **Interoperabilitet:** Muliggør kommunikation mellem enheder fra forskellige producenter uden tilpasninger.
- **Skalerbarhed:** Anvendes i små embedded enheder såvel som store enterprise-systemer.
- **Datamodellering:** OPC UA tillader at beskrive data og deres relationer på en struktureret måde.

**Metadata og databerigelse i OPC UA:**
- I OPC UA er det muligt ikke blot at sende rene måleværdier, men også at medsende **metadata** sammen med dataene.
- Hver node i OPC UA kan have attributter som navn, datatype, enhed (EngineeringUnit), minimums- og maksimumsværdier, adgangsrettigheder og beskrivelse.
- OPC UA Properties tillader knytning af ekstra oplysninger til en variabel, fx kalibreringsdato, produktionsbatchnummer eller sensor-ID.
- Alle data i OPC UA er typisk ledsaget af **timestamp** og **statuskode**, hvilket sikrer, at dataens kvalitet, aktualitet og gyldighed kan vurderes automatisk.
- Kompleks datamodellering muliggør overførsel af strukturerede objekter, hvor flere dataværdier og deres metadata sendes samlet, eksempelvis en sensorpakke der indeholder temperatur, tryk, enheds-id og kalibreringsstatus i ét datapunkt.
- Denne evne til at inkludere metadata er afgørende for driftssikkerhed, fejlsøgning, historisering og avanceret beslutningsstøtte i moderne IIOT-systemer.

**Eksempler på brug:**
- En OPC UA-server i en PLC udsender produktionsdata, som en cloud-løsning abonnerer på til analyse.
- SCADA-systemer bruger OPC UA til at forbinde til mange forskellige fabriksenheder for realtidskontrol.
- Smarte fabrikker integrerer sensorer, maskiner og ERP-systemer gennem en OPC UA-baseret datainfrastruktur.

---

## 🔧 Forudsætninger

Før du kan starte denne øvelse, skal du have:

- Node-RED installeret.
- Installeret `node-red-contrib-opcua` via "Manage Palette".
- En OPC UA-server tilgængelig:
  - Brug en simulator som "Prosys OPC UA Simulation Server" eller "FreeOpcUa Simple Server".
  - Kør lokalt på `opc.tcp://localhost:4840`.

---

# 🔄 Praktisk (step-by-step)

Denne udgave af Øvelse 5 fokuserer på at hente data fra en OPC UA-server, inkludere metadata direkte i datapakken og sikre overvågning gennem en watchdog/heartbeat-mekanisme.

---

## 1. Start OPC UA-serveren

- Start en OPC UA-simulationsserver lokalt.
- Find et node-id, fx "ns=2;s=Dynamic/RandomInt32".
- Kontrollér, at serveren tilbyder attributter som EngineeringUnit, Minimum/Maximum range osv.

## 2. Start Node-RED

- Åbn `http://localhost:1880` i din browser.

## 3. Opsæt OPC UA Client Read-flow

- Træk en `inject` node ind.

- Konfigurer:
  - Payload: **timestamp**
  - Repeat: Hvert 5. sekund.

- Træk en `opcua-client` node ind.

- Konfigurer:
  - Endpoint URL: `opc.tcp://localhost:4840`
  - Action: Read
  - NodeId: fx "ns=2;s=Dynamic/RandomInt32"

- Tilføj en `function` node:
  - Formatér payload og tilføj metadata:
    ```javascript
    msg.payload = {
      vaerdi: msg.payload.value.value,
      timestamp: msg.payload.serverTimestamp || new Date().toISOString(),
      status: msg.payload.statusCode.name,
      enhed: msg.payload.dataType, // Hvis tilgængeligt fra serveren
      nodeId: msg.addressSpace ? msg.addressSpace.browseName : "Ukendt"
    };
    return msg;
    ```

- Træk en `debug` node ind og forbind.
- Flow: `inject` -> `opcua-client` -> `function` -> `debug`

## 4. Deploy flowet

- Klik "Deploy" for at starte flowet.

## 5. Test kommunikationen

- Bekræft at data modtages korrekt i debug-panelet.
- Bekræft at værdi, timestamp, status og enhed/navn medsendes som en del af datapakken.

## 6. Fejlhåndtering

- Hvis ingen data modtages:
  - Kontrollér OPC UA-serverens status.
  - Kontrollér endpoint URL og NodeId.
  - Tjek eventuelle certifikatproblemer.

## 7. Gem arbejdet

- Eksporter flowet som `.json`-fil klar til aflevering.

---

## 💡 Bonus: Watchdog/Heartbeat

8. **Implementér Watchdog-mekanisme**

- Tilføj en `trigger` node efter `function` node:
  - Reset hver gang der modtages gyldig data.
  - Hvis ingen data modtages inden 15 sekunder, send en alarm: "ALARM: Mistet OPC UA forbindelse!"

9. **Alarm-output**

- Forbind triggerens alarmudgang til en `debug` node og eventuelt en visuel indikator på et dashboard.

# 💡 Noter

- Husk at dokumentere eventuelle fejl, problemer og hvordan de blev løst.
- Tidsstempling og metadata er afgørende for datavalidering, analyse og historik i industrielle systemer.
- Reflektér over hvordan metadata kan bruges til bedre beslutningsstøtte i IIOT-løsninger.
- Overvej OPC UA's styrker sammenlignet med tidligere protokoller, særligt inden for sikkerhed, datamodellering og interoperabilitet.

---


# 🎉 Klar til videre arbejde!

Efter denne øvelse er du klar til at arbejde med avanceret IIOT-datahåndtering.

