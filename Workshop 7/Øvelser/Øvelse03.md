---

## 📋 Opgave 3: Log alle alarmhændelser – Uddybning

### 🌟 Formål

At gemme alle alarmhændelser, så du kan se historik og analysere, hvornår og hvorfor alarmer er blevet udløst.

---

### 📚 Baggrund

Logning af alarmer er vigtigt for at kunne dokumentere fejl, finde mønstre og forbedre systemet. En logfil (fx CSV) gør det nemt at se tilbage og analysere hændelser.

---

### 📝 Trin-for-trin

1. **Tilføj en file-node i Node-RED:**  
   - Find “file”-noden i Node-RED og træk den ind i dit flow.

2. **Forbind alarmen til file-node:**  
   - Forbind output fra din function-node (fra opgave 2) til file-noden.

3. **Formatér log-beskeden:**  
   - Brug en change-node eller function-node til at lave en tekststreng med:
     - Tidspunkt (brug fx `new Date().toISOString()`)
     - Måleværdi
     - Alarmtype (fx “Lav værdi!”, “Høj værdi!”)
   - Eksempel på tekst:
     ```
     2025-08-05T12:34:56Z, 8, Lav værdi!
     ```

4. **Indstil file-node:**  
   - Vælg “append to file” og angiv filnavn, fx `alarmlog.csv`.

5. **Test logningen:**  
   - Udløs en alarm og tjek, at der kommer en linje i din CSV-fil.

---

### 💡 Eksempel

> Når temperaturen er 32°C, skal der logges:  
> `2025-08-05T12:34:56Z, 32, Høj værdi!`

---

### ✅ Aflevering

- Vis din CSV-fil med mindst én alarmhændelse.
- Forklar kort, hvordan dit flow logger alarmer.
- Dokumentér i din