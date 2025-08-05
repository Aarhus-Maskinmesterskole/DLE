## 📋 Øvelse 4: Tilføj en alarm eller advarsel

### **Formål**

* At vise en tydelig alarm på dashboardet, hvis en måling overskrider en fastsat grænse.
* At lære at gøre kritiske hændelser ekstra synlige for brugeren.

---

### **Baggrund**

Alarmer gør det let at opdage farlige eller unormale situationer med det samme. Et godt dashboard viser tydeligt, når noget er galt – fx med farver, tekst eller en blinkende indikator.

---

### **Sådan gør du – step by step**

1. **Brug et af dine eksisterende måleflows**

   * Vælg fx temperatur eller tryk, du allerede viser på dashboardet.

2. **Tilføj en function-node til alarm-logik**

   * Træk en “function”-node ind på flowet før din alarm-widget.
   * Skriv kode, der tjekker om målingen er over/under en grænse.
   * **Eksempel:**

     ```javascript
     if (msg.payload > 30) {
       msg.alarm = "ALARM: For høj temperatur!";
     } else {
       msg.alarm = "";
     }
     return msg;
     ```

3. **Tilføj en dashboard-widget til alarmen**

   * Brug fx “ui\_text”, “ui\_led” eller “ui\_template” til at vise alarmen.
   * For farver: Rød hvis alarm, tom eller grøn hvis alt OK.

4. **Forbind function-node til alarm-widget**

   * Så alarmen vises hver gang værdien ændrer sig.

5. **Deploy flowet**

   * Klik “Deploy”.

6. **Test alarmen**

   * Prøv at sende en værdi, der udløser alarmen – tjek at det er tydeligt på dashboardet.

---

### **Krav til øvelsen**

* Dashboardet skal vise en alarm eller advarselsbesked, hvis en måling går over (eller under) en valgt grænse.
* Alarmer skal være tydelige, fx med rød farve eller stor tekst.

---

### **Når du er færdig**

* Nu kan du både vise data, status og alarmer på dit eget IIoT-dashboard!
* Gå videre til sidste øvelse: “Del dit dashboard med andre”.
