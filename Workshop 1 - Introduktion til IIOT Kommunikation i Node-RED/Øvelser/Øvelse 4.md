# 📝 Øvelse 4: CoAP kommunikation i Node-RED

## 🌟 Formål
Formålet med denne øvelse er at introducere de studerende til brugen af CoAP-protokollen (Constrained Application Protocol) til kommunikation med ressourcebegrænsede enheder i IIOT-systemer. Fokus er på at opsætte en simpel CoAP-klient i Node-RED, sende forespørgsler og modtage svar.

---

## 📖 Teori (læs først)

**Hvad er CoAP?**
- CoAP (Constrained Application Protocol) er en specialiseret webprotokol designet til at give letvægtskommunikation for enheder med lav regnekraft og begrænset netværksbåndbredde.
- CoAP fungerer over **UDP** (User Datagram Protocol) i stedet for TCP, hvilket betyder, at forbindelsen er mere effektiv og hurtigere, men på bekostning af pålidelighed (ingen garanteret levering eller orden på beskeder).
- Protokollen er baseret på en RESTful model svarende til HTTP, hvilket betyder, at den anvender metoder som **GET**, **POST**, **PUT** og **DELETE** for at interagere med ressourcer.
- CoAP er optimeret til anvendelse i små enheder, der arbejder i netværk med lav energi og begrænset båndbredde, som det ofte ses i IIOT og smart home enheder.

**Hvordan fungerer CoAP i OSI-modellen?**
- **Applikationslaget (Layer 7):** CoAP fungerer som applikationsprotokollen. Det tillader enheder at forespørge, opdatere og slette ressourcer ved at bruge en RESTful interface.
- **Transportlaget (Layer 4):** CoAP anvender UDP som sin transportmekanisme, hvilket betyder at forbindelsen er "connectionless" og ikke garanterer pakkelevering. For at kompensere for dette har CoAP indbygget mekanismer til bekræftelse og retransmission.
- **Netværkslaget (Layer 3):** CoAP benytter IP (Internet Protocol) til at dirigere datapakker gennem netværket til målenheden.
- **Datalink- og fysiske lag (Layer 2 og 1):** Disse lag håndterer den egentlige transmission af pakker over fysiske medier som Ethernet, Wi-Fi, eller trådløse sensornetværk som 6LoWPAN.

**Grundbegreber:**
- **Client:** Enheden, der initierer en anmodning til en server om en bestemt ressource.
- **Server:** Enheden, der modtager anmodningen og sender et svar tilbage.
- **Resource:** Et stykke data eller en funktion, der tilgås via en specifik URI (Uniform Resource Identifier).

**Hvorfor bruge CoAP i IIOT?**
- **Lavt ressourceforbrug:** CoAP kræver minimale systemressourcer og er ideel til batteridrevne enheder.
- **Multicast-støtte:** En besked kan sendes til flere enheder samtidig, hvilket effektiviserer broadcast-kommunikation.
- **Effektivitet:** Mindre overhead sammenlignet med HTTP, hvilket reducerer netværkets belastning.
- **Pålidelighedsmekanismer:** Selvom CoAP anvender UDP, har det indbyggede bekræftelsesmekanismer (CON/NON beskeder) for at sikre, at vigtige beskeder bliver modtaget.

**Eksempler på brug:**
- Fjernovervågning og kontrol af trådløse sensornetværk i industri- eller landbrugsanvendelser.
- Smart home teknologier som intelligente lysstyringssystemer, termostater og sikkerhedsenheder.
- IoT-enheder i smarte byer (Smart Cities) hvor energieffektivitet og minimal datatrafik er vigtig.

---

## 🔧 Forudsætninger

For at kunne gennemføre denne øvelse, skal følgende være klar:

- Node-RED installeret lokalt eller via Docker.
- Installeret CoAP noder:
  - Gå til "Manage Palette" > "Install" og installer `node-red-contrib-coap`.
