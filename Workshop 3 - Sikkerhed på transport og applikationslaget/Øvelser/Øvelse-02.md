## 📋 Øvelse 2: Byg en simpel HTTP-service i Node-RED

### **Formål**

* At oprette et simpelt HTTP-endpoint i Node-RED, hvor du kan modtage og sende data via HTTP.
* At prøve at sende og modtage beskeder “åbent” – som i den rigtige verden.

---

### **Baggrund**

I Node-RED kan du nemt oprette en webservice, som modtager data fra fx en browser eller Postman. Denne service bruger HTTP, så data sendes uden sikkerhed – alle på netværket kan i princippet læse med.

---

### **Sådan gør du – step by step**

1. **Åbn Node-RED**

   * Log ind på din Node-RED, hvis du ikke allerede er klar.

2. **Træk en “http in”-node ind på flowet**

   * Find “http in” i paletten (venstre side) og træk den ind.

3. **Konfigurer din HTTP-endpoint**

   * Dobbeltklik på “http in”-noden.
   * Sæt en metode (fx “POST” eller “GET”).
   * Skriv en URL-sti, fx `/test`.

4. **Træk en “http response”-node ind**

   * Forbind “http in” til “http response”.

5. **(Valgfrit) Tilføj en “debug”-node**

   * Forbind “http in” (eller evt. en function-node mellem dem) til en debug-node, så du kan se de data, du modtager.

6. **Deploy flowet**

   * Klik “Deploy” oppe til højre.

7. **Test din HTTP-service**

   * Brug din browser, Postman, eller en “http request”-node i Node-RED til at sende en forespørgsel til din server:

     * Fx: `http://[din-ip-adresse]:1880/test`
   * Hvis du bruger “POST”, kan du sende et lille stykke tekst eller tal med.

8. **Se respons og debug**

   * Tjek at din besked vises i debug-vinduet og/eller at du får svar fra din HTTP-service.

---

### **Krav til øvelsen**

* Du skal kunne modtage en besked på dit HTTP-endpoint.
* Du skal kunne sende et svar tilbage (selv bare et “OK”).

---

### **Når du er færdig**

* Prøv at sende flere typer beskeder – og tænk over, at alt sendes åbent!
* Gå videre til næste øvelse, hvor du ser, hvordan andre nemt kan aflure din data.
