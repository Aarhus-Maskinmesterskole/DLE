## 📊 Workshop 4: Samarbejd og del data mellem systemer


### 🌟 **Formål**

* At opleve, hvordan man **deler og modtager data** på tværs af flere brugere eller systemer ved hjælp af MQTT.
* At forstå, hvordan data kan flyde mellem forskellige flows, og hvad det betyder for åbenhed, samarbejde og datasikkerhed.
* At kunne diskutere, hvornår det er smart at dele data – og hvornår man skal være forsigtig.

---

### 👩‍💻 **Kompetencer du opbygger**

Efter workshoppen kan du:

* **Sende og modtage beskeder** via fælles MQTT-topic i Node-RED.
* **Bygge flows, der kommunikerer med andres flows** (fx chat, fælles måling, opslagstavle).
* **Visualisere data fra flere kilder** på et dashboard.
* **Reflektere over datasikkerhed** – hvem kan læse/skrive på et åbent topic?
* **Samarbejde om data** og forklare, hvad åbne og lukkede datastrømme betyder i praksis.


### 📋 Øvelse 1: Send data til et fælles topic

**Formål:**

* At sende en besked til et fælles MQTT-topic, som andre kan modtage.
* At forstå, at data på et åbent topic kan læses af alle med adgang.

**Krav:**

* Du skal kunne sende fx temperatur, navn eller besked til et aftalt topic (fx `klasse/test`).

---

### 📋 Øvelse 2: Modtag data fra en medstuderende

**Formål:**

* At modtage beskeder fra andre via det fælles topic.
* At se, hvordan flere flows kan “lytte” på det samme topic.

**Krav:**

* Dit flow skal kunne vise beskeder fra andre på samme topic i debug eller dashboard.

---

### 📋 Øvelse 3: Chat med MQTT

**Formål:**

* At prøve en simpel “chat”, hvor I skriver beskeder til hinanden via MQTT.

**Krav:**

* Du skal kunne skrive en besked, som en medstuderende ser i deres Node-RED (og omvendt).

---

### 📋 Øvelse 4: Lav et lille “fælles dashboard”

**Formål:**

* At vise beskeder fra flere brugere på et fælles dashboard (fx liste eller tekstfelt).

**Krav:**

* Dit dashboard skal opdatere sig, når der kommer nye beskeder fra andre.

---

### 📋 Øvelse 5: Refleksion og sikkerhed

**Formål:**

* At tænke over, hvem der kan læse data på et åbent topic.
* At forklare, hvornår det er smart at dele data – og hvornår det ikke er!

**Krav:**

* Skriv eller fortæl kort, hvilke data du ville dele åbent, og hvilke du helst ville beskytte.

---

### 📢 Husk:

* **Et åbent MQTT-topic er som en fælles opslagstavle:** Alle med adgang kan læse og skrive!
* Det er smart til fx beskeder, chat eller fælles sensordata – men ikke til følsomme oplysninger.
* Spørg underviseren, hvis du er i tvivl om brugen af topic eller deling af data.
