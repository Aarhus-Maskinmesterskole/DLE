# 🧪 Øvelse 2: Analyse af eksisterende emnestrukturer

## 🎯 Formål
Formålet med denne øvelse er at udvikle din evne til at analysere og vurdere kvaliteten af eksisterende emnestrukturer, som bruges i IIOT-systemer. Du skal lære at identificere både gode og dårlige praksisser inden for topic-navngivning, hierarkisk opbygning, semantisk tydelighed og skalerbarhed. Ved at gennemgå reelle eller simulerede eksempler vil du opnå en forståelse for, hvordan dårlig emnestruktur kan føre til forvirring, fejltolkning og ineffektivitet – og hvordan en veldesignet struktur kan understøtte samarbejde, vedligeholdelse og udvidelse af systemer.

Denne øvelse skal klæde dig på til at:
- Genkende ustruktureret eller inkonsistent navngivning
- Vurdere emnernes robusthed over tid og på tværs af teams
- Foreslå konkrete forbedringer og oversætte eksisterende emner til UNS-format
- Udvikle et kritisk blik på struktur, semantik og informationsværdi i emnehierarkier

---

## 🛠️ Forudsætninger
- Du har gennemført Øvelse 1 og har et grundlæggende kendskab til Unified Namespace (UNS)
- Du har adgang til Node-RED, tidligere flows, MQTT/Sparkplug-emner eller OPC UA NodeId’er fra Workshop 4
- Du kan skelne mellem flad og hierarkisk emnestruktur og ved, hvorfor semantik og entydighed er vigtige

---

## 🔍 Aktivitet – Trin-for-trin

### 1. Saml konkrete eksempler
- Find 2–3 emnestrukturer:
  - Et fra dit eget Node-RED- eller Sparkplug-flow (brug debug eller MQTT Explorer)
  - Et OPC UA-node-id fra din serverstruktur
  - Et "kritisk" eksempel – f.eks. fra undervisningsmateriale, en kollega eller et dårligt designet testmiljø

### 2. Analyser og vurder
For hver struktur:
- Notér:
  - Er der en logisk hierarkisk opbygning? (site/area/line/device/tag)
  - Er navngivningen konsistent og let at forstå?
  - Hvad siger emnet om datakildens kontekst og funktion?
  - Hvilke metadata er indlejret i emnet – og hvilke mangler?

Brug en skala fra 1 (meget dårlig) til 5 (meget god) og vurder:
- Klarhed
- Semantik
- Skalerbarhed
- Robusthed (ændringer, flytning, gensyn af data om 6 mdr.)

Skriv vurderinger og kommentarer i en tabel, skema eller i din notesbog.

### 3. Udpeg og forbedr ét eksempel
- Vælg det eksempel, du synes er dårligst eller mest utydeligt
- Forklar:
  - Hvad fungerer dårligt?
  - Hvorfor kan det give problemer på sigt (ved integration, drift, analyse)?
  - Hvordan kan det forbedres? Omskriv det i et nyt format baseret på UNS-principper

Eksempel:
```
Før: temp_sensor1
Efter: fabrik_alpha/hal3/linje2/device17/temperature/value
```

Angiv hvorfor du har valgt netop det hierarki og de navne.

### 4. Sammenlign med andre og diskuter
- Del dine resultater og forbedringsforslag med sidemanden eller gruppen
- Diskutér:
  - Hvad ser I som de mest almindelige problemer i dårlig emnestruktur?
  - Hvad kunne have hjulpet designeren? Guidelines, skabeloner, konventioner?
  - Hvordan opleves det at arbejde med gode vs. dårlige strukturer?

---

## 📋 Refleksion
Besvar følgende:
- Hvad har du lært om emnestrukturers betydning i større IIOT-systemer?
- Hvordan kan navngivning være både teknisk og kommunikativt værktøj?
- Hvordan ville du sikre, at et team eller virksomhed fastholder en god emnestruktur fremover?
- Hvad vil du selv være mere opmærksom på næste gang, du designer emner?

> 💡 Denne refleksion vil hjælpe dig med at formulere konkrete designprincipper, som du skal bruge i Øvelse 3, hvor du skal udvikle en fuld UNS-struktur for et simuleret produktionssystem.

