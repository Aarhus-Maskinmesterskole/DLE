## **Øvelse 8: Eksperimentér med forskellige payload-formater**

### **Formål**

At forstå forskellen på forskellige typer data (payloads), der kan sendes via MQTT – og hvordan du håndterer og visualiserer dem i Node-RED.

---

### **Sådan gør du:**

1. **Opret eller brug et eksisterende MQTT-flow**

   * Brug din “MQTT out”-node og “MQTT in”-node.

2. **Send en simpel tekstbesked**

   * Brug en inject-node til at sende en tekststreng (fx “Hej verden”).

3. **Send et tal**

   * Skift inject-node til at sende et heltal eller decimaltal (fx 42 eller 23.5).

4. **Send et JSON-objekt**

   * Indstil inject-node til at sende et JSON-objekt, fx:
     `{ "temp": 21.4, "unit": "C" }`

5. **Modtag og visualisér data**

   * Tilføj debug-node for at se, hvordan data vises.
   * Prøv at trække en **dashboard widget** (fx gauge eller chart) ind og vis tallene i realtid.

6. **Tjek hvordan Node-RED håndterer de forskellige formater**

   * Notér, hvordan tekst, tal og JSON ser ud i debug-vinduet og på dashboard.

---

### **Når du er klar:**

Du har nu praktisk erfaring med at sende og modtage forskellige datatyper via MQTT og kan visualisere dem i Node-RED!
