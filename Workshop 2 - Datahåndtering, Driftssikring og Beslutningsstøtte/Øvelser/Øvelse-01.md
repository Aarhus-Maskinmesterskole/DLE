Ja! Her får du en **komplet beskrivelse af Øvelse 1** med formål, baggrund, step-by-step og konkrete krav – klar til brug i README, opgaveark eller LMS.

---

## 📋 Øvelse 1: Tilføj timestamp og metadata til data

### **Formål**

* At sikre, at alle indkommende data i Node-RED automatisk beriges med et præcist tidsstempel (timestamp) og relevant metadata.
* At understøtte sporbarhed, fejlfinding og efterfølgende analyse af IIoT-data.

---

### **Baggrund**

I industrielle systemer er det afgørende, at al data kan spores og sættes i kontekst. Metadata som **timestamp**, **unit** (måleenhed), **source** (datakilde) og **status** gør det muligt at analysere, validere og dokumentere data – også længe efter de er modtaget.

---

### **Sådan gør du – step by step**

1. **Opsæt dataindsamling i Node-RED**

   * Brug fx en “inject”-node, MQTT-in eller anden datakilde som input.

2. **Tilføj en “function”-node**

   * Tilføj en function-node lige efter din datakilde.
   * I function-node skal du tilføje/indsætte følgende metadata til msg-objektet:

     * `msg.timestamp` – Sæt til `Date.now()` eller brug `msg.payload.timestamp` hvis allerede til stede.
     * `msg.unit` – Sæt til måleenheden, fx `"°C"`, `"Pa"`, `"V"` osv.
     * `msg.source` – Sæt til navnet på din sensor, topic eller input-node.
     * `msg.status` – Sæt standardstatus til fx `"OK"`.

3. **Eksempel på function-kode:**

   ```javascript
   msg.timestamp = Date.now();
   msg.unit = "°C";
   msg.source = "sensor1";
   msg.status = "OK";
   return msg;
   ```

4. **Debug og kontrol**

   * Tilføj en debug-node for at se, hvordan data nu altid indeholder metadata.

5. **Test dit flow**

   * Inject/simuler data og tjek at alle felter udfyldes korrekt – også ved forskellige input.

---

### **Krav til øvelsen**

* Alle datapakker, der forlader dit flow, skal have **timestamp**, **unit**, **source** og **status** påført.
* Metadata skal automatisk tilføjes – ikke manuelt for hvert datapunkt.
* Du skal kunne demonstrere, at dit flow virker for flere datatyper (fx temperatur, tryk, spænding osv.).

---

### **Ekstra for nørderne**

* Hent unit/source dynamisk ud fra input eller config.
* Brug moment.js eller native `toLocaleString()` til at formatere tidsstempel læsbart.
* Tilføj ekstra metadata, fx “location”, “deviceId”, eller “alarmStatus” hvis relevant.

---

### **Når du er færdig**

* Gå videre til næste øvelse, hvor du skal validere dine data med sanity-check og plausibility test!

---

Sig til, hvis du ønsker samme format for Øvelse 2 – eller ønsker denne omskrevet til ultrakort “huskeliste”!
