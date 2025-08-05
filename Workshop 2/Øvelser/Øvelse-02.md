## 📋 Øvelse 2: Implementér sanity-check og plausibility test

### **Formål**

* At sikre, at alle data automatisk valideres for at fange målefejl, urealistiske værdier eller defekte sensorer.
* At kunne identificere og håndtere data, der falder uden for forventede (plausible) grænser.

---

### **Baggrund**

Data fra sensorer kan være fejlbehæftede, forkerte eller ligefrem umulige (fx temperatur på -120°C i et kontor!). **Sanity-checks** og **plausibility tests** bruges til at validere, at data er inden for rimelige grænser – og markerer/registrerer målefejl tidligt i flowet.

---

### **Sådan gør du – step by step**

1. **Modtag data med metadata fra Øvelse 1**

   * Dit flow skal nu allerede have timestamp, unit, source og status på hver datapakke.

2. **Indsæt en function-node til sanity-check**

   * Træk en function-node ind efter den node, der tilføjer metadata.

3. **Angiv dynamiske grænseværdier**

   * Opret flow- eller global variables til fx min/max-grænser, så du kan ændre dem uden at deploye flowet igen.

     * Fx: `flow.set("minTemp", 10); flow.set("maxTemp", 40);`

4. **Tilføj sanity-check og plausibility test i function-node**

   * Tjek om `msg.payload` (din måling) ligger inden for de definerede grænser.
   * Opdater `msg.status` til `"OK"`, `"Warning"` eller `"Error"` afhængig af resultatet.

5. **Eksempel på function-kode:**

   ```javascript
   let min = flow.get("minTemp") || 0;
   let max = flow.get("maxTemp") || 100;
   let value = msg.payload;

   if (value < min || value > max) {
       msg.status = "Error";
       msg.errorReason = "Out of bounds";
   } else {
       msg.status = "OK";
   }
   return msg;
   ```

6. **Debug og visualisering**

   * Tilføj en debug-node for at vise alle data inkl. status og evt. fejl.
   * (Valgfrit) Send fejl videre til separat log eller alarm-flow.

7. **Test dit flow**

   * Prøv at sende data indenfor og udenfor grænserne. Tjek at status og eventuel fejlmelding ændres korrekt.
   * Prøv at ændre grænseværdier (fx via et dashboard input eller inject-node) **uden** at deploye flowet på ny.

---

### **Krav til øvelsen**

* Hver datapakke skal gennemgå sanity-check og plausibility test.
* Grænseværdier skal kunne ændres dynamisk (uden deploy).
* Data udenfor grænserne skal markeres tydeligt og kunne viderebehandles separat.

---

### **Ekstra for nørderne**

* Udvid flowet, så forskellige datatyper (fx tryk, temperatur, spænding) får egne grænseværdier.
* Giv brugeren mulighed for at justere grænserne via dashboard.
* Gem alle “Error”-målinger i en separat fejllog med timestamp og årsag.

---

### **Når du er færdig**

* Gå videre til næste øvelse, hvor du skal overvåge, om data ankommer regelmæssigt med en watchdog!
