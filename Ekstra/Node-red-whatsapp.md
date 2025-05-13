# 📲 Node-RED: Send WhatsApp-beskeder

Denne vejledning viser, hvordan du konfigurerer Node-RED til at sende WhatsApp-beskeder, f.eks. ved sensorudløsning eller som regelmæssige statusopdateringer.

---

## 🧰 Forudsætninger

* Node-RED installeret (f.eks. på en Raspberry Pi eller lokal PC).
* En WhatsApp-konto.
* En CallMeBot API-nøgle.

---

## 🔑 Trin 1: Få en CallMeBot API-nøgle

1. Tilføj telefonnummeret `+34 621 331 709` til dine kontakter (navngiv det f.eks. "CallMeBot").
2. Send beskeden: `I allow callmebot to send me messages` til den nye kontakt via WhatsApp.
3. Vent på svar: "API Activated for your phone number. Your APIKEY is XXXXXX".

> **Bemærk:** Hvis du ikke modtager en API-nøgle inden for 2 minutter, prøv igen efter 24 timer.

---

## 📦 Trin 2: Installer WhatsApp-noder i Node-RED

1. Åbn Node-RED.
2. Gå til **Menu > Manage Palette > Install**.
3. Søg efter `node-red-contrib-whatsapp-cmb` og installer den.

Dette tilføjer WhatsApp-noder til din værktøjspalette.

---

## 🔧 Trin 3: Opret dit WhatsApp-flow i Node-RED

1. Træk en **Inject**-node, en **Send Message WhatsApp**-node og en **Debug**-node ind i dit flow.
2. Forbind dem sammen.
3. Dobbeltklik på **Inject**-noden og konfigurer:

   * **Payload**: Den ønskede beskedtekst (som en streng).
4. Dobbeltklik på **Send Message WhatsApp**-noden og konfigurer:

   * Klik på blyantikonet for at tilføje en ny WhatsApp-konto.
   * Indtast dit telefonnummer (i internationalt format) og den API-nøgle, du modtog fra CallMeBot.
   * Klik på "Update" og derefter "Done".

---

## ▶️ Trin 4: Test flowet

1. Klik på **Deploy** for at gemme og aktivere flowet.
2. Klik på knappen ved siden af **Inject**-noden for at sende en testbesked.
3. Tjek din WhatsApp for at bekræfte modtagelsen.

---

## ✅ Klar til brug

Du kan nu integrere dette flow med sensorer, tidsplaner eller andre hændelser i dit automatiseringssystem. For eksempel:

* Send en WhatsApp-besked, når en temperatursensor overskrider en tærskel.
* Modtag daglige statusrapporter.
* Få besked, når bevægelse registreres.

---

## 📘 Yderligere ressourcer

* [Node-RED: Send Messages to WhatsApp](https://randomnerdtutorials.com/node-red-send-messages-whatsapp/)
* [CallMeBot WhatsApp API](https://www.callmebot.com/blog/whatsapp-api/)
* [SMART HOME with Raspberry Pi, ESP32, and ESP8266](https://randomnerdtutorials.com/smart-home-ebook/)

---
