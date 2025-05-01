# 🧪 Øvelse 5: Dokumentér angrebet med logging og forbered afslutning

## 🎯 Formål
I denne øvelse skal du arbejde med at **dokumentere og analysere dine observationer fra MITM-angrebet**. Formålet er at sikre, at du kan redegøre for, hvad du så, hvordan det kunne misbruges, og hvilke tegn der potentielt kunne have afsløret angrebet. Logging fungerer her som dit vigtigste værktøj: du bruger det til at samle beviser, forstå hændelsesforløbet og evaluere, hvor sårbart et ubeskyttet system er.

Denne øvelse lægger fundamentet for den afsluttende analyse i Workshop 3. Når man arbejder professionelt med cybersikkerhed, er det ikke nok at vide at noget skete – man skal kunne **bevise** det, og forstå dets konsekvenser. Derfor skal du nu samle dine tekniske iagttagelser i en struktureret dokumentation, som kunne bruges i en sikkerhedsvurdering i en rigtig virksomhed efter et sikkerhedsbrud.

Du lærer, hvordan du opsamler relevante data, hvordan du gemmer dem, og hvordan du vurderer om dine observationer giver mening. Du får også erfaring med at adskille normal systemadfærd fra unormal, og du begynder at tænke som en IT-sikkerhedsanalytiker, der skal bruge fakta til at tage beslutninger.

---

## 🛠️ Forudsætninger
For at kunne gennemføre denne øvelse skal følgende være på plads:

- Du har gennemført Øvelse 2–4 og har opsnappet data via dit MITM-script.
- Du har testet både før og efter du aktiverede TLS/adgangskontrol i dit MQTT-setup.
- Du har adgang til Node-RED eller en anden MQTT-klient, og du kan bruge debug-værktøjer.
- Du ved hvilke topics og værdier dit system arbejder med.

---

## ⚙️ Trin-for-trin

### 1. **Opsæt lokal logning i klienten (Node-RED eller andet)**
- Tilføj `debug`-noder efter dine `mqtt-in`-noder, så du kan se alle beskeder.
- Gem output til fil ved hjælp af `file` node – gerne i CSV- eller JSON-format.
- Hvis du har opsat SQLite i tidligere øvelser, så brug `sqlite` node til at logge datastrømmen automatisk.
- Notér tidsstempler og værdier – det er vigtigt til senere sammenligning.

### 2. **Sammenlign data før og efter TLS**
- Lav to konkrete tests:
  - Uden TLS: send data og aflyt med MITM. Log hvad du ser.
  - Med TLS: send data igen. Se om MITM-scriptet stadig kan vise noget.
- Gem et eksempel på begge tilfælde:
  - F.eks. screenshot, fil eller kopi af debug-output
- Kommentér forskellen – hvad var synligt før, og hvad er skjult nu?

### 3. **Vurder systemets adfærd og logs**
- Tjek om din MQTT-broker (fx Mosquitto) loggede noget mistænkeligt:
  - Forkerte forbindelser?
  - Afbrudte forbindelser?
  - Fejl ved certifikater eller login?
- Tjek Node-RED eller klientlog for:
  - Timeout-fejl
  - Manglende svar
  - Uventede payloads
- Brug denne information til at vurdere, hvor synligt angrebet var for systemet.

### 4. **Skab en dokumentationspakke til analyse**
- Lav en mappe eller notesamling hvor du gemmer:
  - Screenshots af opsnappede beskeder
  - Dokumentation af forsøg med TLS (hvad blev der ikke vist?)
  - Dine egne noter om processen og testmiljøet
- Du må meget gerne bruge timestamps og navngivning som gør det nemt at følge rækkefølgen.

---

## 📋 Refleksion
Besvar følgende spørgsmål som del af din portfolio:

- Hvilke beskeder blev opsnappet før sikring? Var de følsomme?
- Hvad så du (eller så du ikke) efter TLS blev aktiveret?
- Hvordan kunne du i en rigtig organisation bruge denne logning til at påvise angreb eller lækager?
- Hvorfor er det vigtigt at have sporbarhed i sikkerhedskritiske systemer?
- Hvad ville du anbefale at logge i et produktionsmiljø for at sikre eftervisning og dokumentation?

> 💡 Dette er din overgangsøvelse fra MITM-angreb til teknisk evaluering. Du dokumenterer dine resultater og forbereder dig til analysen i Øvelse 6.

👉 Gå videre til Øvelse 6, hvor du bruger dine logninger og dokumentation til at vurdere sikkerhedsniveau og risici.

