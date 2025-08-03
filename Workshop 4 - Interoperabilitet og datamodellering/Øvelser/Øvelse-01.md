## 📋 Øvelse 1: Send data til et fælles topic

### **Formål**

* At lære, hvordan du kan **sende data**, som alle med adgang til samme MQTT-topic kan modtage.
* At opleve, at et fælles topic fungerer som en “opsalgstavle” for beskeder.

---

### **Baggrund**

I MQTT er et “topic” ligesom en fælles kanal eller opslagstavle, hvor alle kan skrive og læse beskeder.
Hvis du sender en besked til et åbent topic, kan alle andre, der lytter på det samme topic, modtage beskeden – også dine medstuderende.

---

### **Sådan gør du – step by step**

1. **Åbn Node-RED**

   * Log ind på din Node-RED.

2. **Find eller opret din MQTT broker-forbindelse**

   * Brug fx `test.mosquitto.org` som broker (port 1883, ingen login).

3. **Aftal et fælles topic med din klasse**

   * Fx `klasse/test` eller `workshop/chat`.

4. **Træk en “MQTT out”-node ind på dit flow**

   * Sæt topic til det fælles topic, I har aftalt.

5. **Tilføj en “inject”-node**

   * Brug denne til at sende fx din temperatur, dit navn eller en kort besked.

6. **Forbind inject-node til MQTT out-node**

   * Sådan sender du beskeden ud på det fælles topic.

7. **Deploy flowet**

   * Klik “Deploy” oppe til højre.

8. **Test ved at sende en besked**

   * Tryk på inject-knappen – nu ligger din besked på det fælles topic!

---

### **Krav til øvelsen**

* Du skal kunne sende mindst én besked til det fælles topic, så andre kan modtage den.

---

### **Når du er færdig**

* Gå videre til næste øvelse, hvor du lærer at **modtage beskeder fra dine medstuderende**!
