---

## 📋 Opgave 4: Send alarmbesked til bruger (valgfrit) – Uddybning

### 🌟 Formål

At lære at sende en besked til en bruger, når en alarm udløses – fx via email, Telegram eller anden beskedtjeneste.

---

### 📚 Baggrund

Automatisk besked ved alarm gør det muligt at reagere hurtigt, selv hvis du ikke sidder ved dashboardet. Det er nyttigt både i industrien og hjemme.

---

### 📝 Trin-for-trin

1. **Vælg beskedtype:**  
   - Bestem om du vil sende email, Telegram, SMS eller anden besked.

2. **Tilføj besked-node i Node-RED:**  
   - Find fx “email”- eller “telegram”-node og træk den ind i dit flow.

3. **Forbind alarmen til besked-node:**  
   - Forbind output fra din alarm-function-node til besked-noden.

4. **Formatér beskeden:**  
   - Skriv en klar besked, fx:  
     ```
     Alarm! Temperatur udenfor grænse: 32°C (Høj værdi!) kl. 2025-08-05T12:34:56Z
     ```

5. **Konfigurer besked-node:**  
   - Indtast modtager, login-oplysninger og evt. API-nøgle (følg Node-RED dokumentation).

6. **Test beskeden:**  
   - Udløs en alarm og tjek, at beskeden bliver sendt og modtaget.

---

### 💡 Eksempel

> Når temperaturen er 8°C, skal der sendes en email med teksten:  
> “Alarm! Temperatur for lav: 8°C kl. 2025-08-05T12:34:56Z”

---

### ✅ Aflevering

- Vis, at du har modtaget mindst én alarmbesked.
- Forklar kort, hvordan dit flow sender beskeder.
- Dokumentér i din