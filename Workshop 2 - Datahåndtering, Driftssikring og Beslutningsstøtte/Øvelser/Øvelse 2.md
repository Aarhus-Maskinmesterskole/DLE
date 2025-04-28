# 📝 Øvelse 2: Sanity-checks og Avancerede Watchdog Flows

## 🌟 Formål
Denne øvelse fokuserer på at sikre kvalitet og stabilitet i de opsamlede datastrømme. I skal implementere sanity-checks for at validere, at data ligger inden for realistiske grænser, og opbygge watchdog flows, der overvåger datastrømmens tilstedeværelse og stabilitet.

---

## 📖 Kontekst for datastrømmene

- Data modtaget fra to forskellige protokoller (fra Øvelse 1).
- Sanity-checks skal sikre, at måledata er realistiske.
- Watchdog flows skal detektere tab eller stop af datastrømme.

## 🔄 Praktisk (step-by-step)

### 1. Definer sanity-check regler
- Eksempler:
  - Temperatur skal være mellem -40°C og 120°C.
  - Tryk skal være mellem 0 bar og 10 bar.
- Lav en `function` node efter hver datastrøm til at kontrollere disse regler.

**Eksempel sanity-check function:**
```javascript
if (msg.payload.vaerdi < -40 || msg.payload.vaerdi > 120) {
    msg.payload.status = "Warning";
} else {
    msg.payload.status = "OK";
}
return msg;
```

### 2. Implementér watchdog pr. datastrøm
- Brug en `trigger` node efter sanity-check:
  - Reset hver gang data modtages.
  - Hvis ingen data modtages inden fx 20 sekunder, udløs en alarm.

**Trigger node eksempelopsætning:**
- Send intet ved input.
- Vent 20 sekunder.
- Hvis timeout, send besked: "No data from Sensor_1".

### 3. Opsæt fejlflows
- Ved sanity-fejl:
  - Log fejl separat.
  - Send visuel advarsel til dashboard.
- Ved watchdog-fejl:
  - Log fejl separat.
  - Udløs en kritisk alarm på dashboard.

### 4. Test flows
- Simulér out-of-range data ved at ændre værdier manuelt.
- Simulér datastrømstop ved at deaktivere en input-node.
- Kontroller, at systemet korrekt opfanger og reagerer på fejl.

### 5. Gem arbejdet
- Eksporter flows:
  - Gem som `.json`-fil i din portfolio.

**Navngivning:**
- Brug eksempelvis: `workshop2_oevelse2_sanity_watchdog.json`

---

# 💡 Tips og ekstraudfordringer
- Lav dynamiske sanity-grænser, som kan konfigureres via UI.
- Differentier mellem "Warning" og "Critical" status afhængigt af alvoren.
- Send en e-mail ved kritiske fejl (ekstra bonus).

---

# 🎉 Klar til næste øvelse!
Når sanity-checks og watchdogs fungerer, går vi videre til logging til CSV og database!

