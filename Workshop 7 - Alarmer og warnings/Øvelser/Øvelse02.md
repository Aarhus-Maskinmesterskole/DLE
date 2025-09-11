---

## 📋 Opgave 2: Byg alarm-logik i Node-RED – Uddybning

### 🌟 Formål

At opsætte et flow i Node-RED, der automatisk tjekker om din måling er udenfor de grænser, du har valgt – og udløser en alarm/advarsel hvis det sker.

---

### 📚 Baggrund

Automatisk overvågning af målinger er vigtigt for at opdage fejl hurtigt. Med Node-RED kan du bygge et flow, der sammenligner måleværdier med dine grænser og reagerer, hvis noget er unormalt.

---

### 📝 Trin-for-trin

1. **Start Node-RED:**  
   Åbn Node-RED og find det flow, hvor din måling kommer ind.

2. **Tilføj en function-node:**  
   - Opret en function-node, der sammenligner målingen med dine grænser.
   - Eksempel på JavaScript-kode i function-node:
     ```javascript
     // filepath: /workspaces/DLE/Workshop 7/Øvelser/Øvelse 2.md
     // ...existing code...
     let value = msg.payload;
     let lower = 10; // din nedre grænse
     let upper = 30; // din øvre grænse

     if (value < lower) {
         msg.alarm = "Lav værdi!";
         msg.level = "danger";
     } else if (value > upper) {
         msg.alarm = "Høj værdi!";
         msg.level = "danger";
     } else {
         msg.alarm = "OK";
         msg.level = "normal";
     }
     return msg;
     // ...existing code...
     ```

3. **Test dit flow:**  
   - Send forskellige værdier igennem og se om alarmen udløses korrekt.

4. **Send besked videre:**  
   - Forbind function-node til fx en debug-node, dashboard-widget eller næste alarm-flow.

---

### 💡 Eksempel

> Hvis temperaturen er 8°C, skal alarmen vise “Lav værdi!”.  
> Hvis temperaturen er 32°C, skal alarmen vise “Høj værdi!”.  
> Hvis temperaturen er 20°C, skal alarmen vise “OK”.

---

### ✅ Aflevering

- Tag et screenshot af dit flow og din function-node.
- Forklar kort, hvordan din alarm-logik virker.
- Dokumentér i din