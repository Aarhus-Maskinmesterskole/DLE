# 🧪 Øvelse 5: Sammenlign OPC UA, MQTT og Sparkplug B

## 🎯 Formål
I denne øvelse skal du sammenligne de tre centrale protokoller, du har arbejdet med i Workshop 4: **OPC UA**, **klassisk MQTT**, og **MQTT med Sparkplug B**. Disse teknologier repræsenterer forskellige tilgange til kommunikation og semantik i IIOT-systemer. Formålet er at give dig et solidt overblik over deres styrker og begrænsninger, så du fremover kan træffe mere informerede valg, når du arbejder med datakommunikation og systemintegration i praksis.

Du skal:
- Udarbejde en systematisk sammenligning på baggrund af dine egne erfaringer.
- Reflektere over hvordan de enkelte teknologier understøtter semantik, struktur, skalerbarhed og interoperabilitet.
- Diskutere hvilke teknologier der egner sig bedst til forskellige IIOT-scenarier.
- Øve dig i at kommunikere fordele og ulemper i et teknisk valg.

---

## 🛠️ Forudsætninger
Inden du går i gang, skal du have:
- Gennemført Øvelse 2 (OPC UA), Øvelse 3 (Sparkplug B) og Øvelse 4 (datamodel-design).
- Gemt eksempler på flows, payloads og strukturer fra dine egne tests.
- Forståelse for centrale begreber som datamodel, payload-format, topic-struktur og semantik.
- Grundlæggende kendskab til, hvordan protokoller indgår i en samlet IIOT-arkitektur.

---

## 🔍 Aktivitet – trin-for-trin

### 1. Udfyld sammenligningstabel
Lav en tabel med følgende kolonner:
- **Protokol** (OPC UA, MQTT, Sparkplug B)
- **Semantik-understøttelse** (fx datamodeller, typeinformation, enhedsangivelse)
- **Struktur og navngivning** (hierarki, topic-format, metadata)
- **Payload-format** (binært, JSON, protobuf, fleksibilitet)
- **Brugervenlighed** (opstart, værktøjer, dokumentation)
- **Skalerbarhed og vedligehold** (kompleksitet ift. mange enheder)
- **Sikkerhed** (TLS, certifikater, adgangskontrol)
- **Realtime-egnethed** (forsinkelse, robusthed, pub/sub-model)
- **Typiske brugsscenarier** (hvor/hvornår ser du det anvendt?)

Brug både egne observationer og evt. producentdokumentation til at udfylde tabellen.

### 2. Beskriv fordele og ulemper i praksis
Lav en skriftlig eller visuel sammenfatning (mindmap, liste eller plakat), hvor du:
- Fremhæver styrker og svagheder ved hver teknologi.
- Forklarer hvilke problemer du stødte på under test – og hvordan du løste dem.
- Sammenligner hvordan hver teknologi understøtter semantisk interoperabilitet.

### 3. Vurder anvendelsesområder
Reflektér over følgende spørgsmål:
- Hvornår er **OPC UA** det bedste valg – og hvornår bliver det for komplekst?
- Hvornår er **MQTT** ideelt – og hvornår bliver det for simpelt og ustruktureret?
- Hvornår giver **Sparkplug B** en god balance mellem struktur og enkelhed?
- Hvordan påvirker valget af protokol resten af dit system (fx krav til klienter, datalagring, monitoring og brugere)?

---

## 📋 Refleksion
Skriv 10–15 linjer eller lav en punktvis refleksion hvor du svarer på:
- Hvordan påvirker protokolvalget muligheden for **interoperabilitet** på tværs af platforme?
- Hvad har du lært om forskellen mellem **fleksibilitet** og **standardisering**?
- Hvordan kan **semantisk struktur** understøtte fejlfinding, udvikling og skalering?
- Hvilken protokol ville du vælge til:
  - En fabrik med 100+ sensorer?
  - Et lille edge-baseret setup med få enheder?
  - En løsning der skal sende data til både lokal database og cloud?
- Hvordan har dine egne test påvirket din opfattelse af de tre teknologier?

---

## 📤 Aflevering (format)
Du må gerne aflevere som:
- PDF-dokument med tabel, refleksion og screenshots
- Plakat / infografik / OneNote-side med sammenligning
- Kort video med forklaring og visning af flows

> 💡 Husk: Det vigtige er ikke hvilken teknologi der er “bedst” – men hvilken der passer bedst **i konteksten**. Din evne til at analysere og begrunde dit valg er det centrale mål for øvelsen.

