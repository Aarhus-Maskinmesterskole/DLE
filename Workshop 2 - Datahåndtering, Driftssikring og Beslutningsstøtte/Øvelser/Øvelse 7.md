# 📝 Øvelse 7: Alarmflows med Forskellig Alvorlighedsgrad (Warning/Kritisk)

## 🌟 Formål
I denne øvelse skal I bygge intelligente alarmflows, der kan skelne mellem **advarsler** (Warnings) og **kritiske fejl** (Critical errors) baseret på analyseret eller realtidsdata. Formålet er at sikre, at operatører hurtigt kan prioritere handlinger.

---

## 📖 Kontekst for datastrømmene

- Data kommer fra sanity-checks, watchdogs eller beslutningsstøtte (fra Øvelse 6).
- Status på data kan være: OK, Warning eller Error.

## 🔄 Praktisk (step-by-step)

### 1. Definer kriterier for alvorlighedsgrad

Eksempler:
- **Warning:**
  - Temperatur mellem 70°C og 85°C (høj, men ikke kritisk).
  - Tryk mellem 1-1,5 bar (lavt, men stabilt).
- **Critical:**
  - Temperatur > 85°C.
  - Tryk < 1 bar eller trykudsving over 20% på 10 sekunder.

### 2. Opsæt filtrering af status

- Brug en `function` node til at analysere beskeder og tildele "severity" felt.

**Eksempel function til severity:**
```javascript
if (msg.payload.vaerdi > 85) {
    msg.payload.severity = "Critical";
} else if (msg.payload.vaerdi > 70) {
    msg.payload.severity = "Warning";
} else {
    msg.payload.severity = "OK";
}
return msg;
```

### 3. Split beskeder efter alvorlighedsgrad

- Brug en `switch` node:
  - Property: `msg.payload.severity`
  - Rules:
    - == "Critical"
    - == "Warning"

- Så kan I sende beskeder videre til forskellige flows baseret på alvorlighed.

### 4. Håndtér Critical og Warning adskilt

- **Critical handlinger:**
  - Vis rød alarm på dashboard.
  - Log straks til fejllog.
  - Evt. send e-mail/SMS notifikation.

- **Warning handlinger:**
  - Vis gul advarsel på dashboard.
  - Log til almindelig driftsovervågningslog.

**Eksempel:**
- Brug `template` node med rød baggrund for kritisk alarm.
- Brug `notification` node for hurtige pop-up beskeder til operatøren.

### 5. Test alarmflows

- Simulér:
  - Høj temperatur: 75°C (Warning).
  - Ekstrem temperatur: 90°C (Critical).
- Kontroller at:
  - Den rigtige handling udføres i hver situation.
  - Alarmer logges og vises korrekt.

### 6. Gem arbejdet

- Eksporter flowet:
  - Gem som `.json`-fil i din portfolio.

**Navngivning:**
- Brug eksempelvis: `workshop2_oevelse7_alarmflows.json`

---

# 💡 Tips og ekstraudfordringer
- Implementér eskalering: Hvis 3 warnings på 5 minutter, opgrader til critical.
- Tilføj lydnotifikationer på kritiske alarmer.
- Brug "last alarm" widget på dashboard for hurtigt overblik.
