# README: Node-RED Protokol Eksempler (MQTT, AMQP, CoAP, Modbus, WebSocket) 📄

## Introduktion 👋

Dette dokument beskriver en samling af Node-RED flows, der demonstrerer brugen af forskellige kommunikationsprotokoller og teknologier, som er essentielle inden for automation, IIoT (Industrial Internet of Things) 🏭 og moderne webudvikling 🌐. Flowene er designet som simple eksempler, der kan importeres og tilpasses til egne projekter.

De dækkede protokoller/teknologier er:

1.  **MQTT** 📡: Letvægts publish/subscribe protokol, ideel til IoT-enheder og sensornetværk.
2.  **AMQP** 📦: Robust message queuing protokol, velegnet til pålidelig kommunikation mellem systemer (bruger RabbitMQ).
3.  **CoAP** 💡: Letvægts request/response protokol designet til ressourcebegrænsede IoT-enheder.
4.  **Modbus TCP** 🔌: Udbredt protokol til industriel automation og kommunikation med PLC'er og andre enheder.
5.  **WebSocket** ↔️: Protokol til fuld duplex realtidskommunikation, ofte brugt mellem webservere og browsere.

## Forudsætninger ✅

* **Node-RED:** En kørende instans af Node-RED.
* **Nødvendige Nodes:** Sørg for at have de relevante Node-RED nodes installeret via "Manage Palette" 🎨:
    * `node-red-contrib-amqp` (for AMQP)
    * `node-red-contrib-coap` (for CoAP)
    * `node-red-contrib-modbus` (for Modbus)
    * MQTT og WebSocket nodes er typisk indbyggede i standard Node-RED installationer.
* **Eksterne Services (afhængigt af flow):**
    * En MQTT Broker (f.eks. Mosquitto, HiveMQ, eller en cloud service). Eksemplet bruger `test.mosquitto.org`.
    * En AMQP Broker (f.eks. RabbitMQ). Eksemplet forventer en kørende RabbitMQ-instans på hostnavnet `rabbitmq`.
    * En CoAP-kompatibel enhed/server (hvis du tester CoAP request). Eksemplet sender til `aams_test`.
    * En Modbus TCP Slave/Server enhed eller simulator. Eksemplet forbinder til `172.24.0.5` på port `4999`.

## Implementering af Flows ⚙️

For hvert eksempel-flow nedenfor:

1.  Kopier den tilhørende JSON-kode 📋.
2.  I din Node-RED editor, gå til Menu (≡) -> Import.
3.  Indsæt JSON-koden i "Clipboard" fanen og klik "Import".
4.  Gennemgå og tilpas konfigurationen som beskrevet 🔧.
5.  Deploy flowet ▶️.

---

### 1. MQTT (Publish/Subscribe) 📡

* **Formål:** Demonstrerer afsendelse og modtagelse af beskeder via en MQTT broker. Bruges ofte til at sende sensordata eller kommandoer.
* **Flow Beskrivelse:**
    * En `mqtt in` node abonnerer på topic'et `sensor/temperatur`.
    * En `inject` node sender et timestamp til en `mqtt out` node.
    * `mqtt out` noden publicerer timestampet til topic'et `sensor/temperatur`.
    * Begge MQTT nodes er konfigureret til at bruge en MQTT broker (her `test.mosquitto.org`).
* **Tilpasning:**
    * **MQTT Broker:** Dobbeltklik på `mqtt in` eller `mqtt out` noden. Klik på blyanten ved siden af "Broker" feltet for at redigere broker-konfigurationen. Skift `test.mosquitto.org` og port `1883` til din egen broker, hvis nødvendigt. Tilføj credentials hvis din broker kræver det.
    * **Topic:** Ændr `sensor/temperatur` i `mqtt in` og `mqtt out` noderne til de topics, du vil bruge.

---

### 2. AMQP (Message Queuing med RabbitMQ) 📦

* **Formål:** Viser afsendelse og modtagelse af beskeder via en AMQP broker (RabbitMQ). Bruges til robust, asynkron kommunikation mellem applikationer.
* **Flow Beskrivelse:**
    * En `amqp in` node lytter på en kø (`test_queue`), som er bundet til en exchange (`temp` med routing key `temp`).
    * En `inject` node sender et timestamp til en `amqp out` node.
    * `amqp out` noden sender timestampet til `temp` exchange med routing key `temp`.
    * Begge AMQP nodes er konfigureret til at bruge en AMQP broker på hostnavnet `rabbitmq`.
* **Tilpasning:**
    * **AMQP Broker:** Dobbeltklik på `amqp in` eller `amqp out` noden. Klik på blyanten ved "Broker" for at redigere. Skift `rabbitmq` og port `5672` til adressen på din RabbitMQ server. Tilføj credentials hvis nødvendigt.
    * **Exchange/Queue/Routing Key:** Juster navnene (`temp`, `test_queue`) og routing key (`temp`) i `amqp in` og `amqp out` noderne, så de passer til din RabbitMQ opsætning.

---

### 3. CoAP (Constrained Application Protocol) 💡

* **Formål:** Demonstrerer CoAP som en letvægtsprotokol for IoT, både ved at modtage requests (server-rolle) og sende requests (klient-rolle).
* **Flow Beskrivelse:**
    * **Server-del:** En `coap in` node lytter på stien `/temp` for POST requests. Når en request modtages, formaterer en `function` node payload'en og sender et svar tilbage via `coap response`.
    * **Klient-del:** En `inject` node sender et timestamp til en `coap request` node, som sender en POST request til `coap://aams_test:5683/temp`.
