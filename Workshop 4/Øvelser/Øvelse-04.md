## 📋 Øvelse 4: Lav et lille “fælles dashboard”

### **Formål**

* At vise beskeder fra flere brugere på et fælles Node-RED dashboard.
* At opleve, hvordan et dashboard gør det let at følge med i, hvad der sker på et fælles topic – i realtid.

---

### **Baggrund**

Et dashboard gør det nemt at få overblik over, hvad alle sender og skriver – også for brugere, der ikke arbejder direkte med flows og debug-vinduer. Det kan bruges til chat, status, delte målinger osv.

---

### **Sådan gør du – step by step**

1. **Installer Node-RED dashboard (hvis ikke allerede gjort)**

   * Gå til “Manage palette” og installer `node-red-dashboard`, hvis det ikke er på plads.

2. **Åbn dit flow med “MQTT in”-node på fælles topic**

   * Fx `klasse/chat`.

3. **Træk en “ui\_text” eller “ui\_text\_input” node ind på flowet**

   * “ui\_text” viser beskeder, “ui\_text\_input” kan bruges til at skrive beskeder fra dashboardet.

4. **Forbind “MQTT in”-node til “ui\_text”-node**

   * Nu vil alle beskeder, der modtages på topic’et, blive vist på dashboardet.

5. **(Valgfrit) Tilføj flere visninger**

   * Du kan også bruge “ui\_list”, “ui\_table” eller “ui\_template” for at vise flere beskeder/brugere.

6. **Deploy flowet**

   * Klik “Deploy”.

7. **Åbn dashboardet i din browser**

   * Gå til `http://[din-ip]:1880/ui`.
   * Du ser nu beskederne komme ind, når du eller andre sender til topic’et.

8. **Test og observer**

   * Send beskeder fra dig selv eller andre – se dem dukke op på dashboardet med det samme.

---

### **Krav til øvelsen**

* Dashboardet skal vise beskeder fra flere brugere/flows i realtid.

---

### **Når du er færdig**

* Overvej: Hvordan kan et fælles dashboard bruges i rigtige systemer til status, samarbejde eller alarmer?
* Gå videre til næste øvelse, hvor du reflekterer over sikkerhed og deling!
