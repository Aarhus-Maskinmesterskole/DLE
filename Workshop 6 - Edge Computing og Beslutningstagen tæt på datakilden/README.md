# 📊 Workshop 6: Edge Computing og Beslutningstagen tæt på datakilden

## 📚 Introduktion
I denne sjette workshop udvider vi dine IIOT-kompetencer ved at rette blikket mod **Edge Computing**, et paradigme hvor databehandling og beslutningstagen foregår lokalt – direkte på eller tæt ved den enhed, der genererer data. Dette er en afgørende komponent i moderne IIOT-arkitektur, især når det gælder lav latenstid, øget robusthed, netværksuafhængighed og decentral intelligens.

Hvor tidligere workshops har fokuseret på central dataintegration, UNS og protokoller, handler denne workshop om at skabe logik **helt ude på kanten af netværket**. Edge computing tillader, at sensorer og controllere ikke kun indsamler data, men også agerer på det med det samme – før data overhovedet når cloud eller centrale systemer.

Workshoppen er designet til at give dig:
- Praktisk erfaring med at konfigurere lokale flows i Node-RED
- Indsigt i edge computing-arkitekturens rolle og fordele
- Øvelse i at behandle, filtrere og analysere data før det sendes videre
- Viden om forskellen på lokal og central intelligens
- Eksempler på simpel anomali-detektion og beslutningsunderstøttelse direkte på edge-niveau

Du vil arbejde med simulerede eller fysiske edge-enheder (fx Raspberry Pi, virtualiseret Linux eller container), og lære hvordan man lokalt filtrerer unødvendige datapunkter, implementerer thresholds og producerer handlinger – alt sammen tæt på kilden.

---

## 🎯 Formål
- At forstå hvad Edge Computing er, og hvorfor det er en vigtig arkitekturkomponent i IIOT
- At kunne implementere lokal logik, filtering og beslutningstagen i praksis
- At demonstrere hvordan edge-noder komplementerer centrale UNS- og cloud-baserede systemer
- At kunne måle og sammenligne latenstid, resiliens og robusthed mellem edge og cloud
- At få indsigt i, hvordan simple algoritmer som glidende gennemsnit og thresholds kan bruges lokalt

---

## 🧠 Kompetencer
Når workshoppen er afsluttet, forventes det at du:
- Kan forklare edge computing og placere det i en IIOT-sammenhæng
- Kan opsætte og teste lokal behandling i Node-RED (fx på Raspberry Pi eller VM)
- Kan implementere pre-processing, værdifiltrering, og threshold-beslutning
- Kan visualisere effekten af lokal behandling sammenlignet med cloud-routing
- Kan dokumentere og præsentere en komplet edge-løsning, herunder logik, flow og resultater

---

## 📋 Struktur og Øvelser
| Øvelse | Titel |
|--------|-------|
| 1 | Introduktion til Edge Computing og arkitektur |
| 2 | Opsætning af lokal beslutningsmotor (Node-RED Edge) |
| 3 | Pre-processing og filtrering af data på edge |
| 4 | Lokale thresholds og beslutningslogik |
| 5 | Sammenligning af edge vs cloud – latency og robusthed |
| 6 | Anomali-detektion med glidende gennemsnit (moving average) |
| 7 | Dokumentation og præsentation af edge-løsning |

Hver øvelse bygger ovenpå den forrige og integrerer både teori og praksis. Du får både mulighed for at eksperimentere teknisk og reflektere over dine valg.

---

## 📦 Aflevering
- Node-RED-flows, som viser lokal behandling, thresholds og eventuelle reaktioner
- Dashboard eller visuel visning af edge-behandlede data
- En kort skriftlig refleksion over:
  - Hvor og hvornår det giver mening at behandle data lokalt
  - Hvad du lærte om forskellen på edge og cloud i praksis
  - Hvordan du vil anvende edge computing i større arkitekturer
- Diagrammer eller grafik, der viser hvordan edge-noder placeres i IIOT-systemet

---

## 📢 Husk
Edge computing er ikke et alternativ til cloud eller UNS – det er en **strategisk udvidelse**, som gør det muligt at opnå bedre reaktionstid, mindske netværksbelastning og opretholde funktionalitet under netværksbrud. Men det kræver disciplin i navngivning, logik og struktur. 

Tænk derfor i arkitektur og dokumentation hele vejen – og vær klar til at vise, hvordan edge kan være både smart, simpelt og stærkt.

Vi ser frem til at se dine løsninger og hvordan du placerer edge i din IIOT-forståelse!

