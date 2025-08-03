## 📋 Øvelse 3: Opsæt watchdog for datastrøm

### **Formål**

* At sikre, at dine sensordata ankommer regelmæssigt, og at du hurtigt opdager “døde” eller afbrudte datastrømme.
* At kunne advare, logge og visualisere, når der mangler data fra en sensor.

---

### **Baggrund**

En **watchdog** er en overvågningsmekanisme, der tjekker, om der fortsat kommer data fra hver sensor indenfor et bestemt tidsinterval. Hvis datastrømmen stopper (fx sensor offline, netværksproblem, softwarefejl), skal det opdages og håndteres automatisk.

---

### **Sådan gør du – step by step**

1. **Modtag valideret data fra forrige øvelser**

   * Dit flow skal nu have datapakker med metadata og status fra sanity-check.

2. **Indsæt watchdog-mekanisme**

   * Brug fx [node-red-contrib-watchdog](https://flows.nodered.org/node/node-red-contrib-watchdog) eller lav din egen med `delay`, `trigger` og `status`-noder.

3. **Definér timeout for datastrøm**

   * Sæt en tidsgrænse (fx 10 sekunder). Hvis der ikke modtages data indenfor dette interval, skal watchdog advare eller markere fejlsituation.

4. **Opsæt flow**

   * Når ny data modtages:

     * Nulstil watchdog (fx send “reset” til trigger/watchdog-node).
     * Opdater status til “OK”.
   * Hvis timeout overskrides:

     * Sæt status til “Warning” eller “Error”.
     * Send evt. besked til separat fejllog og dashboard.

5. **Eksempel (egenskrevet):**

   * Brug en trigger-node, der sender “Error” efter timeout, med reset ved ny data.
   * Eller brug “watchdog”-node, der automatisk håndterer det.

6. **Debug og visualisering**

   * Tilføj debug-node og/eller dashboard-indikator, så du tydeligt kan se om datastrømmen er aktiv, forsinket eller afbrudt.

7. **Test flowet**

   * Simuler normal datastrøm og tjek at status forbliver “OK”.
   * Stop datastrømmen og tjek, at status ændres og fejl logges/vises.

---

### **Krav til øvelsen**

* Hver datastrøm/sensor skal overvåges af en watchdog.
* Timeout for watchdog skal kunne tilpasses (fx via dashboard eller variable).
* Tab eller afbrydelse af datastrøm skal logges og visualiseres tydeligt.

---

### **Ekstra for nørderne**

* Giv brugeren mulighed for at justere timeout via dashboard.
* Send notifikation (mail, sms, telegram) ved længerevarende afbrud.
* Log alle watchdog-events med timestamp, sensor-id og fejltype.

---

### **Når du er færdig**

* Gå videre til næste øvelse, hvor du visualiserer status og fejl på dashboard!
