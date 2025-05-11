# 📝 Øvelse 6: AMQP kommunikation i Node-RED

## 🌟 Formål
Formålet med denne øvelse er at introducere de studerende til anvendelsen af AMQP (Advanced Message Queuing Protocol) til pålidelig messaging i IIOT-systemer. Fokus er på at opsætte en RabbitMQ-server, sende og modtage beskeder via AMQP i Node-RED, samt implementere en watchdog-mekanisme for overvågning af beskedflowet.

---

## 📖 Teori (læs først)

**Hvad er AMQP?**
- AMQP (Advanced Message Queuing Protocol) er en internationalt anerkendt, åben standardprotokol designet til at muliggøre message-oriented middleware-kommunikation mellem distribuerede applikationer.
- Den tilbyder en pålidelig og sikret metode til at sende beskeder mellem systemer, uanset netværksforhold, servercrash eller midlertidige forbindelsesproblemer.
- AMQP fungerer ved at decouplere producent (sender) og forbruger (modtager) af beskeder via en mellemliggende "broker", hvilket muliggør asynkron kommunikation.
- Protokollen specificerer både netværksinteraktionen (wire format) og brokerens opførsel, hvilket sikrer fuld kompatibilitet på tværs af implementeringer.

**Typiske komponenter i AMQP-systemer:**
- **Producer:** Applikation eller enhed, der sender beskeder til en broker.
- **Broker (f.eks. RabbitMQ):** Server der modtager beskeder fra producenter, gemmer dem sikkert og videresender dem til de rette forbrugere via køer og exchanges.
- **Queue:** Midlertidig lagerplads i broker, hvor beskeder venter på at blive behandlet.
- **Exchange:** Router beskeder til de korrekte køer baseret på routing-nøgler og bindings.
- **Consumer:** Applikation eller enhed, der modtager beskeder fra en queue.

**Hvordan fungerer AMQP i forhold til OSI-modellen?**
- **Applikationslaget (Layer 7):** AMQP-definerede beskeder (med payloads og headers) sendes mellem applikationer.
- **Session og transportlag (Layer 5 og 4):** AMQP benytter TCP til transport og etablerer en stabil session mellem client og broker.
- **Netværkslaget (Layer 3):** IP anvendes til at dirigere datatrafikken.

**Sikkerhedsaspekter:**
- AMQP kan køre over TLS for at sikre kryptering af data under transport.
- Authentificering (typisk via brugernavn og adgangskode) anvendes for at beskytte adgang til broker og køer.

**Hvorfor bruge AMQP i IIOT?**
- **Pålidelig levering:** Beskeder kan persisteres på disk, hvilket betyder, at de ikke mistes selvom serveren crasher.
- **Transaktioner:** Mulighed for at gruppere flere beskeder i en transaktion, som enten accepteres samlet eller afvises samlet.
- **Kvitteringer:** Producenter kan modtage bekræftelse på, at en besked er leveret til en queue.
- **Routing-fleksibilitet:** Brug af exchanges og routing keys gør det muligt at distribuere beskeder intelligent baseret på regler.
- **Skalerbarhed:** Velegnet til storskalasystemer hvor tusindvis af enheder skal kommunikere samtidigt.
- **Robusthed mod netværksproblemer:** Da beskeder gemmes i brokeren, kan modtagere være offline midlertidigt uden at beskeder mistes.

**Eksempler på anvendelse i IIOT:**
- Produktionsudstyr der sender status- og alarmbeskeder til en central server.
- Sensorer der rapporterer data til cloud-tjenester gennem en AMQP-broker.
- Automatiske vedligeholdelsesanmodninger baseret på maskinstatus sendt via AMQP-netværk.

---

## 🔧 Forudsætninger

For at kunne gennemføre denne øvelse, skal du have følgende klar:

- **Node-RED installeret**
  - Enten lokalt på din maskine eller i en Docker-container.

