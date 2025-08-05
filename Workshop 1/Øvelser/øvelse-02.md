## **Øvelse 2: MQTT til dig selv – Send og modtag beskeder**

### **Formål**

At lære, hvordan du sender og modtager beskeder via MQTT i Node-RED – i dit eget flow.

---

### **Sådan gør du:**

1. **Opret et nyt flow (valgfrit)**

   * Klik på plus-ikonet øverst for at tilføje et nyt flow, hvis du vil holde øvelsen adskilt.

2. **Træk en “MQTT in”-node ind på arbejdsfladen**

   * Find “MQTT in” i venstremenuen og træk den ud på midten.

3. **Træk en “MQTT out”-node ind på arbejdsfladen**

   * Find “MQTT out” og træk den ud.

4. **Opret en forbindelse mellem de to noder**

   * Træk en linje fra output på “MQTT out” til input på “MQTT in” (eller til en debug-node, hvis du vil se beskeder).

5. **Dobbeltklik på “MQTT in”-noden og vælg broker**

   * Vælg den allerede konfigurerede broker (fx “mqtt-broker”).
   * Skriv et topic, fx `ditnavn/test`.

6. **Dobbeltklik på “MQTT out”-noden**

   * Vælg samme broker.
   * Brug samme topic som ovenfor.

7. **(Valgfrit) Tilføj en debug-node**

   * Træk en debug-node ind, og forbind den til output fra din “MQTT in”-node, så du kan se modtagne beskeder i debug-vinduet.

8. **Deploy (udgiv) dit flow**

   * Klik på “Deploy” oppe til højre for at gemme og aktivere flowet.

9. **Send en besked**

   * Dobbeltklik på “MQTT out”-noden og brug en inject-node til at sende en testbesked.

10. **Se beskeden komme retur**

    * Tjek om din besked bliver modtaget af din egen “MQTT in”-node (og evt. vises i debug-panelet).

---

### **Når du er klar:**

Gå videre til næste øvelse, hvor du skal sende og modtage beskeder sammen med en medstuderende!
