# 🧪 Øvelse 5: Logging og sporbarhed

## 🎯 Formål
I denne øvelse skal du arbejde med, hvordan man opbygger et sikkert, transparent og overvågeligt IIOT-system ved hjælp af logging. Logning er et af de vigtigste redskaber, vi har, når det kommer til at opdage fejl, identificere uautoriseret aktivitet og dokumentere systemets adfærd over tid.

Du skal både aktivere og analysere logs i din MQTT-broker og i klienten (fx Node-RED), så du ser hvordan hændelser og datakommunikation dokumenteres. Logging er ikke kun vigtigt i forhold til cybersikkerhed – det er også centralt i forbindelse med dokumentation af systemets normale drift, til fejlretning, og til auditformål i regulerede miljøer.

Ved at arbejde med logs lærer du at læse og tolke hændelser, forstå hvor og hvordan man bedst placerer logpunkter, og hvordan man balancerer detaljeringsniveau med systemets ydeevne.

---

## 🛠️ Forudsætninger
- Du har gennemført Øvelse 4 og har nu en fungerende MQTT-forbindelse med både TLS og adgangskontrol.
- Du har adgang til din MQTT-brokers konfiguration og logfiler (fx Mosquitto logs).
- Du har Node-RED (eller anden MQTT-klient) konfigureret og tilsluttet brokeren.
- Du har tidligere opsnappet eller forsøgt at opsnappe trafik ved hjælp af `mitm.py` og har dermed erfaring med sårbarheder i usikret kommunikation.

---

## ⚙️ Trin-for-trin: Logning i praksis

### 1. **Aktivér og konfigurer logging i MQTT-broker (Mosquitto)**
- Åbn konfigurationsfilen `mosquitto.conf`, og tilføj følgende:
  ```
  log_dest file /var/log/mosquitto/mosquitto.log
  log_type error
  log_type warning
  log_type notice
  log_type information
  ```
- Disse linjer sørger for, at brokeren logger både kritiske fejl, advarsler, forbindelser og almindelig drift.
- Genstart brokeren med `sudo systemctl restart mosquitto` eller tilsvarende.
- Navigér til logfilen og observer, hvad der bliver skrevet under almindelig drift.

### 2. **Observer forbindelser og hændelser**
- Lav følgende tests én ad gangen, og observer forskellen i loggen:
  - Forbind korrekt med gyldig bruger og TLS.
  - Prøv at oprette forbindelse med forkert brugernavn.
  - Prøv at oprette forbindelse uden TLS.
  - Prøv at genstarte klienten flere gange.
- Kig i loggen og notér:
  - Hvilke hændelser der registreres.
  - Hvor detaljerede informationer du får (IP-adresser, topics, loginforsøg osv.).
  - Hvad der ikke bliver logget – og hvad du evt. gerne ville kunne se.

### 3. **Log dataflow i klienten (Node-RED)**
- I din Node-RED-flow:
  - Placer `debug` nodes efter dine `mqtt-in` og `mqtt-out` nodes, så du kan se alle ind- og udgående beskeder i debug-panelet.
  - Tilføj en `file` node for at gemme beskeder til en `.log`- eller `.csv`-fil.
  - Alternativt: brug `sqlite` node til at gemme data i en database for senere analyse.
- Dette giver dig både realtidsindsigt og historik over, hvad systemet har sendt og modtaget.

### 4. **Test logging under angreb**
- Start dit `mitm.py` script og simulér et aflytningsforsøg.
- Undersøg om brokeren registrerer noget usædvanligt:
  - Kommer der uventede forbindelsesforsøg?
  - Er der spor i loggen af noget, der indikerer MITM-aktivitet?
  - Hvis ikke – hvad kunne du logge manuelt for at opdage det?

---

## 📋 Refleksion
Skriv dine svar på følgende spørgsmål i portfolioen:

- Hvordan kan logfiler være med til at opdage uautoriserede forbindelser?
- Hvilke hændelser logges automatisk, og hvilke skal man selv konfigurere?
- Hvordan kunne du som operatør eller udvikler blive gjort opmærksom på kritiske hændelser i realtid?
- Hvordan sikrer man, at logs ikke fylder for meget eller belaster systemet?
- Hvordan kunne du bruge logs i forbindelse med dokumentation til en kunde, en revisor eller en audit?

> 💡 Husk: Logs er kun værdifulde, hvis de bliver læst og reageret på. Gode logs skaber transparens og dokumentation, dårlige logs kan skjule problemer eller skabe støj.

---

👉 Når du er klar, går du videre til Øvelse 6, hvor vi arbejder med at omdanne vigtige hændelser til alarmer og automatiserede reaktioner.

