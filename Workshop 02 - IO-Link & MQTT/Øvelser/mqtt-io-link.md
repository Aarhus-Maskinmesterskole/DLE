# Dag 2: IO-Link & MQTT – Øvelser

Denne dag skal du lære at arbejde med MQTT i Node-RED og hente data fra en IO-Link enhed via MQTT. Opgaverne guider dig igennem opsætning, modtagelse og behandling af data.

---

## 1️⃣ Introduktion til MQTT i Node-RED
**Opgave 1:**
- Opret forbindelse til en MQTT-broker (fx test.mosquitto.org eller lokal broker).
- Brug en MQTT-in node til at abonnere på et test topic (fx `test/io-link`).
- Brug en Inject-node til at sende en testbesked via en MQTT-out node på samme topic.
- Se beskeden i Debug-vinduet.

**Step-by-step:**
1. Opret en MQTT-in node og vælg broker + topic.
2. Opret en MQTT-out node og vælg samme broker + topic.
3. Opret en Inject-node, der sender en testbesked til MQTT-out.
4. Tilslut MQTT-in til Debug-node.
5. Deploy og test at beskeder modtages.

---

## 2️⃣ Parse og Brug IO-Link Data
**Opgave 2:**
- IO-Link data sendes ofte som JSON. Parse dataen og vis fx alle IO-Link masterens sensor data i Dashboard.

**Step-by-step:**
1. Tilføj en JSON-node efter din MQTT-in node.
2. Tilslut JSON-node til en Debug-node for at se det parse-de objekt.
3. Tilslut JSON-node til en Dashboard-node (fx tekst eller gauge) for at vise værdien.
4. Deploy flowet.

---

## 3️⃣ Metadata og Status Information
**Opgave 3:**
- Ofte så fås sensordata uden metadata eller statusinformation. Lav et flow, der tjekker for tidsstempel, enhedens ID og status.

**Step-by-step:**
1. Tilføj en Function-node efter din JSON-node.
2. I Function-node, tilføj kode der tjekker for nødvendige metadata:
   ```javascript
   if (!msg.payload.timestamp || !msg.payload.deviceId || !msg.payload.status) {
     msg.payload = "Fejl: Manglende metadata!";
     node.status({fill:"red",shape:"ring",text:"Metadata missing"});
     return msg;
   }
   node.status({fill:"green",shape:"ring",text:"Metadata present"});
   return null;
   ```
3. Tilslut Function-node til en Debug-node.
4. Deploy flowet og test med forskellige beskeder.

---

## 4️⃣ Ekstra: Simuleret IO-Link Data
**Opgave 4:**
- Hvis du ikke har adgang til rigtig IO-Link data, kan du simulere data med en Inject-node og MQTT-out.

**Step-by-step:**
1. Opret en Inject-node, der sender et JSON-objekt, fx:
   ```json
   { "temperatur": 23, "status": "OK" }
   ```
2. Tilslut Inject-node til en JSON-node og derefter til en MQTT-out node på IO-Link emnet.
3. Brug din MQTT-in node fra tidligere til at modtage og vise dataen.

---

Når du har løst opgaverne, kan du modtage, parse og vise IO-Link data via MQTT i Node-RED!
