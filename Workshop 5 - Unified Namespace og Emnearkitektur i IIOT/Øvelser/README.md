# 📊 Workshop 5: Øvelsesoversigt med Formål

## 📚 Introduktion
Denne README giver overblik over alle øvelser i Workshop 5, som handler om at udvikle og implementere et **Unified Namespace (UNS)** i praksis. Workshoppen bygger videre på tidligere erfaringer med protokoller (MQTT, OPC UA, Sparkplug B) og fokuserer på at skabe et **fælles emnehierarki**, der understøtter skalerbar, semantisk og realtidsbaseret dataudveksling i IIOT-systemer.

Målet er, at de studerende ikke blot kan strukturere og visualisere data, men også forstå og dokumentere arkitekturen bag moderne, interoperable IIOT-løsninger.

---

## 📋 Øvelse 1: Introduktion til UNS og topic-design
**Formål:**
- Forstå hvad et Unified Namespace er
- Lære hvorfor topic-struktur og navngivning er afgørende
- Designe simple hierarkier baseret på fysisk/teknisk struktur

**Krav:**
- Lav emneeksempler og diskuter designprincipper
- Omskriv rå emner til hierarkiske, semantiske emner

---

## 📋 Øvelse 2: Analyse af eksisterende emnestrukturer
**Formål:**
- Opøve kritisk analyse af topic-struktur
- Genkende dårlig navngivning og manglende semantik

**Krav:**
- Evaluer 2–3 eksempler (MQTT, OPC UA eller egne flows)
- Foreslå forbedringer og omskriv emner til UNS-format

---

## 📋 Øvelse 3: Design af eget topic-hierarki (UNS)
**Formål:**
- Udvikle en fuld UNS-struktur for et fiktivt anlæg
- Træne hierarkisk tænkning og emnenormalisering

**Krav:**
- Design et hierarki med minimum 6 datapunkter
- Dokumentér emnestrukturen (grafisk, tabel, JSON etc.)

---

## 📋 Øvelse 4: Mapping af OPC UA-data til UNS
**Formål:**
- Praktisk erfaring med at læse data fra OPC UA og strukturere det efter UNS

**Krav:**
- Læs min. 3 datapunkter fra OPC UA-server
- Omform data til UNS-format og visualisér i Node-RED

---

## 📋 Øvelse 5: Mapping af Sparkplug B-data til UNS
**Formål:**
- Lære at arbejde med Sparkplug-metrics og mappe dem til eget UNS

**Krav:**
- Abonnér på DDATA-beskeder fra Sparkplug-device
- Parse payload og transformer til UNS-emner
- Visualisér i Node-RED dashboard

---

## 📋 Øvelse 6: Validering og visualisering af samlet UNS
**Formål:**
- Samle data fra flere protokoller og validere om UNS fungerer i praksis

**Krav:**
- Visualisér data fra både OPC UA og Sparkplug B i ét samlet dashboard
- Brug mindst 3 visningstyper (fx gauge, table, icon)
- Dokumentér resultater og observerede forbedringspunkter

---

## 📋 Øvelse 7: Dokumentation og præsentation af dit UNS
**Formål:**
- Samle og præsentere al dokumentation, refleksion og visualisering
- Vise evnen til at strukturere, integrere og formidle en teknisk løsning

**Krav:**
- Aflever en portefølje med flow, screenshots, struktur og refleksion
- Præsentér dit UNS-projekt som slides, video eller PDF

---

## 📢 Husk
Workshop 5 er en afsluttende workshop i denne serie – og et vigtigt skridt mod at kunne designe og implementere professionelle IIOT-løsninger. Hver øvelse bygger ovenpå den forrige og kulminerer i en samlet dokumentation og refleksion, der demonstrerer dine færdigheder i interoperabilitet, struktur og systemintegration.

Vi glæder os til at se din løsning!

