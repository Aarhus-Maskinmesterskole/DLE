# 📊 Workshop 3: Øvelsesoversigt med Formål

## 📚 Introduktion
Denne README beskriver de enkelte øvelser i Workshop 3, hvor vi fokuserer på cybersikkerhed i IIOT-systemer – med særligt fokus på trusler som Man-in-the-Middle (MITM), sikkerhedsprotokoller som TLS, adgangskontrol og teknikker til at analysere og visualisere datasikkerhed.

Hver øvelse bygger ovenpå den forrige og er designet til at give erfaring med både angreb og forsvar i et kontrolleret miljø.

---

## 📋 Øvelse 1: Forstå IIOT-sikkerhedstrusler
**Formål:**
- At introducere begreberne sniffing, spoofing og MITM-angreb.
- At skabe forståelse for hvor i IIOT-arkitekturen truslerne opstår.
- At danne begrebsramme for resten af workshoppen.

**Krav:**
- Læs og diskuter eksempler på sikkerhedsbrud.
- Udarbejd egne noter med typiske angreb og konsekvenser.

---

## 📋 Øvelse 2: Kør MITM-script og observer data
**Formål:**
- At opsnappe MQTT-data i klartekst via MITM-simulering.
- At lære hvordan usikret datatrafik kan læses og misbruges.
- At analysere hvad der kan ses og hvordan.

**Krav:**
- Brug udleveret Python-GUI-script til at simulere MITM.
- Dokumentér opsnappet data og datatyper.

---

## 📋 Øvelse 3: Manipulér data i transit
**Formål:**
- At demonstrere hvordan data kan ændres i en MITM-situation.
- At reflektere over konsekvenser af forfalsket sensor- eller statusdata.
- At øve manipulation på en måde, der ikke bliver opdaget.

**Krav:**
- Ændr payload i script og vis forskel mellem oprindelig og manipuleret besked.
- Dokumentér hvad der ændres og hvorfor.

---

## 📋 Øvelse 4: Implementér TLS og adgangskontrol
**Formål:**
- At beskytte datatrafik mod MITM ved brug af kryptering og autentifikation.
- At opnå praktisk erfaring med TLS-certifikater og brugerstyring.

**Krav:**
- Konfigurer Mosquitto-broker med TLS og adgangskontrol.
- Forbind klient med certifikat og login.
- Gentest MITM og dokumentér effekten.

---

## 📋 Øvelse 5: Dokumentér angrebet med logging
**Formål:**
- At logge og dokumentere datatrafik før og efter TLS.
- At samle spor og beviser for MITM.
- At skabe grundlag for vurdering og forbedring.

**Krav:**
- Gem output fra debug, file eller database.
- Udvælg eksempler før/efter og gem dem i struktur.

---

## 📋 Øvelse 6: Stop angrebet og analyser hvad du så
**Formål:**
- At afslutte MITM-angrebet og evaluere resultaterne.
- At identificere risici i usikrede systemer.
- At forberede konklusion og evaluering.

**Krav:**
- Gennemgå loggede og opsnappede data.
- Dokumentér payloads, topics og angrebsmuligheder.

---

## 📋 Øvelse 7: Visualisering med dashboard og statusindikatorer
**Formål:**
- At præsentere sikkerhedsstatus og dataoversigt i realtid.
- At træne design af brugervenlige statusoversigter.

**Krav:**
- Brug Node-RED dashboard til at vise status med farver og indikatorer.
- Visualisér mindst én sensor og én hændelsestilstand (OK/FEJL).

---

## 📋 Øvelse 8: Samlet opsamling og refleksion
**Formål:**
- At dokumentere og samle alle resultater fra workshoppen.
- At vise teknisk forståelse og refleksion over sikkerhed.

**Krav:**
- Aflever samlet portfolio med dokumentation, refleksion og evt. video.
- Inkludér tests, billeder, flow og sikkerhedsvurdering.

---

## 📢 Husk
Alle øvelser bygger ovenpå hinanden – dine opsætninger og erfaringer fra én øvelse bliver brugt i de næste.  
Du forventes at dokumentere undervejs og reflektere over dine handlinger og valg.  
Målet er ikke blot at kunne “få det til at virke” – men at **forstå hvorfor det virker, og hvordan du sikrer det bedst muligt**.

Vi glæder os til at se jeres arbejde!

