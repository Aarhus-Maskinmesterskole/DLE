## **Øvelse 6: Forbind til MQTT via TLS/kryptering**

### **Formål**

At lære at forbinde til en MQTT-broker via en **krypteret (TLS/SSL) forbindelse**, så data bliver sendt sikkert over nettet.

---

### **Sådan gør du:**

1. **Opret en ny MQTT broker-forbindelse**

   * Dobbeltklik på en af dine “MQTT in”- eller “MQTT out”-noder.
   * Klik på blyanten ud for broker og vælg “Add new mqtt-broker”.

2. **Indstil broker til test.mosquitto.org**

   * Server: `test.mosquitto.org`
   * Port: **8883** (standard for MQTT over TLS)

3. **Slå TLS/SSL til**

   * Marker feltet “Enable secure (SSL/TLS) connection”.
   * Det er normalt ikke nødvendigt at udfylde flere felter for test.mosquitto.org (den accepterer anonyme forbindelser med standardcertifikat).

4. **Gem og vælg broker**

   * Gem indstillinger og brug denne broker i både “MQTT in” og “MQTT out”-node.

5. **Send og modtag en testbesked**

   * Sæt et topic (fx `tls/test`).
   * Brug inject og debug som tidligere.

6. **Tjek forbindelsen**

   * Hvis alt virker, ser du beskeder i debug – nu sendes data krypteret over internettet.

7. **Hvis du oplever fejl**

   * Tjek at du bruger port 8883 og har sat TLS til.
   * Genstart evt. flowet eller spørg underviseren.

---

### **Når du er klar:**

Gå videre til næste øvelse, hvor du arbejder med fysisk IO-Link master som MQTT publisher!
