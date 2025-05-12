# 📝 Øvelse 3: Logging til CSV og SQLite Samtidigt (Opdateret)

## 🌟 Formål
Denne øvelse fokuserer på at etablere en **pålidelig og struktureret logging** af IIOT-data til både CSV-filer og/eller SQLite database (advanceret - optional). I skal sikre, at data fra sanity-checked datastrømme gemmes korrekt og kan anvendes til historisk analyse og fejlfinding.

---

## 📖 Kontekst for datastrømmene

- Data er sanity-checked og valideret (fra Øvelse 2).
- Hver datapakke indeholder metadata (timestamp, source, unit, status).
- Både valide data og fejl skal logges (separat).

## 🔄 Praktisk (step-by-step)

### 1. Forbered datastrømmene (Uddybning)

1.1. **Hent output fra sanity-check flows**
- Find de steder i dit flow, hvor data allerede er sanity-checked.
- Placer en `link out` node lige efter sanity-check.
- Navngiv linket fx `Data til logging`.

1.2. **Modtag data til logging**
- Træk en `link in` node ind et nyt sted, og forbind den til resten af logging-flowet.
- Dette skaber et rent setup til logging.

1.3. **Filter beskeder via en function node**
- Træk en `function` node ind efter `link in`.
- Filtrer direkte på `msg.payload.status`, så kun beskeder med "OK" eller "Warning" sendes videre.

**Eksempel function til filtering:**
```javascript
if (msg.payload.status === "OK" || msg.payload.status === "Warning") {
    return msg; // Send beskeden videre
} else {
    return null; // Stop beskeden
}
```

**Diagram indtil videre:**
```
Sanity-checked Data
     |
  [Link Out]  
     |
  [Link In] --> [Function: Status Filter] --> [Til logging]
```

---

### 2. Logging til CSV
- Træk en `file` node ind.
- Konfigurer til at skrive til en lokal CSV-fil.
- Brug en `function` node for at formatere data til CSV string.

**Eksempel CSV-format function:**
```javascript
msg.payload = `${msg.payload.timestamp},${msg.payload.source},${msg.payload.unit},${msg.payload.vaerdi},${msg.payload.status}\n`;
return msg;
```
- Vælg "Append to file" i `file` node indstillinger.

### 3. Logging til SQLite (advanceret)
- Installer `node-red-node-sqlite` hvis nødvendigt.
- Træk en `sqlite` node ind.
- Opret en database og tabel med følgende struktur:
```sql
CREATE TABLE IF NOT EXISTS measurements (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  timestamp TEXT,
  source TEXT,
  unit TEXT,
  vaerdi REAL,
  status TEXT
);
```
- Brug en `function` node til at generere SQL INSERT statements.

**Eksempel SQLite insert function:**
```javascript
msg.topic = `INSERT INTO measurements (timestamp, source, unit, vaerdi, status) VALUES ('${msg.payload.timestamp}', '${msg.payload.source}', '${msg.payload.unit}', ${msg.payload.vaerdi}, '${msg.payload.status}')`;
return msg;
```
- Forbind output til `sqlite` node.

### 4. Samtidig logging
- Brug en `split` eller `link` node til at sende datastrømmen til **både** CSV og database parallelt.

### 5. Test flows
- Send testdata gennem systemet.
- Bekræft:
  - Data skrives korrekt i CSV-fil.
  - Data indsættes korrekt i SQLite database.
- Åbn CSV-filen og databasen og kontrollér indholdet.

### 6. Gem arbejdet
- Eksporter flowet:
  - Gem som `.json`-fil i din portfolio.

**Navngivning:**
- Brug eksempelvis: `workshop2_oevelse3_logging.csv_sqlite.json`

---

# 💡 Tips og ekstraudfordringer
- Tilføj "logtype" kolonne: normal/fejl.
- Log fejl og valide målinger i separate tabeller.
- Brug "date-based" navngivning af CSV-filer.

---

# 🎉 Klar til næste øvelse!
Når logging er på plads, går vi videre til at opsætte en separat fejllog.

