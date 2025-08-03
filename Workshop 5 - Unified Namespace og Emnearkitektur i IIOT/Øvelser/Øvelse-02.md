## 📋 Øvelse 2: Tilføj statusindikator (OK/fejl) med farver

### **Formål**

* At vise tydeligt på dashboardet, om alt er OK – eller der er en fejl.
* At bruge farver eller tekst, så status er let at forstå for alle.

---

### **Baggrund**

Det er vigtigt hurtigt at kunne se, om noget er galt. En simpel statusindikator (fx grøn for OK, rød for fejl) hjælper både dig og andre med at opdage problemer – uden at skulle læse tal eller debug-beskeder.

---

### **Sådan gør du – step by step**

1. **Åbn dit flow fra øvelse 1**

   * Du skal bruge samme flow, hvor du allerede viser en måling.

2. **Tilføj en funktion, der bestemmer status**

   * Træk en “function”-node ind mellem din måling og dashboard-widget.
   * Skriv kode, der vurderer om målingen er OK eller fejl.
     **Eksempel:**

     ```javascript
     // Antag fx temperatur skal være mellem 10 og 30
     if (msg.payload >= 10 && msg.payload <= 30) {
       msg.status = "OK";
     } else {
       msg.status = "FEJL";
     }
     return msg;
     ```

3. **Tilføj en dashboard-widget til status**

   * Brug fx “ui\_text”, “ui\_led” eller “ui\_template”.
   * Forbind function-noden til denne widget.

4. **Gør status visuelt (farver/tekst)**

   * For “ui\_led”: Vælg farve for OK (grøn) og FEJL (rød) under konfiguration.
   * For “ui\_text” eller “ui\_template”: Skift tekstfarve/ikon alt efter status.

5. **Deploy flowet**

   * Klik “Deploy”.

6. **Test indikatoren**

   * Prøv at sende både OK- og fejl-værdier og se status skifte farve eller tekst.

---

### **Krav til øvelsen**

* Dashboardet skal vise status tydeligt – grøn/“OK” når alt er fint, rød/“FEJL” når noget er galt.
* Status skal opdatere automatisk, når nye data modtages.

---

### **Når du er færdig**

* Nu kan du både vise data og se status direkte på dit dashboard!
* Gå videre til næste øvelse: “Lav flere visninger på samme dashboard”.
