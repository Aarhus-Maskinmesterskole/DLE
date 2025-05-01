# 🧪 Øvelse 6: Stop angrebet og analyser hvad du så

## 🎯 Formål
I denne øvelse skal du afslutte din MITM-simulering og analysere, hvad der blev opsnappet under angrebet. Formålet er at vurdere konsekvenserne af ubeskyttet kommunikation og forstå, hvordan data kan aflures og evt. misbruges. Det er her, du samler trådene fra de tidligere øvelser og dokumenterer de observationer, der skal danne grundlag for din vurdering af risici og sikringsbehov.

---

## 🛠️ Forudsætninger
- Du har kørt `mitm.py` og opsnappet MQTT-trafik i klartekst.
- Du har set forskel på opsnappede beskeder før og efter TLS blev implementeret (Øvelse 4).

---

## ⚙️ Trin-for-trin

### 1. **Stop MITM-scriptet**
- Brug “Stop Attack” i GUI’en eller afslut scriptet i terminalen.
- Bekræft, at ARP-forgiftningen er ophørt (du kan pinge mellem klient og broker uden problemer).

### 2. **Gennemgå opsnappet data**
- Se på, hvad du har opsnappet i dit script/GUI:
  - Hvilke topics blev brugt?
  - Hvad var værdierne (payloads)?
  - Kunne du læse data i klartekst?
  - Var der følsomme oplysninger som adgangskoder, brugernavne, interne enhedsnavne osv.?

### 3. **Sammenlign før og efter TLS**
- Hvis du lavede testen igen efter TLS blev aktiveret:
  - Hvordan ændrede dataene sig i dit terminalvindue?
  - Kunne du stadig aflæse noget meningsfuldt?
  - Hvordan blev forbindelsen påvirket af, at du forsøgte MITM igen?

### 4. **Diskuter med en medstuderende**
- Hvad kunne en angriber reelt gøre med den information, du fangede?
- Hvordan kunne en virksomhed opdage, at der foregår MITM?
- Ville du som operatør kunne se det i logs, på dashboard, eller via nedbrud?

---

## 📋 Refleksion og dokumentation
- Dokumentér det du så: tag screenshots eller noter topics og payloads.
- Besvar disse spørgsmål i din portfolio:
  - Hvad blev opsnappet?
  - Hvordan kunne det misbruges?
  - Hvordan ændrede sikringen det?
  - Hvilke konkrete risici ser du i et system, der ikke bruger TLS?

> 💡 Denne dokumentation indgår i jeres endelige vurdering. Vær præcis, men fokuser på det vigtigste.

👉 Gå videre til Øvelse 7, hvor vi bygger et dashboard for visning og overblik.

