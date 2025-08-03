## 📋 Øvelse 5: Visualiser sikkerhedsstatus på dashboard

### **Formål**

* At gøre det tydeligt for brugeren, om data sendes sikkert (HTTPS) eller usikkert (HTTP).
* At lære at bruge farver eller ikoner til at vise sikkerhedsstatus på dit Node-RED dashboard.

---

### **Baggrund**

Et godt dashboard hjælper dig og andre med at se, om systemet er sikkert – også uden at kende til tekniske detaljer. Med farver, tekst eller ikoner kan du gøre sikkerhed håndgribeligt for alle.

---

### **Sådan gør du – step by step**

1. **Åbn dit flow i Node-RED**

   * Brug det flow, du lavede med HTTP og HTTPS (fx to forskellige endpoints eller en variabel, der skifter mellem dem).

2. **Installer Node-RED dashboard (hvis ikke allerede gjort)**

   * Gå til “Manage palette” og installer `node-red-dashboard`, hvis det mangler.

3. **Tilføj en indikator-widget**

   * Træk fx en **“ui\_text”**, **“ui\_led”**, **“ui\_gauge”** eller **“ui\_template”** node ind på flowet.

4. **Sæt din indikator op**

   * Vis status med tekst (fx “Sikker forbindelse” / “Usikker forbindelse”) **eller**
   * Brug farver: **Grøn** (HTTPS) og **Rød** (HTTP).
   * Du kan skifte status automatisk, hvis du har flows til begge forbindelser.

5. **Forbind indikator til dit flow**

   * Når data sendes via HTTPS, skal indikatoren vise “Sikker”/grøn.
   * Når data sendes via HTTP, skal indikatoren vise “Usikker”/rød.

6. **Deploy og test dashboardet**

   * Åbn dashboardet i browseren (`http://[din-ip]:1880/ui`).
   * Tjek at indikatoren viser rigtigt, alt efter hvilken forbindelse du bruger.

7. **Tag et screenshot**

   * Gem et billede af dashboardet med begge statusser (sikker/usikker).

---

### **Krav til øvelsen**

* Dashboardet skal klart vise, om forbindelsen er sikker (HTTPS) eller usikker (HTTP).
* Farver eller tekst skal bruges, så det er let at forstå – også for ikke-tekniske brugere.

---

### **Når du er færdig**

* Du har nu en visuel indikator for datasikkerhed – nem at forstå for alle!
* Gå videre til næste øvelse, hvor du dokumenterer og sammenligner dine løsninger.
