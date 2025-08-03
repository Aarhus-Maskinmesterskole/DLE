## **Øvelse 7: Opsæt fysisk IO-Link master som MQTT publisher**

### **Formål**

At lære at forbinde en fysisk IO-Link master til netværket og konfigurere den til at sende data som MQTT-beskeder, som du kan modtage i Node-RED.

---

### **Sådan gør du:**

1. **Tilslut IO-Link masteren til netværket**

   * Sørg for, at IO-Link masteren er korrekt tilsluttet netværket og har forbindelse til strøm og sensorer.

2. **Åbn konfigurationsværktøj til IO-Link masteren**

   * Brug det relevante software/webinterface, der følger med din IO-Link master.

3. **Indstil MQTT publishing**

   * Find MQTT-indstillingerne i masterens konfiguration.
   * Indtast følgende oplysninger:

     * **Broker address:** `test.mosquitto.org`
     * **Port:** 1883 (eller 8883 for TLS, hvis understøttet)
     * **Topic:** Vælg et unikt topic, fx `iolink/data/dinmaster`

4. **Konfigurer payload/data**

   * Vælg hvilke data fra IO-Link sensorer, der skal publiceres.
   * (Ofte kan du vælge JSON-format, enkeltværdier eller rå data).

5. **Gem og genstart om nødvendigt**

   * Gem konfigurationen.
   * Genstart IO-Link masteren, hvis det kræves.

6. **Opret “MQTT in”-node i Node-RED**

   * Abonnér på det samme topic, som IO-Link masteren publicerer til.
   * Brug debug-node til at vise indkomne data.

7. **Bekræft dataflow**

   * Tjek i Node-RED, at der modtages data fra IO-Link masteren.
   * Prøv evt. at ændre på sensoren (fx dække, bevæg, mål temp.) og se opdatering i realtid.

---

### **Hvis du ikke har adgang til fysisk IO-Link master:**

* Brug en demo, simulator, eller følg opsætningen i grupper med én master.

---

### **Når du er klar:**

Du har nu sat fysisk udstyr op til at levere data via MQTT til Node-RED!
