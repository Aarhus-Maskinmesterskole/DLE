# 🧪 Øvelse 4: Implementér TLS og adgangskontrol

## 🎯 Formål
I denne øvelse skal du sikre dit MQTT-setup mod Man-in-the-Middle (MITM)-angreb, som du testede i de forrige øvelser. Du skal implementere **TLS-kryptering** og **adgangskontrol med brugernavn og adgangskode** på både broker og klient. Formålet er, at du oplever den tydelige forskel mellem ubeskyttet og beskyttet datakommunikation, og forstår, hvordan disse mekanismer forhindrer både afluring og manipulation.

Denne øvelse er central i Workshop 3, fordi det er her du **går fra at simulere angrebet til at stoppe det**. Du ser med egne øjne, hvordan korrekt sikkerhedsopsætning effektivt blokerer forsøg på datatyveri.

---

## 🛠️ Forudsætninger
- Du har opsnappet beskeder via MITM (fx med `mitm.py`).
- Du har en MQTT-broker til rådighed (Mosquitto anbefales).
- Du har en MQTT-klient (Node-RED, MQTT Explorer eller andet).
- Du kan ændre konfiguration og genstarte din broker.

---

## ⚙️ Trin-for-trin

### 1. **Opsæt TLS på din broker**
- Brug enten udleverede certifikater eller generér selv med OpenSSL:
  - CA-certifikat: `ca.crt`
  - Server-certifikat: `server.crt`
  - Server-nøgle: `server.key`
- Rediger `mosquitto.conf` og tilføj:
  ```
  listener 8883
  cafile ca.crt
  certfile server.crt
  keyfile server.key
  require_certificate false
  allow_anonymous false
  password_file passwords.txt
  ```
- Genstart brokeren og tjek at den kører på port 8883 med TLS.

### 2. **Tilføj brugere og adgangskontrol**
- Opret bruger med Mosquittos terminalværktøj:
  ```bash
  mosquitto_passwd -c passwords.txt student
  ```
- Test, at du **ikke kan forbinde** uden brugernavn eller med forkert adgangskode.

### 3. **Tilpas klienten til at forbinde via TLS**
- I Node-RED:
  - Tilføj MQTT-broker node og sæt URL til `mqtts://<din-IP>:8883`
  - Angiv brugernavn og adgangskode
  - Under TLS: upload `ca.crt` som CA-certifikat
- I MQTT Explorer:
  - Indstil connection til TLS og brug certifikat + login

### 4. **Gentag MITM-angrebet**
- Kør `mitm.py` og forsøg at opsnappe trafik igen.
- Observer:
  - Får du stadig adgang til payloads?
  - Ser du kun binære/krypterede data?
  - Får du afviste forbindelser?

---

## 🔍 Observationer
- Notér hvordan MITM-scriptet opfører sig nu:
  - Bliver beskeder afvist?
  - Er data ulæselige?
- Dokumentér hvad der ændrer sig før/efter TLS.

---

## 📋 Refleksion
- Hvordan forhindrer TLS aflytning og manipulation?
- Hvilken rolle spiller adgangskontrol i at beskytte systemet?
- Hvordan kan du sikre korrekt vedligeholdelse af certifikater?
- Hvordan oplevede du forskellen i datatilgængelighed som angriber?

> 🎓 Din dokumentation af før/efter-effekten bliver central i Øvelse 5 og 6.

👉 Gå videre til Øvelse 5, hvor du begynder at logge dine observationer og opbygge din tekniske dokumentation.

