## 📋 Øvelse 2: Modtag data fra en medstuderende

### **Formål**

* At lære, hvordan du kan **modtage beskeder** fra andre via et fælles MQTT-topic.
* At opleve, at alle med adgang til samme topic kan se hinandens data.

---

### **Baggrund**

Når du “lytter” på et fælles topic i MQTT, kan du se alle beskeder, der bliver sendt dertil – uanset hvem der sender dem. Det gør det nemt at dele information på tværs af flows og brugere.

---

### **Sådan gør du – step by step**

1. **Åbn dit flow i Node-RED**

2. **Træk en “MQTT in”-node ind på flowet**

   * Sæt broker til fx `test.mosquitto.org`.
   * Sæt topic til det fælles topic, I har aftalt (fx `klasse/test`).

3. **Tilføj en “debug”-node**

   * Forbind “MQTT in”-node til en debug-node, så du kan se beskeder i debug-vinduet.

4. **Deploy flowet**

   * Klik “Deploy”.

5. **Bed en medstuderende om at sende en besked**

   * Når din medstuderende sender en besked til det fælles topic, vil du kunne se beskeden dukke op i debug-vinduet.

6. **Send selv en besked (hvis du ikke allerede har gjort det)**

   * På den måde kan I “skrive sammen” via MQTT.

---

### **Krav til øvelsen**

* Du skal kunne se mindst én besked fra en anden på det fælles topic i dit debug-vindue.

---

### **Når du er færdig**

* Gå videre til næste øvelse, hvor I bygger videre og fx laver en lille “chat”!
