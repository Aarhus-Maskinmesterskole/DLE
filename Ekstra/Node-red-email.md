# 📧 Node-RED: Send e-mail notifikationer

Denne guide viser, hvordan du konfigurerer Node-RED til at sende e-mails, f.eks. ved sensorudløsning eller som regelmæssige statusopdateringer.

---

## 🧰 Forudsætninger

* Node-RED skal være installeret (f.eks. på en Raspberry Pi eller lokal PC).
* En e-mailkonto (f.eks. Gmail) til afsendelse.
* En modtager-e-mailadresse (kan være den samme eller en anden).

---

## 📦 Trin 1: Installer e-mail-noder i Node-RED

1. Åbn Node-RED.
2. Gå til **Menu > Manage Palette > Install**.
3. Søg efter `node-red-node-email` og installer den.

Dette tilføjer e-mail-noder til din værktøjspalette.

---

## 📧 Trin 2: Opret og konfigurer en afsenderkonto

### Brug af Gmail (anbefalet)

1. Opret en ny Gmail-konto (anbefales ikke at bruge din primære konto).
2. Aktivér **2-trinsbekræftelse** på kontoen.
3. Gå til [Google App Passwords](https://myaccount.google.com/security) og opret en ny adgangskode:

   * Vælg "Mail" som app.
   * Vælg "Andet" som enhed og navngiv den f.eks. "Node-RED".
   * Klik på "Generer" og kopier den 16-cifrede adgangskode.

### SMTP-indstillinger for Gmail

* **SMTP-server**: `smtp.gmail.com`
* **Port**: `465` (SSL) eller `587` (TLS)
* **Brugernavn**: Din fulde Gmail-adresse
* **Adgangskode**: Den genererede app-adgangskode

---

## 🔧 Trin 3: Opret dit e-mail-flow i Node-RED

1. Træk en **Inject**-node og en **E-mail**-node ind i dit flow.
2. Forbind dem sammen.
3. Dobbeltklik på **Inject**-noden og konfigurer:

   * **Payload**: Den ønskede e-mailtekst (som en streng).
   * **Topic**: Emnet for e-mailen (som en streng).
4. Dobbeltklik på **E-mail**-noden og konfigurer:

   * **To**: Modtagerens e-mailadresse.
   * **Server**: `smtp.gmail.com`
   * **Port**: `465` eller `587`
   * **Brugernavn**: Din Gmail-adresse.
   * **Adgangskode**: Den genererede app-adgangskode.
   * **TLS**: Aktiveret (hvis tilgængelig).

---

## ▶️ Trin 4: Test flowet

1. Klik på **Deploy** for at gemme og aktivere flowet.
2. Klik på knappen ved siden af **Inject**-noden for at sende en test-e-mail.
3. Tjek modtagerens indbakke for at bekræfte modtagelsen.

---

## ✅ Klar til brug

Du kan nu integrere dette flow med sensorer, tidsplaner eller andre hændelser i dit automatiseringssystem. For eksempel:

* Send en e-mail, når en temperatursensor overskrider en tærskel.
* Modtag daglige statusrapporter.
* Få besked, når bevægelse registreres.

---

## 📘 Yderligere ressourcer

* [Node-RED: Send Email Notifications](https://randomnerdtutorials.com/node-red-send-email-notifications/)
* [Node-RED: Send Messages to WhatsApp](https://randomnerdtutorials.com/node-red-send-messages-whatsapp/)
* [SMART HOME with Raspberry Pi, ESP32, and ESP8266](https://randomnerdtutorials.com/smart-home-ebook/)

---

