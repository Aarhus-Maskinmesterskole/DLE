## 📅 Workshop 2: Datasikkerhed & Fejlhåndtering i IIoT

### 👋 Velkommen til Workshop 2!

I denne workshop arbejder vi målrettet med **sanity-checks, plausibility tests, watchdog-flows og korrekt tidsstempling** af IIoT-data. Fokus er på at gøre data **robuste, sporbare og troværdige**, og at opdage fejl hurtigt.

---

### 🌟 Formål

* Implementere sanity-checks og plausibility tests på indkommende IIoT-data
* Opsætte watchdog-overvågning til at fange tabte eller “døde” datastrømme
* Tilsikre, at alle data har et korrekt og ensartet timestamp
* Skelne mellem forskellige typer fejl og visualisere dem tydeligt

---

### 📊 Struktur for Workshop 2

| Øvelse | Fokus                                                     |
| ------ | --------------------------------------------------------- |
| 1      | Tilføj timestamp og metadata til alle indkommende data    |
| 2      | Implementér sanity-check og plausibility test             |
| 3      | Opsæt watchdog på datastrøm (tabt forbindelse/datahuller) |
| 4      | Visualisér fejl og status på dashboard                    |

---

### 📕 Forventede leverancer

* Node-RED flow (.json)
* Simpelt dashboard med statusindikatorer (OK, Warning, Error)
* Kort dokumentation (skriftligt eller som video/demo)

---

### 📚 Krav til løsning

* Alle data skal forsynes med timestamp
* Sanity-checks og plausibility tests skal kunne redigeres uden at deploye flow
* Watchdog skal kunne detektere og indikere tab af datastrøm
* Dashboard skal tydeligt vise status for alle flows

---

### 👩‍💻 Kompetencer du opbygger

* Validering og overvågning af IIoT-data i realtid
* Håndtering af fejl og mangler i datastrømme
* Visualisering af systemstatus og fejl
* Refleksion over datakvalitet og robusthed

---

### 🔄 Afslutning

Workshoppen afsluttes med en fælles opsamling, hvor vi diskuterer de implementerede sanity-checks, fejldetektering og hvordan timestamp bruges til at sikre datakvalitet.
