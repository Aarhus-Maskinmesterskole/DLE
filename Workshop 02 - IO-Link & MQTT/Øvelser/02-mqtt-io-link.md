# Dag 2: IO-Link & MQTT – Øvelser

Denne lektion skal du lære at arbejde med MQTT i Node-RED og hente data fra en IO-Link enhed via MQTT. Opgaverne guider dig igennem opsætning, modtagelse og behandling af data.

---

## Hvad er `test.mosquitto.org`?
Vi starter med at forestille os **skolegårdens kæmpe opslagstavle**.
Alle må hænge en seddel op under en bestemt overskrift—fx “dyr/kat”—og alle andre kan læse sedlen eller hænge en ny seddel under samme overskrift. Ingen ejer tavlen, og intet er hemmeligt.

`test.mosquitto.org` er præcis sådan en **fælles opslagstavle på internettet** for små beskeder mellem ting (computere/sensorer).
I MQTT-verdenen hedder overskrifterne **“topics”**. Når du “skriver en seddel”, kaldes det **publish**; når du står og kigger på en overskrift for at se nye sedler, hedder det **subscribe**.

Et par enkle regler i den her legeplads-analog:

* **Alle kan læse og skrive**, så skriv **ingen hemmeligheder**.
* Tavlen er **kun til øvelse**—nogle gange er der meget støj, eller den virker ikke perfekt.
* Der findes både **åbne hængelåse** (ingen sikkerhed) og **låste** (krypteret) måder at hænge sedler op på—men tavlen er stadig offentlig.

Kort sagt: `test.mosquitto.org` er en **gratis, offentlig øve-tavle** for MQTT-beskeder, hvor man lærer at sende og modtage uden at skulle sætte sin egen tavle op.


## 1️⃣ Introduktion til MQTT i Node-RED
**Opgave 1:**
- Opret forbindelse til en MQTT-broker (fx test.mosquitto.org eller lokal broker).
- Brug en MQTT-in node til at abonnere på et test topic (fx `test/io-link`).
- Brug en Inject-node til at sende en testbesked via en MQTT-out node på samme topic.
- Se beskeden i Debug-vinduet.

**Step-by-step:**
1. Opret en MQTT-in node
   <img width="3447" height="1732" alt="image" src="https://github.com/user-attachments/assets/40658a9d-a81b-4e49-8d9f-b304bcf215d8" />
2. Tryk på MQTT-in noden
   <img width="3452" height="1732" alt="image" src="https://github.com/user-attachments/assets/8f3be099-c195-4e7b-b7cc-dc810c7f0b26" />
3. Tryk på **+** for at redigere server config
   <img width="3452" height="1725" alt="image" src="https://github.com/user-attachments/assets/7c7ef2db-c4cd-4134-822f-f514beac898a" />
4. Indsæt følgende for broker: `test.mosquitto.org` + port: `1883` og tryk på *Add/Update*
   <img width="3447" height="1725" alt="image" src="https://github.com/user-attachments/assets/afd81183-18ee-49c3-9046-34f7b9758487" />
5. Indsæt topic: `test/io-link` og tryk derefter done.
    <img width="3445" height="1732" alt="image" src="https://github.com/user-attachments/assets/c1eda04a-7d21-4502-a999-682b73a780f9" />
6. Indsæt en debug node og forbind til MQTT-in noden.
    <img width="3447" height="1725" alt="image" src="https://github.com/user-attachments/assets/1be93cdf-3946-46b3-9832-f7c9fa2a3d7e" />
7. Opret en MQTT-out node
    <img width="3447" height="1720" alt="image" src="https://github.com/user-attachments/assets/e7b23c5c-d84d-46c4-9f68-4797e487f4ed" />
8. Dobbelt klik på MQTT-out node
    <img width="3450" height="1730" alt="image" src="https://github.com/user-attachments/assets/5f87711a-baa3-4bbb-a040-72a4969118c2" />
9. vælg samme broker + topic.
    <img width="3447" height="1730" alt="image" src="https://github.com/user-attachments/assets/ae74b25f-957e-4d15-a5db-35fdf0ea6d8d" />
10. Opret en Inject-node, og forbind til MQTT-out node.
    <img width="3447" height="1720" alt="image" src="https://github.com/user-attachments/assets/602d8b86-24ea-4237-a3eb-50520243342b" />
11. I Inject-node, tryk på det lille ur ved `msg.payload=` for at vælge datatype `string` -> `az`
    <img width="3450" height="1735" alt="image" src="https://github.com/user-attachments/assets/18239d08-b533-4c6a-bc18-0a85d3735503" />
12. Indsæt `string` som du vil have sendt til MQTT-out.
    <img width="3445" height="1725" alt="image" src="https://github.com/user-attachments/assets/06c5fb96-abaf-4494-84dd-0a621af51e96" />
