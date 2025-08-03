## 📋 Øvelse 4: Skift til HTTPS og gør kommunikationen sikker

### **Formål**

* At lære hvordan HTTPS beskytter din data via kryptering.
* At opleve forskellen mellem usikret (HTTP) og sikret (HTTPS) kommunikation i praksis.

---

### **Baggrund**

HTTPS står for “HyperText Transfer Protocol Secure”. Det er den sikre version af HTTP, hvor al kommunikation er krypteret. Det betyder, at selv hvis nogen “lytter” med på netværket, kan de ikke læse dine beskeder.
Du kan kende HTTPS på hængelåsen i browseren og “https\://” i adressen.

---

### **Sådan gør du – step by step**

1. **Forbered HTTPS i Node-RED**

   * Spørg din underviser, om der er sat en “https in”-node op, eller følg en guide for at aktivere HTTPS i Node-RED (fx ved at bruge selvsigneret certifikat).
   * (Måske arbejder du på en færdig demo, hvis du ikke selv kan opsætte HTTPS.)

2. **Skift din service til HTTPS**

   * Udskift “http in”-node med “https in”-node i dit flow.
   * Sæt samme URL-sti (fx `/test`).
   * Forbind til “http response”-node som før.

3. **Deploy flowet**

   * Klik “Deploy” i Node-RED.

4. **Test din HTTPS-service**

   * Åbn din browser eller Postman.
   * Skriv: `https://[din-ip-adresse]:[port]/test`
   * (Accepter evt. browser-advarsler, fordi du bruger et test-certifikat.)

5. **Send en besked og se respons**

   * Tjek, at du kan sende og modtage data – nu over en sikker forbindelse.

6. **Observer forskellen**

   * Underviseren (eller du selv) kan prøve at “sniffe” trafikken igen – denne gang kan man ikke læse beskeden!
   * Læg mærke til hængelås-symbolet og “https” i adressen.

---

### **Krav til øvelsen**

* Du skal kunne sende/modtage data via HTTPS i Node-RED.
* Du skal kunne forklare, hvorfor data nu er sikret mod afluring.

---

### **Når du er færdig**

* Nu har du prøvet både usikret (HTTP) og sikret (HTTPS) data.
* Gå videre til næste øvelse, hvor du gør sikkerhedsstatus synlig i dit dashboard!
