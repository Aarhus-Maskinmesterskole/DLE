# 📝 Øvelse 4: Implementering af Separat Fejllog

## 🌟 Formål

Denne øvelse fokuserer på at opsamle og gemme **fejlhåndteringsdata** separat fra normale måledata. En dedikeret fejllog sikrer bedre overskuelighed, hurtigere fejlanalyse og en mere struktureret tilgang til driftsovervågning.

---

## 📖 Kontekst for datastrømmene

- Fejl kan opfanges både fra sanity-checks (out-of-range værdier) og watchdogs (datastrømstop).
- Disse fejl skal logges separat fra almindelige valide data.

## 🔄 Praktisk (step-by-step)

### 1. Identificér fejlkilder

- Gennemgå jeres flows fra tidligere øvelser (sanity-checks og watchdogs).
- Find de steder, hvor:
  - En `function` node i sanity-check markerer beskeder med `status: "Warning"` eller `status: "Error"`.
  - En watchdog-flow genererer en fejlbesked som "No data from Sensor".

**Handling:**
- Sæt en `link out` node direkte efter de steder, hvor fejl opfanges.
- Navngiv linket fx `Fejl til fejllog` for at sikre konsistens.

**Eksempel på opbygning:**
```
Sanity-Check Error or Watchdog Alarm
      |
  [Link Out: Fejl til fejllog]
```

### 2. Opsaml fejlbeskeder

- Opret en `link in` node et nyt sted i flowet kaldet "Fejllog".
- Forbind `link in` node med alle `link out` noder fra fejlkilderne.

**Formål:**
- Samle alle fejlbeskeder centralt, så de kan behandles og logges samlet.

**Diagram:**
```
[Link In: Fejl til fejllog] --> [Structure Function Node]
```

### 3. Strukturér fejlbeskeden

- Tilføj en `function` node direkte efter `link in` noden.
- Denne skal sikre, at alle fejlbeskeder får en ensartet struktur, uanset om de kommer fra sanity-check eller watchdog.

**Eksempel kode:**
```javascript
msg.payload = {
  timestamp: new Date().toISOString(),
  source: msg.payload.source || "Ukendt", // Hvis ikke angivet
  type: msg.payload.type || "Sanity/Watchdog", // Typen af fejl
  description: msg.payload.description || "Fejl registreret", // Kort beskrivelse
  status: "Error"
};
return msg;
```

**Vigtigt:**
- Hvis fejlen ikke har "source" eller "description", skal default værdier indsættes, så strukturen er komplet.

### 4. Logging til CSV (fejllog)

4.1. **Formatér CSV-strengen:**
- Tilføj endnu en `function` node efter struktureringen.
- Denne function laver en korrekt CSV-linje.

**Eksempel CSV-format function:**
```javascript
msg.payload = `${msg.payload.timestamp},${msg.payload.source},${msg.payload.type},${msg.payload.description},${msg.payload.status}\n`;
return msg;
```

4.2. **Gem til fil:**
- Træk en `file` node ind.
- Konfigurer den til at "Append to file".
- Angiv filnavn fx `error_log.csv`.
- Kontroller at data gemmes korrekt linje for linje.

**Diagram:**
```
[Structure Function] --> [CSV Format Function] --> [File: error_log.csv]
```

### 5. Logging til SQLite (fejllog)

5.1. **Opret en fejltabel:**
- I SQLite-databasen, opret en dedikeret tabel til fejl:

```sql
CREATE TABLE IF NOT EXISTS error_log (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  timestamp TEXT,
  source TEXT,
  type TEXT,
  description TEXT,
  status TEXT
);
```

5.2. **Generér SQL INSERT statements:**
- Tilføj en `function` node efter strukturering (eller split flow).

**Eksempel SQLite insert function:**
```javascript
msg.topic = `INSERT INTO error_log (timestamp, source, type, description, status) VALUES ('${msg.payload.timestamp}', '${msg.payload.source}', '${msg.payload.type}', '${msg.payload.description}', '${msg.payload.status}')`;
return msg;
```

5.3. **Gem til database:**
- Tilslut en `sqlite` node og peg på fejldatabasen.

**Diagram:**
```
[Structure Function] --> [SQL Insert Function] --> [SQLite Node]
```

### 6. Test fejlloggen

- Simulér fejl ved:
  - At sende out-of-range værdier (sanity-check fejl).
  - At stoppe en datastrøm midlertidigt (watchdog fejl).

**Kontroller:**
- At fejlbeskeder vises korrekt i `error_log.csv`.
- At fejlbeskeder indsættes korrekt i `error_log` tabellen i SQLite.

Brug "tail"-kommando eller åbn CSV-fil for at tjekke indholdet.
Brug SQLite Browser eller simple SELECT-statements for at inspicere databaseindhold.

### 7. Gem arbejdet

- Eksporter flowet:
  - Åbn Node-RED Menu > Export > Clipboard.
  - Gem som `.json`-fil i din portfolio.

**Navngivning:**
- Brug eksempelvis: `workshop2_oevelse4_errorlog.json`

---

# 💡 Tips og ekstraudfordringer
- Tilføj kolonne for "severity" (fx Warning, Error, Critical).
- Lav separate CSV-filer pr. dag (navngivning baseret på dato).
- Opret e-mail alarmer ved kritiske fejl direkte fra fejlloggen.

---

# 🎉 Klar til næste øvelse!
Når fejlloggen er stabil, skal vi opsætte et dashboard, der grafisk viser systemets driftstilstand.