14. Tryk på den røde Deploy i højre øverste hjørne og test at beskeder modtages.
    <img width="3445" height="1727" alt="image" src="https://github.com/user-attachments/assets/ecf10749-2946-4659-af5c-b02a44155976" />

---

## 2️⃣ Forbind til skolens MQTT broker
**Opgave 2:**

1. Indsæt en MQTT-in node.
   <img width="3447" height="1722" alt="image" src="https://github.com/user-attachments/assets/6b21b173-70c7-47c9-8f09-3b47a1af0335" />
2. Dobbelt klik på MQTT-in node.
   <img width="3450" height="1727" alt="image" src="https://github.com/user-attachments/assets/260d59f8-4394-4598-9109-e727eb821cda" />
3. Tryk på **+**
   <img width="3442" height="1727" alt="image" src="https://github.com/user-attachments/assets/7225e674-e923-4ece-aa77-acbded263737" />
4. Indsæt følgende og tryk *Add*
   - **Server:** 142.93.135.2
   - **Port:** 1883
   <img width="3450" height="1725" alt="image" src="https://github.com/user-attachments/assets/e6205d78-7284-44fa-a284-720916f3e25b" />
5. Indsæt `#` i topic og tryk *Done*
   <img width="3447" height="1735" alt="image" src="https://github.com/user-attachments/assets/9f4c3c49-d023-4bbc-bac8-02c778df72a3" />
6. Indsæt Debug node og forbind til MQTT-in node
   <img width="3445" height="1715" alt="image" src="https://github.com/user-attachments/assets/1d016086-1526-4024-b25b-c3c0f2502920" />
7. Tryk Deploy og bemærk det data som vælder ind i debug vinduet
   <img width="3447" height="1730" alt="image" src="https://github.com/user-attachments/assets/0bbb1359-8192-4031-8fdb-06217d48471c" />


---

## 3️⃣ Parse og Brug IO-Link Data
**Opgave 3:**
- IO-Link data sendes ofte som JSON. Parse dataen og vis fx alle IO-Link masterens sensor data i Dashboard.

**Step-by-step:**
1. Tilføj en Function node efter din MQTT-in node.
   <img width="3447" height="1725" alt="image" src="https://github.com/user-attachments/assets/be463255-4ec5-40fe-85fe-b7749be3a25e" />
2. Ændre topic i MQTT-in node til det topic i indstillede i IO-Link AL1350 fx `dle/gr1/distance`.
3. Tilslut Function node til en Debug node og Dashboard-node (fx tekst eller gauge) for at vise værdien.
   <img width="3450" height="1720" alt="image" src="https://github.com/user-attachments/assets/fcbd73b5-e57e-4587-a08a-ff98077ee708" />
4. Indsæt følgende i Function node
   ```javascript
   var data = {
    Distance : Number(msg.payload)
   }
   msg.payload = data
   return msg;
   ```
   <img width="3450" height="1725" alt="image" src="https://github.com/user-attachments/assets/4c9a1756-5771-47fb-a49e-847139cfa903" />
5. Dobbelt klik `Gauge` og indsæt som følgende
   <img width="3442" height="1717" alt="image" src="https://github.com/user-attachments/assets/e648a673-3a46-4f25-bfae-b9b68997dcba" />
6. Deploy flowet.
   <img width="3442" height="1727" alt="image" src="https://github.com/user-attachments/assets/4f731184-54da-46f9-a4d1-a35892f3fe2a" />
7. Gå til Web-UI og se jeres data i jeres `gauge`
    <img width="3445" height="1922" alt="image" src="https://github.com/user-attachments/assets/62cc164d-90d2-4283-988d-8b114b7add44" />

---

## 4️⃣ Metadata og Status Information
**Opgave 4:**
- Ofte så fås sensordata uden metadata eller statusinformation. Lav et flow, der tjekker for tidsstempel, enhedens ID og status.

**Step-by-step:**
1. Tilføj en ny Function-node efter den Function node i har.
   <img width="3450" height="1727" alt="image" src="https://github.com/user-attachments/assets/4271d4a5-fcbd-4cb5-a786-a93a00fab57c" />
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
   <img width="3445" height="1732" alt="image" src="https://github.com/user-attachments/assets/c77f0ce7-b413-42b3-bfe4-6ff98dd7311e" />
4. Deploy flowet og test med forskellige beskeder.
   <img width="3442" height="1722" alt="image" src="https://github.com/user-attachments/assets/e466d1f0-8327-4e56-89a9-aa3473f97169" />
5. Tilføj Meta data så vi opnår `node.status({fill:"green",shape:"ring",text:"Metadata present"});` i den næste Function node
   <img width="3450" height="1720" alt="image" src="https://github.com/user-attachments/assets/7ac2672a-a508-4599-8955-9e8edbedf175" />

---

## 5️⃣
**Opgave 5:**
Tilføj flere sensorer ig vis data via dashboard

---

## 6️⃣ Ekstra: Simuleret IO-Link Data
**Opgave 6:**
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
