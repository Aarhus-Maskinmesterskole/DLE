# Workshop 1: Introduktion til IIOT Kommunikation i Node-RED

## 📊 Praktiske Øvelser

De studerende skal gennemføre følgende praktiske øvelser i Node-RED. Hver øvelse har et specifikt formål:

### Øvelse 1: MQTT kommunikation
**Formål:** Lære at etablere letvægts, pub/sub-baseret kommunikation mellem enheder.
- Opret forbindelse til en lokal eller cloud-baseret MQTT-broker.
- Opret et flow hvor en `inject` node sender en temperaturværdi som publish.
- Opret et flow der subscribes til emnet og viser beskeden i `debug`.
- Tilføj et timestamp til hver besked.

### Øvelse 2: Modbus TCP/IP kommunikation
**Formål:** Lære at integrere med klassiske industrielle enheder via Modbus protokollen.
- Installer og konfigurer en Modbus TCP simulator/server.
- Læs en coil eller holding register ind i Node-RED.
- Vis resultatet i `debug`.
- Lav fejlhåndtering hvis forbindelsen mistes.

### Øvelse 3: HTTP/REST API kommunikation
**Formål:** Lære at hente eksterne data fra webservices ved hjælp af HTTP forespørgsler.
- Lav en `http request` node der henter data fra en åben API (fx OpenWeatherMap).
- Parse svaret (JSON) og vis en specifik værdi i `debug`.

### Øvelse 4: CoAP kommunikation (valgfri/bonus hvis muligt)
**Formål:** Få kendskab til CoAP som en lav-overhead protokol til små enheder.
- Simuler eller forbind til en CoAP server.
- Lav en simpel `coap request` til en sensor og vis respons.

### Øvelse 5: OPC UA kommunikation
**Formål:** Forstå hvordan OPC UA muliggør sikker og pålidelig maskindataudveksling i industrielle systemer.
- Forbind Node-RED til en OPC UA server (f.eks. en simulator).
- Læs en variabel (fx temperatur eller tryk).
- Håndter fejl, hvis forbindelsen til serveren afbrydes.

### Øvelse 6: AMQP kommunikation
**Formål:** Lære at bruge avanceret beskedhåndtering gennem køer og sikre leverancer.
- Opsæt en RabbitMQ server (lokalt eller cloud).
- Send en besked til en kø via en `amqp out` node.
- Modtag beskeden via en `amqp in` node i et andet flow.
- Demonstrer at beskeden ikke går tabt ved midlertidig netværksfejl.

### Krav til alle Øvelser
- Data skal være **tidsstemplet**.
- Der skal være **fejlhåndtering** i flows hvor det er muligt.
- Flows skal være **gemt og dokumenteret** som JSON-filer.
- Resultater skal vises i Node-RED's `debug` eller Dashboard.

---
