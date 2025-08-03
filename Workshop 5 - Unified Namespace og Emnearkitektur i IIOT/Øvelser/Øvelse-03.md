## 📋 Øvelse 3: Lav flere visninger på samme dashboard

### **Formål**

* At samle flere målinger og statusser på ét dashboard, så du får bedre overblik.
* At øve dig i at bruge forskellige widgets på samme side (fx tal, status, graf).

---

### **Baggrund**

I virkelige IIoT-systemer er der ofte mange data, som skal vises samtidigt. Ved at kombinere flere visninger på dit dashboard får du hurtigt overblik over hele systemet.

---

### **Sådan gør du – step by step**

1. **Åbn dit eksisterende dashboard-flow**

   * Brug flowet fra tidligere øvelser.

2. **Tilføj en ny måling**

   * Brug fx en ekstra “inject”-node, “mqtt in”-node eller “modbus read”-node for en ny type data (fx tryk, fugt, strøm).

3. **Tilføj ekstra widgets til dashboardet**

   * Træk fx endnu en “ui\_gauge”, “ui\_chart”, “ui\_text” eller “ui\_led” ind på flowet.
   * Konfigurer widgets med passende labels og enheder (fx “Tryk \[bar]”, “Fugt \[%]”, “Alarmstatus”).

4. **Forbind den nye datakilde til sin widget**

   * Hver widget skal modtage sine egne data.

5. **(Valgfrit) Saml widgets i grupper**

   * I widget-indstillinger kan du lave “groups” og “tabs”, så du kan samle fx målinger i én gruppe og alarmer i en anden.

6. **Deploy flowet**

   * Klik “Deploy”.

7. **Se dit dashboard**

   * Gå til dashboardet i browseren.
   * Du kan nu se flere data og statusser på samme side – og de opdateres live!

---

### **Krav til øvelsen**

* Dashboardet skal vise mindst to forskellige målinger/statusser på samme side.
* Hver visning skal opdatere, når data ændrer sig.

---

### **Når du er færdig**

* Nu har du bygget et rigtigt mini-dashboard – flere målinger og status samlet ét sted!
* Gå videre til næste øvelse, hvor du tilføjer en alarm eller advarsel.
