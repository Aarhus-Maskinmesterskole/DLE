# 🧪 Øvelse 2: Kør Python-script og start GUI

## 🎯 Formål
I denne øvelse skal du arbejde med det færdige Python-script `mitm.py`, som er udviklet til at simulere et Man-in-the-Middle (MITM) angreb i et kontrolleret og sikkert IIOT-miljø. Scriptet åbner en simpel grafisk brugerflade (GUI), hvor du med få klik kan observere, hvordan uautoriseret adgang til et netværk kan give fuld indsigt i beskeder sendt mellem IIOT-enheder. Øvelsen viser, hvor let det er at få adgang til følsomme data, hvis ikke trafikken er beskyttet med moderne sikkerhedsprotokoller som TLS. Det er vigtigt at forstå den tekniske proces bag aflytning, for at kunne vurdere hvor kritisk det kan være i et rigtigt system.

---

## 🛠️ Forudsætninger
For at kunne gennemføre denne øvelse, skal følgende være på plads:

- Du har en computer med Python 3 installeret.
- Du har installeret følgende Python-biblioteker: `scapy`, `psutil`, og `tkinter`.
- Du har adgang til det udleverede Python-script kaldet `mitm.py`.
- Du er forbundet til et netværk, hvor du både kan få fat i IP-adressen på din gateway (router) og på den maskine du vil simulere som offer (ofte din egen maskine).
- Du har mulighed for at køre terminalkommandoer som `sudo`.

---

## 🧭 Trin-for-trin vejledning

1. **Start scriptet**
   - Åbn en terminal og skriv: `sudo python3 mitm.py`
   - Scriptet åbner en grafisk brugerflade (GUI), hvor du kan indtaste de oplysninger, du skal bruge for at simulere angrebet.

2. **Indtast IP-adresser**
   - "Target IP" er den IP-adresse du ønsker at aflytte. Det kan f.eks. være din egen maskine eller en virtuel maskine på samme netværk.
   - "Gateway IP" er den IP-adresse, som din maskine bruger som adgang til netværket – oftest din router (typisk `192.168.1.1` eller lignende).

3. **Vælg netværksinterface**
   - I drop-down menuen skal du vælge det netværksinterface, du bruger. Hvis du er forbundet med kabel, hedder det typisk `eth0`, `enp3s0` eller lignende. Hvis du bruger WiFi, hedder det typisk `wlan0`, `wlp2s0` eller lignende.

4. **Start angrebet**
   - Tryk på knappen **“Start Attack”**. Scriptet vil nu begynde at opsnappe beskeder der går gennem det valgte netværksinterface og matche kriterierne (typisk MQTT-trafik på port 1883).
   - I GUI'en vil du kunne se i realtid hvilke beskeder der bliver opsnappet. Disse beskeder vises som tekst og kan typisk indeholde payloads, temperaturmålinger, statusdata m.m.

5. **Stop angrebet**
   - Når du har fået nok data til at analysere, trykker du på **“Stop Attack”**. Det stopper både aflytningen og ARP-spoofing mellem gateway og target.

---

## 📋 Hvad skal du observere?
Når scriptet kører og opsnapper beskeder, skal du lægge mærke til følgende:

- Hvilke typer beskeder bliver opsnappet og vist i tekstfeltet?
- Indeholder de informationer som sensordata, emner (topics), brugernavne eller andre følsomme data?
- Er data sendt i klartekst, eller kan du ikke læse det?
- Hvad ville en angriber kunne gøre med den information, du ser i dit vindue?

---

## 🧠 Refleksion (til næste øvelse)
Skriv gerne nogle hurtige stikord til dig selv:
- Var der noget, der overraskede dig ved det, du så i vinduet?
- Virkede det svært eller let at komme i gang med angrebet?
- Forestil dig, at du er IT-ansvarlig i en virksomhed – hvordan ville du opdage, at dette foregik?

---

> **Bemærk:** Du skal ikke aflevere noget i denne øvelse. Det er en forberedelse til næste øvelse, hvor vi arbejder med manipulation af datastrømmen.

👉 Gå videre til Øvelse 3, når du har gennemført ovenstående og noteret dine observationer.

