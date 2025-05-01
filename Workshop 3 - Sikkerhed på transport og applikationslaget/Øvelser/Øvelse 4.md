# 🧪 Øvelse 4: Beskyt forbindelsen med TLS og adgangskontrol

## 🎯 Formål
I denne øvelse bygger vi videre på din praktiske erfaring med Man-in-the-Middle (MITM)-angreb fra de tidligere øvelser. Du har nu set, hvordan MQTT-beskeder kan opsnappes og endda manipuleres, hvis forbindelsen er ubeskyttet. Nu skal du tage det næste skridt: at implementere og afprøve beskyttelsesforanstaltninger, som anvendes i industrien for at sikre datastrømme.

Målet med øvelsen er, at du hands-on får forståelse for, hvordan TLS (Transport Layer Security) og adgangskontrol (med brugernavn og adgangskode) virker i praksis. Du vil tydeligt kunne se forskellen på ubeskyttet og beskyttet MQTT-kommunikation – både ved at analysere trafikken med dit MITM-script og ved at konfigurere dine systemer korrekt. Når øvelsen er gennemført, har du ikke blot forståelse for hvorfor man bruger sikkerhed, men også hvordan det gøres.

---

## 🛠️ Forudsætninger
For at du kan gennemføre denne øvelse effektivt, skal du have:

- Gennemført Øvelse 2 og 3, hvor du har brugt `mitm.py` til at aflytte og manipulere MQTT-trafik.
- En MQTT-broker installeret lokalt eller i netværket, der understøtter TLS – fx Mosquitto.
- Adgang til en MQTT-klient som Node-RED, MQTT Explorer, eller et andet værktøj med TLS-understøttelse.
- Adgang til certifikater (enten udleveret i undervisningen eller selv genereret med OpenSSL).
- Grundlæggende forståelse for hvordan MQTT fungerer, og hvordan klient og broker kommunikerer.

---

## ⚙️ Trin-for-trin: Fra ubeskyttet til sikret kommunikation

1. **Opsæt TLS på din broker (fx Mosquitto)**
   - Du skal enten bruge de certifikater du har fået udleveret, eller selv generere dem med OpenSSL. En typisk opsætning kræver:
     - `ca.crt` – Certificate Authority
     - `server.crt` – Brokeren's offentlige certifikat
     - `server.key` – Brokeren's private nøgle
   - Rediger din `mosquitto.conf` så den kun accepterer TLS-krypterede forbindelser:
     ```
     listener 8883
     cafile ca.crt
     certfile server.crt
     keyfile server.key
     require_certificate false
     allow_anonymous false
     password_file passwords.txt
     ```
   - Genstart brokeren, og kontroller at den nu kun svarer på port 8883 og kræver login.

2. **Tilføj adgangskontrol**
   - Brug Mosquittos indbyggede værktøj til at oprette brugere:
     ```bash
     mosquitto_passwd -c passwords.txt student
     ```
   - Test forbindelser med korrekt og forkert brugernavn/adgangskode for at sikre dig, at adgangsbegrænsningen fungerer.

3. **Opsæt klienten med TLS og login**
   - I Node-RED skal du bruge en `mqtt-broker` node og konfigurere:
     - Host: `mqtts://<din-IP>:8883`
     - TLS-config: indlæs CA-certifikatet
     - Brugernavn og adgangskode
   - I MQTT Explorer vælger du TLS og uploader certifikaterne, og indtaster de samme login-oplysninger.

4. **Genkør dit MITM-script (mitm.py)**
   - Start MITM-scriptet som før og prøv at aflytte trafikken mellem klient og broker.
   - Du vil opdage at beskederne ikke længere kan læses – de er nu krypteret.
   - Hvis du forsøger at manipulere beskeder, vil de ikke have nogen effekt.

---

## 🔍 Observationer og testresultater
Under og efter opsætning, læg mærke til:

- Hvordan adfærden i terminalen/GUI ændrer sig.
- Om du kan aflæse beskeder i klartekst som før.
- Hvordan brokeren håndterer forkerte loginforsøg.
- Om du kan se om forbindelsen er krypteret (f.eks. via TLS-håndtryk i log eller GUI).

Notér dine observationer, da du skal bruge dem til dokumentation og refleksion.

---

## 📋 Refleksion og evaluering
Besvar følgende spørgsmål i din portfolio, og inddrag dine observationer:

- Hvordan forhindrede TLS, at du kunne aflæse data via MITM?
- Hvordan sikrer adgangskontrol mod uautoriseret adgang til systemet?
- Hvilke styrker og svagheder er der ved at bruge selv-signed certifikater i undervisningsmiljøet?
- Hvor og hvordan ser du TLS og login anvendt i virkelige industrielle miljøer?

Skriv også gerne dine egne erfaringer eller overraskelser du havde under opsætningen.

---

> 🎓 Aflever dokumentation og refleksion i din gruppeportfolio. Du skal vise, hvad du gjorde før og efter, og forklare forskellen det gjorde for datasikkerheden.

👉 Når du er færdig, går du videre til Øvelse 5, hvor vi arbejder med logging, sporbarhed og dokumentation af hændelser.

