# 🧠 Workshop 9: Avanceret Beslutningsstøtte og Real-time Analyse

## 📚 Introduktion

I denne workshop bygger vi videre på dine dataopsamlings-, edge- og cloud-kompetencer ved at anvende dem til **avanceret beslutningsstøtte**. Du lærer at designe flows, der analyserer data i realtid og aktiverer handlinger baseret på foruddefinerede mønstre, tendenser eller maskinlæringsmodeller.

Formålet er at koble IIOT-data til **intelligente reaktioner**, som forbedrer drift, vedligeholdelse og ressourceudnyttelse. Eksempler kan være:

* Automatisk vedligehold baseret på vibration/temperatur
* Alarmer ved anomalier i energiforbrug
* Dynamisk styring af produktion ud fra forbrugsdata

---

## 🎯 Formål

* At arbejde med realtidsanalyser direkte i Node-RED eller med eksterne analysemoduler
* At anvende aggregerede data (gennemsnit, max, trends) til at danne beslutningsgrundlag
* At udvikle flows der kan udløse handling (fx alarm, notifikation, aktivering af enhed)
* At forstå hvordan data kan bruges prædiktivt frem for reaktivt

---

## 🧠 Kompetencer

Når workshoppen er gennemført, forventes du at kunne:

* Identificere målepunkter relevante for beslutningsunderstøttelse
* Designe beslutningslogik baseret på kombinerede datakilder
* Implementere realtids-flow, der analyserer og reagerer på data
* Vurdere hvorvidt beslutningslogikken bør ligge på edge eller cloud
* Dokumentere og formidle beslutningslogik visuelt

---

## 🧩 Øvelser (eksempler)

| Øvelse | Titel                                                           |
| ------ | --------------------------------------------------------------- |
| 1      | Identificér beslutningspunkter i jeres måledata                 |
| 2      | Lav realtidsanalyse med thresholds, trends og kombinerede flows |
| 3      | Trigger aktivering eller notifikation ved beslutningsgrundlag   |
| 4      | Simulér produktionsoptimering ud fra sensordata                 |
| 5      | Sammenlign manuel vs. automatiseret beslutning                  |
| 6      | Dokumentér beslutningslogik og reflekter over konsekvenser      |

---

## 📦 Aflevering

* Flow (.json) med realtids beslutningslogik
* Screenshots fra tests (fx dashboards med triggerpoints)
* Dokumentation:

  * Hvilke data bruges til beslutning?
  * Hvordan ser jeres logik ud – visuelt og funktionelt?
  * Hvor ligger intelligensen – og hvorfor her?
* Refleksion over styrker/svagheder i løsningen

---

## 📢 Husk

Avanceret beslutningsstøtte handler om **kontekst**: Hvad betyder dataen – og hvad bør vi gøre ved den? God beslutningslogik er hverken for følsom eller for langsom, og skal balancere mellem automatisering og forståelighed.

Du står nu med værktøjer og erfaring nok til at lave løsninger, som aktivt styrer og forbedrer virkelige systemer. Brug det klogt og ansvarligt.
