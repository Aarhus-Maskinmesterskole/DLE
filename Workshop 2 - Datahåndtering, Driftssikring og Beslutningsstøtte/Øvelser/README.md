# 📊 Workshop 2: Øvelsesoversigt med Formål

## 📚 Introduktion

Denne README beskriver de enkelte øvelser i Workshop 2, hvor vi fokuserer på **driftssikring, datahåndtering, beslutningsstøtte og visualisering** i IIOT-systemer.  
Hver øvelse bygger ovenpå den forrige og er designet til at udvikle både tekniske og analytiske færdigheder.

---

## 📋 Øvelse 1: Dataopsamling fra mindst 2 forskellige protokoller

**Formål:**
- At sikre, at dataopsamling ikke afhænger af én enkelt teknologi.
- At træne opsætning af flows med flere samtidige datakilder.
- At introducere kompleksitet i dataintegration fra f.eks. MQTT, Modbus, OPC UA, HTTP eller AMQP.

**Krav:**
- Data skal hentes fra mindst to forskellige protokoller.
- Alle datapakker skal indeholde struktureret metadata.

---

## 📋 Øvelse 2: Sanity-checks og avancerede Watchdog flows

**Formål:**
- At beskytte systemet mod forkerte data og tab af datastrømme.
- At implementere intelligente sanity-checks baseret på dynamiske grænser.
- At bygge watchdog-mekanismer, der overvåger både datastrømmenes tilstedeværelse og kvalitet.

**Krav:**
- Sanity-checks på hver datastrøm.
- Separate watchdogs pr. sensor/stream.

---

## 📋 Øvelse 3: Logging til CSV og SQLite samtidigt

**Formål:**
- At sikre redundans i datalagring.
- At give erfaring med både filbaseret logging (CSV) og databasebaseret logging (SQLite).
- At strukturere data i standardformater velegnet til efterfølgende analyse.

**Krav:**
- Alle valide målinger skal lagres både i CSV-fil og SQLite database.
- Metadata skal logges sammen med målinger.

---

## 📋 Øvelse 4: Implementering af separat fejllog

**Formål:**
- At kunne adskille normal drift og fejlregistrering.
- At gøre fejlanalyse nemmere og mere effektiv.
- At sikre, at fejl ikke overses i store mængder data.

**Krav:**
- Fejl skal registreres i en separat CSV eller database.
- Fejl skal registreres med timestamp, fejltype og kilde.

---

## 📋 Øvelse 5: Grafisk dashboard med dynamiske statusfarver

**Formål:**
- At præsentere data på en brugervenlig måde.
- At understøtte visuel beslutningstagning ved hjælp af statusfarver (grøn, gul, rød).
- At synliggøre systemets driftstilstand i realtid.

**Krav:**
- Live visualisering af målinger og systemstatus.
- Dynamiske farver baseret på data og fejlsituationer.

---

## 📋 Øvelse 6: Beslutningsstøtte via aggregerede data

**Formål:**
- At analysere trends og lave beslutningsgrundlag baseret på historiske målinger.
- At udløse handlinger ikke kun baseret på enkeltdatapunkter, men på gennemsnit, maksimum eller minimum værdier over tid.

**Krav:**
- Implementer flows, der analyserer aggregerede værdier.
- Beslutningsflow skal reagere på f.eks. gennemsnitsværdier over en periode.

---

## 📋 Øvelse 7: Alarmflows med forskellig alvorlighedsgrad (Warning/Kritisk)

**Formål:**
- At skelne mellem alvorlige og mindre alvorlige hændelser.
- At forbedre prioriteringen i driftsovervågningen.
- At skabe automatiske reaktioner på forskellige alarmniveauer.

**Krav:**
- Implementer både warning- og critical-alarmflows.
- Visualiser alarmstatus på dashboard.

---

# 📢 Husk
Alle øvelser bygger ovenpå hinanden — grundlaget fra de første opgaver skal bruges i de sidste.  
Vi forventer høj kvalitet, selvstændighed og grundig dokumentation!

Vi glæder os til at se jeres arbejde!

