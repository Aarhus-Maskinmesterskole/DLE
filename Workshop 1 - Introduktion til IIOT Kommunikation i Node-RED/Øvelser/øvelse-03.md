## **Øvelse 3: MQTT til/fra medstuderende (test.mosquitto.org)**

### **Formål**

At prøve at sende og modtage MQTT-beskeder mellem dig og en medstuderende ved hjælp af en offentlig MQTT-broker: **test.mosquitto.org**.

---

### **Sådan gør du:**

1. **Find sammen med en medstuderende**

   * Aftal, hvem der starter med at sende, og hvem der modtager.

2. **Aftal et fælles topic**

   * Vælg et topic, I begge kan bruge (fx `gruppeX/chat` eller `iot/testgruppe`).

3. **Indstil broker til test.mosquitto.org**

   * På både din “MQTT in”-node og “MQTT out”-node:

     * Klik på broker-indstillinger.
     * Sæt broker address til `test.mosquitto.org`
       (Port: 1883, ingen brugernavn/password).
     * Vælg eller opret broker-forbindelsen med dette navn.

4. **Sæt topic**

   * Sæt både “MQTT in” og “MQTT out” til jeres fællestopic.

5. **Tilføj inject-node og debug-node**

   * Brug inject til at sende beskeder.
   * Brug debug til at se, hvad du modtager.

6. **Deploy dit flow**

   * Klik “Deploy” for at aktivere.

7. **Send beskeder til hinanden**

   * Én sender – den anden ser beskeden komme ind.
   * Byt roller.

8. **Tjek at beskederne kommer frem**

   * I debug-vinduet bør begge kunne se beskeder fra hinanden.

---

### **Når du er klar:**

Gå videre til næste øvelse, hvor du skal abonnere på en ekstern MQTT-datastrøm!
