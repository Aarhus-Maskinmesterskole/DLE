# 🧼 Node-RED: Send SOAP-anmodninger

Denne vejledning viser, hvordan du konfigurerer Node-RED til at sende SOAP-anmodninger til webtjenester ved hjælp af `node-red-contrib-soap`.

---

## 🧰 Forudsætninger

* Node-RED installeret (f.eks. på en Raspberry Pi eller lokal PC).
* En SOAP-webtjeneste med en tilgængelig WSDL (Web Services Description Language).
* Kendskab til den metode og de parametre, du ønsker at kalde.

---

## 📦 Trin 1: Installer `node-red-contrib-soap`

1. Åbn Node-RED.
2. Gå til **Menu > Manage Palette > Install**.
3. Søg efter `node-red-contrib-soap` og installer den.

Dette tilføjer SOAP-noder til din værktøjspalette.

---

## 🔧 Trin 2: Konfigurer SOAP-anmodningen

1. Træk en **Inject**-node, en **SOAP Request**-node og en **Debug**-node ind i dit flow.
2. Forbind dem sammen: Inject → SOAP Request → Debug.
3. Dobbeltklik på **SOAP Request**-noden og konfigurer:

   * Klik på blyantikonet ved siden af **WSDL** for at tilføje en ny konfiguration.
   * Indtast WSDL-URL'en for den ønskede webtjeneste.
   * Vælg autentificeringsmetode, hvis nødvendigt (f.eks. Basic Auth).
   * Klik på "Add" for at gemme konfigurationen.
   * Indtast den metode, du ønsker at kalde, i feltet **Method** (f.eks. `GetGeoIP`).

---

## 📝 Trin 3: Tilføj parametre til anmodningen

1. Dobbeltklik på **Inject**-noden og konfigurer:

   * **Payload**: Vælg "JSON" og indtast de nødvendige parametre som et JSON-objekt. For eksempel:

     ```json
     {
       "IPAddress": "139.130.4.5"
     }
     ```
2. Klik på "Done" for at gemme konfigurationen.

---

## ▶️ Trin 4: Test flowet

1. Klik på **Deploy** for at gemme og aktivere flowet.
2. Klik på knappen ved siden af **Inject**-noden for at sende en testanmodning.
3. Tjek **Debug**-panelet for at se svaret fra webtjenesten.

---

## ✅ Klar til brug

Du kan nu integrere dette flow med sensorer, tidsplaner eller andre hændelser i dit automatiseringssystem. For eksempel:

* Send en SOAP-anmodning, når en temperatursensor overskrider en tærskel.
* Modtag oplysninger fra en ekstern webtjeneste baseret på en hændelse.
* Integrer med virksomhedens systemer, der bruger SOAP-baserede API'er.

---

## 📘 Yderligere ressourcer

* [node-red-contrib-soap på Node-RED flows](https://flows.nodered.org/node/node-red-contrib-soap)
* [node-red-contrib-soap GitHub-repository](https://github.com/chameleonbr/node-red-contrib-soap)

---
