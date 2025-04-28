# 📝 Øvelse 6: Beslutningsstøtte via Aggregerede Data

## 🌟 Formål
I denne øvelse skal I implementere et beslutningsstøtte-system, hvor handlinger ikke træffes på baggrund af enkeltdatapunkter, men på baggrund af **analyserede og aggregerede data**. Formålet er at simulere en intelligent reaktion på trends og gennemsnit i datastrømmene.

---

## 📖 Kontekst for datastrømmene

- I har allerede sanity-checked data, driftsovervågning og dashboard.
- Nu skal I opsummere og analysere målinger over tid.
- Beslutninger skal træffes baseret på fx gennemsnit, maksimum eller minimum over en given periode.

## 🔄 Praktisk (step-by-step)

### 1. Definer beslutningskriterier

- Eksempler:
  - Hvis **gennemsnitstemperaturen** de sidste 60 sekunder overstiger 70°C, send en alarm.
  - Hvis **minimum tryk** de sidste 5 minutter er under 1 bar, udløs en advarsel.

**Tip:** Vælg selv relevante sensorer og værdier baseret på jeres flows.

### 2. Saml data over tid

- Brug en `rbe` node eller `delay` + `buffer` teknikker til at samle målinger.
- Alternativt brug en `join` node sat til at samle x antal beskeder over tid.

**Eksempel:**
- `delay` node til at "samle" data med et fast interval.
- `join` node konfigureret til "manual mode" med 10-20 beskeder.

### 3. Aggreger data

- Brug en `function` node til at analysere den samlede datastrøm.
- Beregn gennemsnit, maksimum eller minimum.

**Eksempel function til gennemsnit:**
```javascript
let sum = 0;
for (let i = 0; i < msg.payload.length; i++) {
    sum += msg.payload[i].vaerdi;
}
let average = sum / msg.payload.length;

msg.payload = {
  average: average,
  timestamp: new Date().toISOString()
};
return msg;
```

### 4. Træf beslutning baseret på aggregerede data

- Brug en `switch` node efter aggregationsfunktionen:
  - Hvis gennemsnittet > 70°C, send en alarm.
  - Ellers gør intet eller send "OK" besked.

**Eksempel:**
- Property: `msg.payload.average`
- Rule: > 70
- Output 1: Alarmflow
- Output 2: Ingen handling eller log OK.

### 5. Aktiver alarm eller handling

- Hvis beslutningskriteriet er opfyldt:
  - Send alarm til dashboard (fx rød advarsel).
  - Log hændelsen i fejllog eller beslutningslog.
  - Evt. send e-mail notifikation (ekstra bonus).

### 6. Test beslutningsstøtten

- Simulér forskellige temperatur- og trykprofiler.
- Kontroller, at:
  - Ingen alarmer udløses ved normale forhold.
  - Alarmer udløses korrekt, når grænseværdier overskrides over tid.

### 7. Gem arbejdet

- Eksporter flowet:
  - Gem som `.json`-fil i din portfolio.

**Navngivning:**
- Brug eksempelvis: `workshop2_oevelse6_decision_support.json`

---

# 💡 Tips og ekstraudfordringer
- Brug "rolling average" over tid, i stedet for faste beskedpakker.
- Log beslutninger separat fra fejl og normale data.
- Differentier mellem alarmer på gennemsnit og på maksimumværdier.

---

# 🎉 Klar til næste øvelse!
Når beslutningsstøtten er på plads, skal vi arbejde med at bygge alarmflows med forskellig alvorlighedsgrad (Warning/Kritisk).

