## 📋 Øvelse 3: Demonstrér afluring af data med HTTP

### **Formål**

* At vise, at data sendt via HTTP let kan læses af andre på netværket.
* At forstå risikoen ved at sende data ukrypteret.

---

### **Baggrund**

Når du bruger HTTP, sendes data i “klartekst”. Det betyder, at alle på samme netværk kan se, hvad du sender – hvis de bruger det rigtige værktøj. Det gælder både beskeder fra sensorer, brugernavne, adgangskoder og alt andet, du sender med HTTP.

---

### **Sådan gør du – step by step**

1. **Sørg for at din HTTP-service fra øvelse 2 virker**

   * Du skal kunne sende og modtage beskeder på dit HTTP-endpoint.

2. **Tal med underviseren**

   * I denne øvelse viser underviseren typisk, hvordan beskeder kan aflures (fx med netværksværktøjet Wireshark, tcpdump eller via live-demo).
   * *Du skal ikke selv installere ekstra programmer, men bare følge med!*

3. **Se eksempler på afluret data**

   * Underviseren viser, hvordan din (eller en andens) HTTP-besked dukker op i klartekst i netværksværktøjet.
   * Bemærk, at både tekst, tal og evt. adgangskoder/brugernavne kan læses!

4. **Diskutér, hvad det betyder**

   * Hvem på netværket kan aflure dine data?
   * Hvad kunne der ske, hvis nogen læste/kopierede/ændrede dine beskeder?

5. **(Valgfrit) Find en side i browseren der bruger HTTP, og se browserens advarsel**

   * Prøv fx at skrive `http://eksempel.dk` i stedet for `https://…`.

---

### **Krav til øvelsen**

* Du skal kunne forklare, hvorfor HTTP ikke er sikkert.
* Du skal kunne give mindst ét eksempel på data, du ikke ville sende ukrypteret.

---

### **Når du er færdig**

* Du forstår nu risikoen ved HTTP – og er klar til at prøve den sikrede version med HTTPS!
