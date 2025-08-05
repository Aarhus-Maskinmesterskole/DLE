## 📋 Øvelse 3: Chat med MQTT

### **Formål**

* At opleve, hvordan du kan lave en simpel chat med dine medstuderende ved hjælp af MQTT og Node-RED.
* At øve dig i at sende og modtage korte beskeder mellem flere personer på et fælles topic.

---

### **Baggrund**

Fordi alle, der lytter på det samme MQTT-topic, kan sende og modtage beskeder, kan I nemt lave en “chat”, hvor beskeder flyver frem og tilbage – lidt ligesom en gruppechat!

---

### **Sådan gør du – step by step**

1. **Brug dit eksisterende flow**

   * Du skal bruge både en “MQTT in”-node (modtag) og en “MQTT out”-node (send) på samme fælles topic (fx `klasse/chat`).

2. **Tilføj en inject-node til “MQTT out”**

   * Skriv en kort tekst i inject-noden, fx dit navn og en besked (“Hej fra \[navn]!”).

3. **Forbind “MQTT in”-node til debug-node**

   * Så du kan se alle beskeder, der bliver sendt på topic’et – både dine egne og andres.

4. **Deploy flowet**

   * Klik “Deploy”.

5. **Chat med dine medstuderende**

   * Tryk på inject-knappen for at sende en besked.
   * Se alle beskeder (også fra andre) i debug-vinduet.
   * Prøv at skrive forskelligt, fx stille et spørgsmål eller svare på en besked.

---

### **Krav til øvelsen**

* Du skal kunne sende og modtage mindst én besked på chat-topic’et.
* Du skal kunne se beskeder fra flere personer (fx dig selv og mindst én medstuderende).

---

### **Når du er færdig**

* Overvej: Hvordan kan du bruge sådan en chat til samarbejde, alarmer eller statusbeskeder i et “rigtigt” IIoT-system?
* Gå videre til næste øvelse, hvor I laver et fælles dashboard!
