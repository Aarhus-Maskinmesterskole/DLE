## 📋 Øvelse 1: Byg et dashboard til én måling

### **Formål**

* At lære, hvordan du kan vise fx temperatur, tryk eller en anden måling direkte på et Node-RED dashboard.
* At opleve, hvordan live-data bliver synlige og lette at forstå – også uden teknisk baggrund.

---

### **Baggrund**

Et dashboard gør det muligt for dig (og andre) at følge med i målinger i realtid – uden at skulle kigge ind i flows eller kode. Det er her, IIoT-data bliver til “noget du kan se”.

---

### **Sådan gør du – step by step**

1. **Åbn Node-RED**

   * Log ind og gå ind på dit workspace.

2. **Installer Node-RED dashboard (hvis ikke allerede gjort)**

   * Gå til “Manage palette” > “Install” og søg på `node-red-dashboard`.
   * Klik “install”, hvis dashboardet ikke allerede findes.

3. **Træk en datakilde ind**

   * Brug fx en “inject”-node, en “mqtt in”-node eller en “modbus read”-node – alt efter hvad du har data fra (fx temperatur).

4. **Træk en dashboard-widget ind**

   * Find “ui\_gauge”, “ui\_text” eller “ui\_chart” i paletten til venstre (under “dashboard”).
   * Træk den ind på dit flow.

5. **Forbind datakilden til dashboard-widget**

   * Forbind din måling direkte til widget’en (fx “inject” → “ui\_gauge”).

6. **Konfigurer widget’en**

   * Dobbeltklik på widget’en.
   * Skriv en passende label (“Temperatur” eller lign.), og vælg enhed, min/max-værdier, osv.

7. **Deploy flowet**

   * Klik “Deploy” øverst til højre.

8. **Åbn dashboardet**

   * Gå til `http://[din-ip-adresse]:1880/ui` i din browser.
   * Se din måling live!

---

### **Krav til øvelsen**

* Du skal kunne vise mindst én måling live på dit dashboard (fx temperatur, tryk, eller besked).
* Målingen skal opdateres, når data ændrer sig.

---

### **Når du er færdig**

* Prøv at sende forskellige værdier ind og se dem opdateres på dashboardet.
* Gå videre til næste øvelse, hvor du tilføjer statusindikator (OK/fejl) med farver!
