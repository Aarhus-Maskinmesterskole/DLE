## **Øvelse 5: Udforsk Retain-flag, QoS og Last Will i MQTT**

### **Formål**

At få praktisk erfaring med centrale MQTT-funktioner: **Retain-flag, Quality of Service (QoS) og Last Will & Testament** – så du forstår, hvordan de påvirker dataaflevering og systemets driftssikkerhed.

---

### **Sådan gør du:**

#### **A. Retain-flag**

1. **Træk en “MQTT out”-node og en “MQTT in”-node ind**

   * Brug fx topic: `retain/test`.

2. **Indstil “Retain” på MQTT out**

   * I “MQTT out”-node, sæt flueben ved **Retain**.

3. **Send en besked**

   * Brug en inject-node til at sende beskeden.

4. **Prøv at abonnere som ny subscriber**

   * Tilføj en ny “MQTT in”-node på samme topic.
   * Tjek om den modtager den senest sendte besked med det samme.

---

#### **B. QoS (Quality of Service)**

1. **Indstil QoS på dine MQTT-noder**

   * Vælg QoS 0, 1 eller 2 i både “MQTT in” og “MQTT out”.

2. **Send flere beskeder**

   * Skift QoS-niveau og observer, hvordan det påvirker leveringssikkerhed (fx tab af forbindelse, dubletter mv.).

---

#### **C. Last Will & Testament**

1. **Konfigurer Last Will i broker-indstillinger**

   * I MQTT broker-opsætningen (“edit mqtt-broker”), indtast:

     * Last Will Topic (fx `lastwill/dinbrugernavn`)
     * Last Will Message (fx “Offline”)

2. **Opret en “MQTT in”-node**

   * Abonnér på Last Will-topic’et.

3. **Simuler en uventet disconnect**

   * Luk Node-RED, eller afbryd forbindelsen pludseligt.

4. **Tjek om last will-beskeden modtages**

   * Se i debug-panelet, om din medstuderende får beskeden.

---

### **Når du er klar:**

Gå videre til næste øvelse, hvor du prøver at forbinde via TLS/kryptering – eller spørg om hjælp, hvis noget ikke virker!
