# 🧪 Øvelse 4: Lokale thresholds og beslutningslogik på Edge

## 🎯 Formål
Formålet med denne øvelse er at opbygge og afprøve **lokal beslutningslogik baseret på tærskelværdier (thresholds)** direkte på en edge-enhed. Ved at analysere data og reagere på hændelser lokalt, uden at skulle involvere cloud eller centrale serversystemer, opnår vi hurtigere svartider, mindre belastning af netværket og en højere grad af robusthed i det samlede IIOT-system.

Du kommer til at arbejde med at:
- Definere og konfigurere logik, der reagerer på måledata
- Udskille normale, advarsel og kritiske tilstande baseret på dynamiske eller faste tærskler
- Aktivere notifikationer og logik i Node-RED, når værdier overskrider definerede grænser
- Implementere en enkel alarm-kvitteringsmekanisme for brugerinteraktion

Denne øvelse danner et vigtigt praktisk grundlag for at kunne træffe automatiske beslutninger tæt på datakilden – en af de mest centrale idéer i edge computing.

---

## 🧰 Forudsætninger
For at kunne gennemføre øvelsen skal du have:
- Gennemført Øvelse 3 og have et fungerende flow, der leverer pre-processerede og validerede målinger
- Adgang til Node-RED med følgende noder tilgængelige:
  - `function`, `switch`, `rbe`, `ui_led`, `ui_icon`, `ui_notification`, `ui_button`, `ui_text`, `ui_chart`
- Et eksisterende dashboard med visningsmuligheder og minimum én realtidsdatakilde

Hvis du arbejder i simuleret miljø, kan du fortsætte med en `random`-baseret sensor og bruge logikken herpå.

---

## 🧩 Trin-for-trin opgave

### 1. Fastlæg dine tærskelværdier
- Vælg en måling, du ønsker at overvåge (fx temperatur, CO₂, tryk, spænding)
- Definér mindst tre niveauer:
  - Normal: fx < 30°C
  - Advarsel: 30–40°C
  - Kritisk: > 40°C
- Notér værdierne i et separat dokument eller på dit dashboard som reference

### 2. Implementér tærskelbaseret logik
- Tilføj en `function`-node efter din datafiltrering
- Indsæt logik der vurderer målingen og tilføjer felterne `status` og `color`:
```javascript
let value = msg.payload.value;
if (value > 40) {
  msg.payload.status = "CRITICAL";
  msg.payload.color = "red";
} else if (value > 30) {
  msg.payload.status = "WARNING";
  msg.payload.color = "orange";
} else {
  msg.payload.status = "OK";
  msg.payload.color = "green";
}
return msg;
```
- Alternativt: brug en `switch`-node til at sortere målinger i tre output-grene

### 3. Visualisér systemets tilstand
- Tilføj visuelle komponenter i dashboardet:
  - `ui_led` eller `ui_icon` med farver afhængigt af status
  - `ui_text` til at vise statusbeskeder
  - `ui_chart` med referencegrænser markeret (brug `threshold`-linie eller særskilte datapunkter)

### 4. Reagér på kritiske tilstande
- Når status er “CRITICAL”, skal systemet:
  - Udsende en `ui_notification` til brugeren
  - Logge en alarmtekst til en fil ved hjælp af `file`-node (append)
  - Evt. sende en MQTT-meddelelse til emne som `edge/alerts/critical`
```javascript
msg.payload = {
  topic: "edge/alerts/critical",
  value: msg.payload.value,
  timestamp: new Date().toISOString(),
  status: msg.payload.status
};
return msg;
```
- Brug `rbe` for at undgå gentagne beskeder, hvis værdien forbliver kritisk over længere tid

### 5. (Bonus) Implementér manuel alarmkvittering
- Tilføj en `ui_button` med label “Kvitter alarm”
- Brug `context.set("alarm_acknowledged", true)` og tjek dette i din beslutningslogik
- Ved kvittering:
  - Vis `ui_toast`-besked: “Alarm kvitteret af bruger”
  - Sæt LED tilbage til grøn eller standby
  - Log tidspunkt og brugerhandling

---

## 📋 Refleksion
Skriv en kort refleksion (10–15 linjer):
- Hvad oplevede du som den største fordel ved lokal beslutningslogik?
- Hvordan kunne en kombination af thresholds og lokale alarmer forbedre et fysisk anlægs sikkerhed?
- Hvad ville du gøre, hvis du havde flere sensorer der skal afgøre én samlet status?
- Hvad gør du, hvis du vil gøre dine thresholds konfigurerbare via dashboardet i stedet for hårdkodet?
- Hvordan ser du potentialet for edge-baseret logik i din egen branche eller i virkelige scenarier?

> 💡 I næste øvelse skal du sammenligne dine edge-flow med en cloud-baseret løsning og vurdere latenstid, robusthed og skalerbarhed.

