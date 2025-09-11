## **Øvelse 4: MQTT ekstern datastrøm (public topic på test.mosquitto.org)**

### **Formål**

At lære at abonnere på en ekstern (offentlig) MQTT-datastrøm og se live-data i Node-RED.

---

### **Sådan gør du:**

1. **Find et offentligt topic**

   * Brug fx et af disse eksempler (eller spørg underviseren for aktuelle topics):

     * `sensors/temperature`
     * `test/topic`
     * `nodemcu/feeds/temperature`
     * (Du kan også lytte på wildcard: fx `#` for alle beskeder)

2. **Træk en “MQTT in”-node ind på arbejdsfladen**

   * Sæt broker til **test.mosquitto.org** (port 1883).

3. **Sæt topic**

   * Indtast det valgte offentlige topic, du vil abonnere på.

4. **Tilføj en debug-node**

   * Forbind debug-node til din “MQTT in”-node, så du kan se alle indkomne beskeder i debug-vinduet.

5. **Deploy dit flow**

   * Klik “Deploy” for at aktivere lytningen.

6. **Se beskeder i debug-panelet**

   * Hvis datastrømmen er aktiv, vil du løbende se nye beskeder poppe op.
   * Hvis der ikke kommer beskeder, så prøv et andet offentligt topic – evt. brug wildcard `#`.

---

### **Ekstra:**

Prøv at kombinere denne datastrøm med en graf eller dashboard i Node-RED – fx vis temperaturmålinger som en kurve.

---

### **Når du er klar:**

Gå videre til næste øvelse, hvor du skal eksperimentere med MQTT-funktioner som retain, QoS og last will!
