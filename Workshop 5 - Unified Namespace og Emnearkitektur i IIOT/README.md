## 📊 Workshop 5: Modbus TCP ↔ MQTT gateway

### 🌟 **Formål**

* At **læse OG skrive** til en inverter via Modbus TCP.
* At koble en relæstation (fx Raspberry Pi) sammen via MQTT – både for at modtage styrekommando og rapportere status.
* At bygge en gateway, så data og styring kan gå frit mellem inverter, relæstation og bruger (dashboard).
* At forstå to-vejs kommunikation på tværs af industrielle netværk.

---

### 👩‍💻 **Kompetencer du opbygger**

Efter workshoppen kan du:

* Opsætte både **Modbus read** og **Modbus write** til inverter (målinger, status OG styring).
* Lave to-vejs gateway mellem Modbus TCP og MQTT.
* Visualisere, sende og modtage status og styring fra både inverter og relæstation på dashboard.
* Forklare fordele og risici ved at kunne styre anlæg eksternt – og hvordan du kan lave “sikker” gateway.

---

## 🏗️ **Scenarie**

* **Inverter (Modbus TCP):**

  * Kan levere målinger/status (fx hastighed, strøm, fejl)
  * Kan modtage styringskommandoer (fx start/stop, setpunkt)
* **Relæstation (Raspberry Pi):**

  * Kan modtage styrekommando via MQTT (fra dashboard, cloud el.lign.)
  * Kan sende relæstatus/feedback tilbage via MQTT
* **Node-RED:**

  * Forbinder det hele (Modbus TCP og MQTT)
  * Bygger gateway og visualisering

---

## 📋 Øvelser

### **Øvelse 1: Læs målinger fra inverter (Modbus read)**

* Brug “modbus read” til at hente status/målinger fra inverteren.
* Visualisér på dashboard og/eller send videre som MQTT-besked (`station/inverter/status`).

---

### **Øvelse 2: Skriv styring til inverter (Modbus write)**

* Brug “mqtt in” (fx på topic `station/inverter/cmd`) til at modtage kommandoer.
* Forbind til “modbus write” – fx for at sende start/stop/setpunkt til inverteren fra dashboard eller cloud.

---

### **Øvelse 3: Relæstation – modtag og udfør kommandoer via MQTT**

* Brug “mqtt in” på Raspberry Pi til at modtage fx `station/relay/cmd` og tænde/slukke et GPIO-relæ (eller simulering).
* Relæstation sender tilbage status som MQTT-besked (`station/relay/status`).

---

### **Øvelse 4: Visualiser og styr det hele fra dashboard**

* Lav knapper/inputs på dashboard til at sende styrekommandoer (både til inverter og relæ).
* Vis status fra både inverter (målinger, fejl) og relæstation (on/off).
* Prøv at styre begge dele og se status opdateres i realtid.

---

### **Øvelse 5: To-vejs gateway og “echo”**

* Prøv at sende en kommando fra dashboard til inverter → relæstation (eller omvendt) og tjek, at feedback/status kører begge veje.
* Demonstrér at ændringer i inverter/relæ kan ses over MQTT af andre systemer.

---

### **Øvelse 6: Refleksion**

* Hvad kan du bruge sådan en gateway til i virkeligheden?
* Hvorfor er to-vejs styring både en fordel og en risiko?
* Hvad ville du sikre, hvis systemet blev brugt i “den virkelige verden”?

---

### **Noter**

* **Begge retninger:** Modbus TCP <--> MQTT <--> Modbus TCP
  (både læsning og skrivning via inverter, og status/styring på relæstation)
* **Alt kan simuleres** hvis du ikke har adgang til rigtig hardware!