- **RabbitMQ server installeret**
  - Du kan installere RabbitMQ på flere måder:

    **Installation via Docker (anbefalet):**
    - Åbn en terminal eller kommandoprompt.
    - Kør følgende kommando for at hente og starte RabbitMQ med management interface:
      ```bash
      docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:management
      ```
    - Port 5672 bruges til AMQP kommunikation.
    - Port 15672 bruges til web-baseret management interface (RabbitMQ Management UI).

    **Installation på Windows/Linux/macOS:**
    - Download installer fra RabbitMQs officielle hjemmeside: [https://www.rabbitmq.com/download.html](https://www.rabbitmq.com/download.html)
    - Følg installationsvejledningen for dit operativsystem.

    **Kontrol:**
    - Efter start kan du tilgå RabbitMQ Management UI på `http://localhost:15672`.
    - Standard login:
      - Brugernavn: `guest`
      - Adgangskode: `guest`

- **Installeret Node-RED AMQP noder**
  - Gå til Node-RED menuen „Manage Palette“.
  - Klik på "Install" fanen.
  - Søg efter og installer pakken `node-red-contrib-amqp`.

- **Bemærk:**
  - Din RabbitMQ-server skal være startet og tilgængelig, før du kan sende eller modtage beskeder via Node-RED.
  - Det anbefales at køre Node-RED og RabbitMQ på samme netværk eller localhost for øvelsens skyld.

---

## 🔄 Praktisk (step-by-step)

For inspiration se [AMQP](https://www.youtube.com/watch?v=lru_T4uLo98&t=92s)

### 1. Start RabbitMQ Server
- Start RabbitMQ-serveren lokalt eller i Docker.
- Åbn Management UI på `http://localhost:15672` (login: guest/guest).

### 2. Start Node-RED
- Åbn `http://localhost:1880` i browseren.

### 3. Opsæt AMQP Sender (Producer)
- Træk en `inject` node ind.
- Konfigurer:
  - Payload: fx `{"temperature": 24, "timestamp": ""}`
  - Repeat: Hvert 10. sekund.
- Tilføj en `function` node:
  - Udfyld timestamp:
    ```javascript
    let data = JSON.parse(msg.payload);
    data.timestamp = new Date().toISOString();
    msg.payload = JSON.stringify(data);
    return msg;
    ```
- Træk en `amqp out` node ind.
- Konfigurer:
  - URL: `amqp://guest:guest@localhost`
  - Queue: `sensor.data`

- Flow: `inject` -> `function` -> `amqp out`

### 4. Opsæt AMQP Modtager (Consumer)
- Træk en `amqp in` node ind.
- Konfigurer:
  - URL: `amqp://guest:guest@localhost`
  - Queue: `sensor.data`

- Tilføj en `debug` node for at vise modtagne beskeder.

- Flow: `amqp in` -> `debug`

### 5. Deploy flowet
- Klik "Deploy" for at starte flows.

### 6. Test kommunikationen
- Bekræft at beskeder sendes og modtages med korrekt temperatur og timestamp.

### 7. Fejlhåndtering
- Hvis ingen beskeder modtages:
  - Kontrollér RabbitMQ-serverens status.
  - Kontrollér queue-navne og URL.
  - Se log i RabbitMQ Management UI.

### 8. Gem arbejdet
- Eksporter flows som `.json`-filer klar til aflevering.

---

## 💡 Bonus: Watchdog/Heartbeat

9. **Implementér Watchdog-mekanisme**
- Brug en `trigger` node efter `amqp in`:
  - Reset på hver modtaget besked.
  - Hvis ingen besked modtages inden 20 sekunder, send alarm: "ALARM: Mistet AMQP forbindelse!"

10. **Vis alarmstatus**
- Tilføj en `debug` node og eventuelt visning på et Dashboard.

---

# 💡 Noter
- Husk at dokumentere eventuelle problemer og hvordan de blev løst.
- Tidsstempling er essentielt for korrekt analyse af data.
- Reflektér over fordelene ved AMQP i forhold til andre protokoller i forhold til pålidelighed og datasikring.
