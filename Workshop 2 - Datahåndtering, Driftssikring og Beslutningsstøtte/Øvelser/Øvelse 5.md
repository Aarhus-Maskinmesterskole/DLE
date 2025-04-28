# 📝 Øvelse 5: Grafisk Dashboard med Dynamiske Statusfarver

## 🌟 Formål
I denne øvelse skal I bygge et Node-RED Dashboard, som i realtid viser systemets driftstilstand. I skal bruge farver og grafiske elementer til at give et hurtigt visuelt overblik over målinger og alarmer.

---

## 📖 Kontekst for datastrømmene

- Data kommer fra sanity-checked og watchdog-overvågede datastrømme.
- Status kan være "OK", "Warning" eller "Error".
- Fejl logges separat i fejlloggen (fra Øvelse 4).

## 🔄 Praktisk (step-by-step)

### 1. Installér Node-RED Dashboard
- Hvis du ikke allerede har dashboard installeret:
  - Gå til "Manage Palette" > "Install" > Søg efter `node-red-dashboard` og installer.

### 2. Design dashboard-struktur
- Planlæg minimum tre sektioner:
  - Live målinger (temperatur, tryk, osv.).
  - Statusindikatorer for hver datastrøm.
  - Alarmsektion (vis fejl eller kritiske statusser).

### 3. Visualisér målinger

3.1. **Træk widgets ind:**
- Brug `gauge`, `chart` eller `text` widgets.

3.2. **Vis live data:**
- Forbind datastrøm fra sanity-checked flows til relevante widgets.

**Eksempel opsætning for temperatur:**
- `gauge` node:
  - Label: "Temperatur Sensor 1"
  - Unit: °C
  - Min/Max: Definer passende intervaller (fx -40 til 120).

### 4. Implementér dynamiske statusfarver

4.1. **Brug template eller text node:**
- Træk en `template` node ind for fuld kontrol over farver, eller brug `text` node med dynamiske baggrundsfarver.

4.2. **Eksempel på dynamisk status-farve i en Template node:**
```html
<div style="padding:10px; background-color: {{msg.background}}; color: white;">
  Status: {{msg.payload.status}}
</div>
```

4.3. **Function node til baggrundsfarver:**
```javascript
if (msg.payload.status === "OK") {
    msg.background = "green";
} else if (msg.payload.status === "Warning") {
    msg.background = "yellow";
} else if (msg.payload.status === "Error") {
    msg.background = "red";
}
return msg;
```
- Forbind denne function til template eller text widget.

### 5. Vis alarmer på dashboard

5.1. **Saml fejlmeldinger:**
- Brug output fra fejllog flows.
- Vis fejl i et tekstfelt, liste eller alert-boks på dashboardet.

5.2. **Eksempel:**
- Træk en `text` node ind, vis fejlbeskeder dynamisk efterhånden som de opfanges.

### 6. Test dashboardet

- Simulér:
  - Normale data (OK-status).
  - Out-of-range målinger (Warning-status).
  - Datastrømstop (Error-status).
- Kontroller:
  - Rigtig farveskift i widgets.
  - Live-opdatering af målinger.
  - Alarmbeskeder vises korrekt.

### 7. Gem arbejdet

- Eksporter flowet:
  - Gem som `.json`-fil i din portfolio.

**Navngivning:**
- Brug eksempelvis: `workshop2_oevelse5_dashboard.json`

---

# 💡 Tips og ekstraudfordringer
- Tilføj historiske kurver for temperatur/tryk.
- Lav et samlet "systemstatus" felt baseret på worst-case fra alle datastrømme.
- Brug "groups" i dashboardet til bedre layout og navigation.

---

# 🎉 Klar til næste øvelse!
Når dashboardet kører, skal vi i næste øvelse opbygge beslutningsstøtte baseret på aggregerede data.

