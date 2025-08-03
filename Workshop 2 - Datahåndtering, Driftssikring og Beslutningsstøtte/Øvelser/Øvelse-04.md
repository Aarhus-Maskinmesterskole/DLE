## 📋 Øvelse 4: Visualisér status og fejl på dashboard

### **Formål**

* At gøre status, fejl og driftstilstand synlig for brugeren i realtid.
* At give et hurtigt overblik over sanity-check, plausibility test og watchdog-status for alle datastrømme.

---

### **Baggrund**

Et godt dashboard giver dig og andre et hurtigt visuelt overblik over systemets sundhed – fx om alt er OK, om der er advarsler, eller om der er kritiske fejl. Farver og ikoner (grøn/gul/rød) hjælper med at prioritere, hvor der skal sættes ind.

---

### **Sådan gør du – step by step**

1. **Installer Node-RED Dashboard (hvis ikke allerede gjort)**

   * Tilføj `node-red-dashboard` via “Manage palette”.

2. **Træk visuelle widgets ind på dit dashboard**

   * Brug fx **“ui\_text”**, **“ui\_gauge”**, **“ui\_led”** eller **“ui\_chart”**.

3. **Vis status for hver datastrøm**

   * Forbind dine flows (med status fra sanity-check, plausibility og watchdog) til dashboard-widgets.
   * Angiv klart for hver datastrøm om status er OK, Warning eller Error.

4. **Brug farver og tydelige labels**

   * Brug grøn for OK, gul for advarsel, rød for fejl.
   * Tilføj evt. en **“ui\_template”** for at lave brugerdefinerede indikatorer.

5. **Vis fejltype og tidspunkt**

   * Hvis der er fejl, vis hvad fejlen er (fx “Value out of range” eller “No data received”).
   * Vis timestamp for seneste fejl.

6. **Opdater automatisk**

   * Sørg for, at dashboardet opdateres i realtid uden manuel refresh.

7. **Test dit dashboard**

   * Simuler både normal drift og fejlscenarier og tjek, at dashboardet reagerer tydeligt.

---

### **Krav til øvelsen**

* Dashboardet skal vise status for hver datastrøm (OK, advarsel, fejl) med farvekoder.
* Fejltyper og tidspunkter skal kunne vises eller findes let på dashboardet.
* Visualisering skal opdateres løbende og være let at aflæse.

---

### **Ekstra for nørderne**

* Lav et samlet “system-status”-felt, der viser om alle systemer kører OK.
* Tilføj “historik” eller “log-overblik” for fejl på dashboardet.
* Brug ikoner, grafer eller egne templates for ekstra tydelighed.

---

### **Når du er færdig**

* Du har nu skabt en driftssikker, valideret og overvåget IIoT-løsning med tydelig visuel status!