* **Tilpasning:**
    * **Server Port/Sti:** Dobbeltklik på `coap in` noden. Klik på blyanten ved "Server" for at ændre den port, Node-RED lytter på (standard 5683). Ændr stien `/temp` hvis nødvendigt.
    * **Klient URL:** Ret URL'en `coap://aams_test:5683/temp` i `coap request` noden, så den peger på den CoAP-enhed/server, du vil kommunikere med. Juster metode (POST, GET, etc.) og content-format efter behov.
    * **Function Node:** Tilpas logikken i `function` noden efter, hvordan du vil behandle indkommende CoAP data.

---

### 4. Modbus TCP (Industriel Kommunikation) 🔌

* **Formål:** Viser hvordan Node-RED kan agere som en Modbus TCP Master (Client) for at læse data fra en Modbus Slave (Server).
* **Flow Beskrivelse:**
    * En `modbus-read` node er konfigureret til periodisk (hvert sekund) at læse 16 Coils (FC1) fra adresse 1 på Unit ID 1.
    * Noden bruger en Modbus Client konfiguration, der peger på en TCP Host `172.24.0.5` på port `4999`.
    * Resultatet sendes til debug-noder.
* **Tilpasning:**
    * **Modbus Server:** Dobbeltklik på `modbus-read` noden. Klik på blyanten ved "Server". Ret `TCP Host` og `TCP Port` til adressen og porten på din faktiske Modbus TCP slave/server enhed.
    * **Læse Operation:** Juster `Unit-Id`, `FC` (Function Code: 1, 2, 3, 4, etc.), `Address` og `Quantity` i `modbus-read` noden, så den passer til de data, du vil læse fra din Modbus-enhed.
    * **Rate:** Ændr polling-intervallet efter behov.

---

### 5. WebSocket (Real-time Kommunikation) ↔️

* **Formål:** Demonstrerer en WebSocket loopback-forbindelse, hvor Node-RED både er server og klient. Dette er primært til test og demonstration af WebSocket-noderne.
* **Flow Beskrivelse:**
    * En `websocket in` node lytter på stien `/ws/test` (på Node-REDs standard port, typisk 1880).
    * En `inject` node sender et timestamp til en `websocket out` node.
    * `websocket out` noden er konfigureret som en klient, der forbinder til `ws://localhost:1880/ws/test` (sin egen listener).
    * Modtagne beskeder vises i debug-ruden.
* **Tilpasning (for at forbinde til eksterne):**
    * **Node-RED som Server:** Behold `websocket in` noden. Slet `websocket out` og `inject`. Eksterne klienter kan nu forbinde til `ws://<din-node-red-ip>:1880/ws/test`. Sørg for at port 1880 er publiceret, hvis Node-RED kører i Docker.
    * **Node-RED som Klient:** Behold `websocket out` og `inject`. Slet `websocket in`. Dobbeltklik på `websocket out`, klik på blyanten ved "Client", og ret URL'en (`ws://localhost:1880/ws/test`) til den eksterne WebSocket server, du vil sende data til (f.eks. `ws://nr4000:4000/ws/data`).

---

## Hvorfor Lære Disse Protokoller/Teknologier? 🤔

For studerende inden for automation, IT, og ingeniørfag (som dem du underviser på aams, Anders) er kendskab til disse kommunikationsmetoder afgørende af flere årsager:

1.  **Industriel Relevans (Modbus, AMQP):** Modbus 🏭 er stadig en de facto standard i mange industrielle miljøer til kommunikation med PLC'er, sensorer og aktuatorer. AMQP (via RabbitMQ) 📨 bruges ofte i større systemer til pålidelig dataudveksling mellem maskiner og softwarelag. At kunne integrere med disse er essentielt for automationsingeniører.
2.  **IoT Udbredelse (MQTT, CoAP, WebSocket):** Internettet af Ting 📈 vokser eksplosivt. MQTT 📡 er den mest populære protokol til at forbinde millioner af enheder til skyen på grund af dens effektivitet. CoAP 💡 er designet til endnu mere ressourcebegrænsede enheder. WebSockets 🕸️ bruges ofte til at vise realtidsdata fra IoT-enheder på web-dashboards. Kendskab til disse åbner døre til IoT-udvikling.
3.  **Systemintegration:** Moderne systemer består sjældent af én enkelt teknologi. Evnen til at få forskellige systemer, der taler forskellige "sprog" (protokoller), til at kommunikere er en kernekompetence 🤝. Node-RED excellerer her ved at tilbyde en visuel måde at bygge bro mellem disse teknologier.
4.  **Fleksibilitet og Problemløsning:** At forstå fordele og ulemper ved forskellige protokoller gør studerende i stand til at vælge det rigtige værktøj til opgaven 🛠️. Skal data sendes pålideligt? (AMQP). Skal det være letvægtigt og til mange enheder? (MQTT). Skal det være realtid til en browser? (WebSocket).
5.  **Øget Beskæftigelsesværdi:** Virksomheder inden for automation, produktion, smart cities, og softwareudvikling efterspørger medarbejdere, der kan håndtere disse teknologier 💼. At have praktisk erfaring med dem, f.eks. via Node-RED projekter, er et stort plus på CV'et ⭐.

Node-RED fungerer som en fantastisk læringsplatform 🎓, da den abstraherer noget af kompleksiteten væk og lader studerende fokusere på *hvordan* data flyder og *hvordan* systemer forbindes, uden at skulle skrive omfattende kode for hver protokol fra bunden.

## Konklusion 🎉

Disse eksempel-flows giver et udgangspunkt for at arbejde med centrale kommunikationsprotokoller i Node-RED. Ved at importere, tilpasse og eksperimentere med dem, kan man opnå en praktisk forståelse for, hvordan moderne systemer udveksler data.