- En CoAP server tilgængelig:
  - Brug en offentlig CoAP server, f.eks. `coap://coap.me/test`
  - Alternativt brug en lokal CoAP server eller simulator.

---

# 🔄 Praktisk (udvidet step-by-step)

Denne udgave af Øvelse 4 fokuserer på at opsætte **både en CoAP-sender og en CoAP-modtager** i Node-RED. Enten i samme flow eller sammen med en sidemand.

---

## 🔄 Del 1: CoAP Server (Modtager)

1. **Start Node-RED**
- Åbn Node-RED på `http://localhost:1880`.

2. **Installer CoAP-server noder**
- Gå til "Manage Palette" > "Install" og installer `node-red-contrib-coap`.

3. **Opret en CoAP-server**
- Træk en `coap in` node ind.
- Konfigurer:
  - URL: `/sensor/temperature`
  - Method: POST (modtag beskeder)

4. **Behandl modtagne data**
- Tilføj en `function` node:
  - Parse payload:
    ```javascript
    msg.payload = {
      modtaget_data: msg.payload.toString(),
      timestamp: new Date().toISOString()
    };
    return msg;
    ```
- Forbind `coap in` node til `function` node.

5. **Vis data**
- Tilføj en `debug` node og forbind den til `function` node.

6. **Deploy flowet**
- Klik "Deploy".
- Serveren er nu klar til at modtage CoAP-beskeder.

---

## 🔄 Del 2: CoAP Client (Sender)

1. **Opret en CoAP-klient**
- Træk en `inject` node ind.
- Konfigurer:
  - Payload: fx `{"temperature": 22}` (JSON som tekst)
  - Sendes en gang eller gentages hvert 10. sekund.

2. **Tilføj en CoAP request**
- Træk en `coap request` node ind.
- Konfigurer:
  - URL: `coap://localhost/sensor/temperature`
  - Method: POST

- Forbind `inject` node til `coap request` node.

3. **Deploy flowet**
- Klik "Deploy".

4. **Test**
- Klik på inject-knappen.
- Se om CoAP serveren modtager beskeden i debug-vinduet.

---

## 🔄 Bonus: Watchdog/Heartbeat Overvågning

5. **Implementér en Watchdog-mekanisme**
- Tilføj en `trigger` node mellem `coap in` (servermodtagelse) og `debug` node.
- Konfigurer `trigger` node:
  - Modtag besked og nulstil timer.
  - Hvis ingen besked modtages inden 15 sekunder, send en alarm besked: "ALARM: Manglende heartbeat!"

6. **Vis Watchdog status**
- Forbind `trigger` output til en ekstra `debug` node.

---

# 💡 Noter
- Hvis du arbejder med en sidemand, kan én PC være server og den anden klient (husk korrekt IP i stedet for `localhost`).
- Hvis du kører på samme PC, kan du bruge `localhost`.
- Husk altid at **tidsstemple** de modtagne data for sporing.
- Dokumentér din opsætning med screenshots og noter om eventuelle fejl eller succeser.
- Overvej hvor vigtigt en heartbeat/overvågning er i kritiske IIOT-systemer.

---

# 🎉 Klar til næste trin!
Når denne udvidede opgave er afsluttet, fortsæt til Øvelse 5: OPC UA kommunikation.


---

# 💡 Noter
- Husk at data stadig skal **tidsstemples**, hvis du bearbejder svaret.
- CoAP fungerer bedst i kontrollerede miljøer på grund af UDP's upålidelige natur.
- Dokumentér eventuelle fejl og hvordan du forsøgte at løse dem.
- Overvej anvendelsesmuligheder for CoAP i batteridrevne IIOT-enheder.

---

# 🎉 Klar til næste øvelse!
Efter denne øvelse fortsætter vi til Øvelse 5: OPC UA kommunikation, hvor vi arbejder med sikre og pålidelige industrielle standarder til maskindataudveksling.
