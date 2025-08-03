## 📊 Workshop 2: Øvelsesoversigt med Formål

📚 **Introduktion**

Denne README beskriver øvelserne i Workshop 2, hvor vi arbejder målrettet med datasikkerhed og validering i IIoT-systemer.
Du vil udvikle praktiske færdigheder inden for sanity-check, plausibility tests, watchdog-mekanismer og håndtering af timestamp/metadata.

---

### 📋 Øvelse 1: Tilføj timestamp og metadata til data

**Formål:**

* At sikre, at alle indkommende data er forsynet med tidsstempel og nødvendig metadata.
* At understøtte sporbarhed og efterfølgende fejlanalyse.
* At opnå ensartethed i datahåndteringen.

**Krav:**

* Alle data skal forsynes med timestamp, unit, source og status.
* Metadata skal tilføjes direkte i flowet, så det følger hver datapakke.

---

### 📋 Øvelse 2: Implementér sanity-check og plausibility test

**Formål:**

* At beskytte systemet mod ugyldige eller usandsynlige data.
* At kunne fange fejlmålinger eller defekte sensorer i realtid.
* At arbejde med dynamiske (let-ændrede) grænseværdier uden flow-deploy.

**Krav:**

* Opsæt sanity-check og plausibility test for hver datastrøm.
* Grænseværdier skal kunne opdateres uden at flowet skal deployes på ny.
* Alle “failed checks” skal markeres tydeligt i data eller fejllog.

---

### 📋 Øvelse 3: Opsæt watchdog for datastrøm

**Formål:**

* At overvåge, om datastrømme er aktive og opdateres som forventet.
* At detektere tab af forbindelse, “døde” sensorer eller uregelmæssig opdatering.
* At reagere hurtigt på manglende data.

**Krav:**

* Implementér watchdog-mekanismer for hver datastrøm/sensor.
* Watchdog skal kunne indikere både OK, warning og error.
* Tab af data skal logges separat med timestamp og sensor-id.

---

### 📋 Øvelse 4: Visualisér status og fejl på dashboard

**Formål:**

* At gøre status, fejl og driftstilstand tydeligt for brugeren i realtid.
* At visualisere resultater fra sanity-checks, plausibility tests og watchdogs med letforståelige indikatorer (fx grøn/gul/rød).
* At give et hurtigt overblik over hele systemets sundhed.

**Krav:**

* Dashboard skal vise status for hver datastrøm (OK, advarsel, fejl).
* Fejltyper og tidspunkter skal kunne vises/udtrækkes for analyse.
* Visualisering skal opdateres automatisk og være let at aflæse.

---

📢 **Husk:**
Øvelserne bygger ovenpå hinanden – en god timestamp- og sanity-check-struktur danner grundlag for resten!
Vi forventer grundighed og aktiv refleksion over, hvordan jeres løsninger kan bruges til **robust og driftssikker IIoT**.

Vi glæder os til at se, hvordan I løser opgaverne!
