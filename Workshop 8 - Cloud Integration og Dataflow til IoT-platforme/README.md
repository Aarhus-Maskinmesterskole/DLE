# ☁️ Workshop 8: Cloud Integration og Dataflow til IoT-platforme

## 📚 Introduktion

I denne workshop lærer du at forbinde dit IIOT-setup til en cloud-platform, så du kan overføre, visualisere og analysere data centralt – uanset hvor din hardware befinder sig. Vi fokuserer på sikker integration med cloud-tjenester som **Azure IoT Hub**, **AWS IoT Core** og **Google Cloud IoT**. Målet er, at du forstår hele vejen fra en lokal sensor til skyen – og hvordan man sikrer datastrømmen undervejs.

Cloud integration muliggør:

* Central overvågning og beslutningsstøtte
* Skalerbarhed og tværorganisatorisk adgang
* Backup og analyse af historiske data
* Integration med dashboards, AI og forretningssystemer

---

## 🎯 Formål

* At forstå, hvordan IIOT-enheder kommunikerer med cloud-platforme
* At opsætte en MQTT-baseret forbindelse til mindst én cloud-tjeneste
* At sikre overførslen vha. **TLS**, **adgangsnøgler** og **enhedsidentitet**
* At designe dataflows, der overfører relevante datapunkter uden støj
* At analysere cloud-modtagne data og vurdere forbindelsens stabilitet og sikkerhed

---

## 🧠 Kompetencer

Når workshoppen er gennemført, forventes det, at du:

* Kan forbinde Node-RED til en ekstern cloud MQTT-broker (Azure, AWS, Google, etc.)
* Kan formatere payloads, så de matcher cloud-platformens forventede struktur
* Forstår sikkerhedslagene i cloud-forbindelser (TLS, token, device ID, etc.)
* Kan overvåge forbindelsen og identificere potentielle problemer (disconnect, throttling, etc.)
* Kan forklare forskellen på edge-lokationer og cloud-lag

---

## 🧩 Øvelser (eksempler)

| Øvelse | Titel                                                |
| ------ | ---------------------------------------------------- |
| 1      | Opsæt forbindelse til cloud via MQTT med TLS         |
| 2      | Formatér payload korrekt til cloud-platformens skema |
| 3      | Anvend cloud-Dashboard til live visualisering        |
| 4      | Log fejl og forbindelsesstatus lokalt ved disconnect |
| 5      | Begræns data og send kun relevante værdier           |
| 6      | Dokumentér din integration og cloud-arkitektur       |

---

## 📦 Aflevering

* Flow (.json) der viser cloud-integration
* Screenshot af cloud-dashboard, hvor dine data vises
* Kort dokumentation (markdown eller slides) med:

  * Beskrivelse af sikkerhedslag
  * Struktur af dine topics/payloads
  * Brugte credentials (maskerede) og protokolvalg
* Refleksion over forskelle mellem lokal og cloud databehandling

---

## 📢 Husk

Cloud er ikke en magisk løsning – det er en **udvidelse** af din arkitektur. For at få det fulde udbytte skal du tænke i **struktur, sikkerhed og formål**: Hvilke data skal sendes? Hvor ofte? Hvem har adgang? Hvad gør du ved disconnects? Hvad sker der, når cloud-tjenesten opdateres?

En god cloud-integration giver både overblik, fleksibilitet og professionel skalerbarhed. Nu bygger vi bro mellem lokal edge og global cloud.
