# 🧪 Øvelse 7: Visualisering med dashboard og statusindikatorer

## 🎯 Formål
I denne øvelse skal du arbejde med at visualisere sikkerhedsstatus og datatrafik i dit IIOT-system ved hjælp af et brugervenligt dashboard. Målet er at give både teknikere og operatører et intuitivt og overskueligt overblik over systemets tilstand, herunder live status på sensorer, sikkerhedsniveauer og forbindelser. Et godt dashboard er ikke blot en flot præsentation – det er et vigtigt værktøj i sikkerhedsarbejdet, da det understøtter tidlig detektion, beslutningsstøtte og hurtig respons ved fejl.

Ved at opbygge dit eget dashboard i Node-RED lærer du, hvordan man omsætter rådata og hændelser til visuelle indikatorer, som alle på et hold kan forstå. Du vil arbejde med farver, ikoner, grafer og tekstfelter for at vise status som fx OK, ADVARSEL og FEJL – og du vil teste, hvordan systemet reagerer på ændringer i realtid.

Denne øvelse understøtter de øvrige øvelser i Workshop 3 ved at synliggøre de data og hændelser, du har arbejdet med tidligere. Det hjælper dig også med at samle op på observationer fra MITM-simulering, beskyttelse med TLS og logning.

---

## 🛠️ Forudsætninger
- Du har gennemført Øvelse 5 og 6, hvor du arbejdede med logging og alarmering.
- Du har adgang til Node-RED og har installeret `node-red-dashboard` via `Manage Palette`.
- Du har adgang til data med felter som `status`, `payload`, `topic`, `timestamp`, m.m.
- Du har evt. eksisterende flow fra tidligere øvelser, som du kan koble op på dit dashboard.

---

## ⚙️ Trin-for-trin: Byg dit dashboard

### 1. **Opsæt dashboardstruktur**
- Gå til Node-RED menuen og vælg `Dashboard` > `Layout`
- Tilføj en ny `ui_tab`, fx "Systemstatus"
- Opret en eller flere `ui_group` elementer (fx "Sensorer", "Alarmer", "Log")

### 2. **Opret statusindikatorer og visualiseringer**
- Tilføj relevante dashboard widgets:
  - `ui_text` til visning af statusbeskeder
  - `ui_led` til at vise sensorstatus (OK/FEJL)
  - `ui_gauge` til måling af fx temperatur, luftfugtighed, tryk
  - `ui_chart` til at vise historiske værdier over tid
  - `ui_template` til avancerede layout med farver og ikoner

### 3. **Design farvekoder og adfærdslogik**
- Brug `function` eller `switch` nodes til at definere:
  - Grøn = status = "OK"
  - Gul = status = "WARNING"
  - Rød = status = "ERROR"
- Overvej at tilføje blink, ikon eller tekstændringer ved fejl
- Vis fx "Online" / "Offline" afhængigt af sidste payload timestamp

### 4. **Knyt til dit eksisterende flow**
- Træk forbindelser fra din `mqtt-in` node til de relevante visualiseringsnoder
- Brug `function` nodes til at transformere payload til visningsvenligt format
- Brug evt. `rbe` node til kun at vise ændringer, ikke spamme GUI’en

### 5. **Test og valider i realtid**
- Brug `inject` node til at simulere:
  - Normale værdier
  - Grænseværdier (fx temperatur > 60)
  - Udeblevne målinger (manglende kommunikation)
- Kontroller, at dashboard opdateres korrekt og er let at forstå

---

## 📋 Refleksion
Skriv i din portfolio – eller diskuter i gruppen:

- Hvilke typer hændelser eller værdier bør altid vises grafisk?
- Hvilke visuelle elementer hjalp dig bedst med at opdage statusændringer?
- Hvordan kan man designe et dashboard, så det er nyttigt både for teknikere og for ikke-tekniske brugere?
- Hvordan kunne dette dashboard videreudvikles til produktionsbrug (brugerstyring, flere skærme, mobilvisning)?
- Er der risiko for, at for mange informationer i dashboardet gør det uoverskueligt?

> 💡 Et effektivt dashboard kombinerer realtidsdata, design og sikkerhed – og skal kunne bruges under pres.

---

👉 Når du er færdig, går du videre til Øvelse 8, hvor du samler op på hele Workshop 3 og afleverer dokumentation og refleksion.

