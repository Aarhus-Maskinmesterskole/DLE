# Workshop 1: Introduktion til IIOT Kommunikation i Node-RED

## 🌟 Formål
Workshoppen introducerer de studerende til grundlæggende IIOT-kommunikation og praktisk opsætning af forskellige industrielle protokoller. Fokus er på at forstå kommunikationsarkitektur, konfigurere flere typer IIOT-forbindelser i Node-RED, vurdere deres styrker og svagheder, samt dokumentere arbejdet professionelt.

Målet er, at de studerende ikke kun kan konfigurere systemer, men også vælge passende teknologier ud fra krav til drift, vedligeholdelse og datasikkerhed.

---

## 🔄 Struktur for workshoppen

- Introduktion: IIOT vs IT, Arkitektur og protokoloversigt
- Gennemgang af hver IIOT-protokol: MQTT, Modbus TCP/IP, HTTP/REST, CoAP, OPC UA, AMQP
- Opsætning af kommunikationstyper i Node-RED (praktisk arbejde)
- Optagelse af video: Demonstration af opsætning
- Udarbejdelse af PowerPoint: Fordele/ulemper sammenligning
- Afleveringsinstruktioner og opsamling

---

## 🗂️ Mappe- og Filstruktur (de skal aflevere)

```
Workshop1_IIOT_kommunikation/
├── Video/                    # Videooptagelse af opsætninger
│    └── iiot_protocol_setup_demo.mp4
├── PowerPoint/               # Sammenligning af protokoller
│    └── iiot_protocol_comparison.pptx
├── Node-RED_Flows/            # Eksporterede Node-RED flows
│    ├── mqtt_flow.json
│    ├── modbus_flow.json
│    ├── http_rest_flow.json
│    ├── coap_flow.json
│    ├── opcua_flow.json
│    └── amqp_flow.json
└── Dokumentation/            # Kort tekst om opsætning og erfaringer
     └── opsummering.md
```

---

## 👩‍💻 Kompetencer efter workshoppen

Når workshoppen er gennemført, forventes det, at den studerende:

- Kan beskrive forskellen på centrale IIOT-protokoller.
- Kan opsætte og konfigurere MQTT, Modbus TCP/IP, HTTP/REST, CoAP, OPC UA og AMQP i Node-RED.
- Kan forklare fordele og ulemper ved hver protokol i forhold til drift, vedligeholdelse og datasikkerhed.
- Kan dokumentere teknisk opsætning gennem video og skriftlig PowerPoint-præsentation.
- Kan identificere hvor driftssikkerhed, skalering og sikkerhed spiller en rolle i valg af protokol.

---

## 📅 Hvad skal de aflevere

**Følgende skal afleveres, når de vurderer sig selv færdige med workshoppen:**

1. **Video (MP4)** der viser:
   - Kort forklaring på hver protokol.
   - Live demonstreret opsætning i Node-RED.

2. **PowerPoint-præsentation (PPTX)** der viser:
   - Fordele og ulemper for hver protokol.
   - Samlet vurdering af hvilken protokol der er bedst til driftssikre IIOT-systemer.

3. **Eksporterede Node-RED flows (JSON-filer)** for alle 6 protokoller.

4. **Kort opsummering (Markdown eller PDF)**:
   - Hvordan gik opsætningen?
   - Hvilke problemer blev mødt, og hvordan blev de løst?

---

# 🎉 Klar til at komme i gang!
Workshoppen afsluttes med opsamling og forberedelse til næste workshop, hvor vi arbejder videre med real-world datastrømme og avancerede datasikkerhedsaspekter.

