## Workshop 1: Introduktion til IIoT‑kommunikation i Node‑RED (MQTT · CoAP · AMQP · Modbus TCP)

### 🌟 Formål

Workshoppen introducerer de studerende til grundlæggende IIoT‑kommunikation og praktisk opsætning af fire udbredte industrielle protokoller: **MQTT, CoAP, AMQP og Modbus TCP**. Fokus er på at forstå kommunikationsarkitektur, konfigurere forbindelserne i Node‑RED, vurdere deres styrker og svagheder samt dokumentere arbejdet professionelt.

Målet er, at de studerende ikke kun kan konfigurere systemer, men også vælge passende teknologier ud fra krav til drift, vedligeholdelse og datasikkerhed.

### 🔄 Struktur for workshoppen

1. **Introduktion** – IIoT vs IT, arkitektur og protokoloversigt
2. **Gennemgang af hver IIoT‑protokol** – MQTT · Modbus TCP · CoAP · AMQP
3. **Praktisk arbejde i Node‑RED** – opsætning af de fire protokoller
4. **Optagelse af video** – demonstration af opsætning
5. **Udarbejdelse af PowerPoint** – sammenligning af protokollerne
6. \*\*Afleveringsinstruktioner og opsamling

### 🗂️ Mappe‑ og filstruktur (aflevering)

```
Workshop1_IIoT_kommunikation/
├── Video/
│   └── iiot_protocol_setup_demo.mp4
├── PowerPoint/
│   └── iiot_protocol_comparison.pptx
├── Node-RED_Flows/
│   ├── mqtt_flow.json
│   ├── modbus_flow.json
│   ├── coap_flow.json
│   └── amqp_flow.json
└── Dokumentation/
    └── opsummering.md
```

### 👩‍💻 Kompetencer efter workshoppen

Efter forløbet forventes den studerende at kunne:

* Beskrive forskellene mellem **MQTT, Modbus TCP, CoAP og AMQP**.
* Opsætte og konfigurere alle fire protokoller i Node‑RED.
* Forklare fordele og ulemper ved hver protokol ift. drift, vedligeholdelse og datasikkerhed.
* Dokumentere teknisk opsætning gennem video og en skriftlig PowerPoint‑præsentation.
* Identificere hvor driftssikkerhed, skalering og sikkerhed spiller en rolle i valg af protokol.

### 📅 Hvad skal afleveres

1. **Video (MP4)**

   * Kort forklaring af hver protokol.
   * Live demonstration af opsætning i Node‑RED.
2. **PowerPoint‑præsentation (PPTX)**

   * Fordele og ulemper for hver protokol.
   * Samlet vurdering af, hvilken protokol der er bedst til driftssikre IIoT‑systemer.
3. **Node‑RED‑flows (JSON)**

   * `mqtt_flow.json`, `modbus_flow.json`, `coap_flow.json`, `amqp_flow.json`
4. **Kort opsummering (Markdown eller PDF)**

   * Hvordan gik opsætningen?
   * Hvilke problemer blev mødt, og hvordan blev de løst?

### 🎉 Klar til at komme i gang!

Workshoppen afrundes med opsamling og en teaser til næste workshop, hvor vi arbejder videre med real‑world datastrømme og avancerede datasikkerhedsaspekter.
