# 🧪 Øvelse 2: Opsætning af lokal beslutningsmotor med Node-RED (Edge)

## 🎯 Formål
Formålet med denne øvelse er at give dig praktisk erfaring med at oprette og konfigurere en **lokal beslutningsmotor** ved hjælp af Node-RED på en edge-enhed. Det indebærer, at du etablerer et selvstændigt flow, som kan modtage data fra en sensor (eller simuleret kilde), analysere den lokalt og generere beslutninger og reaktioner uden afhængighed af cloud eller eksterne servere.

Du skal udvikle et flow, der kan overvåge sensordata (som temperatur, fugtighed, gasniveauer eller CO₂), identificere kritiske grænseværdier og aktivere visuelle indikatorer eller meddelelser. Dette er første skridt i at udnytte fordelene ved Edge Computing, hvor realtidsbeslutninger bliver mulige direkte dér, hvor data opstår.

Denne øvelse lægger fundamentet for alle de efterfølgende aktiviteter, hvor vi går mere i dybden med filtrering, aggregering, edge-logik og systemintegration.

---

## 🧰 Forudsætninger og opsætning
Før du går i gang, skal følgende være opfyldt:

- Du har Node-RED installeret og tilgængelig lokalt – enten på en fysisk edge-enhed (som Raspberry Pi eller industriel gateway) eller i en virtuel maskine eller Docker-container.
- Du har adgang til én af følgende datakilder:
  - Simuleret sensor via `random` og `inject`-noder
  - MQTT-sensor via `mqtt-in`-node
  - Fysisk sensor via `serial-in`-node eller GPIO
- Du har installeret følgende noder:
  - `node-red-dashboard` (til visualisering)
  - `node-red-node-random` (til simulering af datakilder)
  - `node-red-contrib-moment` (valgfrit – til tidsstempling og tidshåndtering)

---

## 🧩 Trin-for-trin opgave

### 1. Generér eller modtag data
- Start med at opsætte en data-generator:
  - Brug `inject` til at sende hvert 5–10 sekunder
  - Tilslut en `random`-node med fx interval 20–50 og udgang som float
  - Alternativt: forbind til en MQTT-topic eller sensor
- Brug en `function`-node eller `change`-node til at strukturere output sådan:
```json
{
  "value": 26.3,
  "unit": "°C",
  "timestamp": "2024-06-01T10:05:12Z"
}
```
- Husk at bruge `moment` eller `new Date().toISOString()` til timestamp.

### 2. Implementér beslutningslogik
- Opret en `function`-node, der sammenligner værdien mod en grænse:
```javascript
if (msg.payload.value > 30) {
  msg.payload.status = "ALERT: Overheating";
  msg.payload.color = "red";
} else {
  msg.payload.status = "OK";
  msg.payload.color = "green";
}
return msg;
```
- Tilslut `ui_text`, `ui_led` og `ui_gauge` for visualisering.
  - Brug `ui_led` til at vise status med farve
  - Brug `ui_text` til statusbesked
  - Brug `ui_gauge` til live visning af målingen

### 3. Tilføj flow-kontrol og opdeling
- Indsæt en `switch`-node, som sender data videre afhængigt af status
  - Gren 1: normal drift → log + visning
  - Gren 2: kritisk → alarm, fx `ui_notification` eller logning i fil
- Tilføj evt. en `delay`-node for at undgå spam ved gentagne alarmer

### 4. Håndtér fejl og robusthed
- Tilføj `catch`-node, som fanger fejl globalt
  - Forbind til `ui_toast` eller `debug` for fejlhåndtering
- Brug `status`-node til at vise systemstatus (OK, fejl, standby)
- Implementér evt. fallback-mekanisme ved data-mangel (vis "N/A")

### 5. Bonus: Lokal logning
- Tilføj `file`-node og gem alle ALERTS lokalt i CSV-format:
```javascript
msg.payload = `${msg.payload.timestamp},${msg.payload.value},${msg.payload.status}\n`;
return msg;
```
- Dette kan udvides til audit trail eller system-overvågning

---

## 📋 Refleksion
Skriv 8–12 linjer hvor du reflekterer over følgende:
- Hvad lærte du om at flytte beslutningstagen til en lokal enhed?
- Hvordan påvirker lokal logik systemets robusthed og reaktionstid?
- Hvilke udfordringer oplevede du i opsætningen – og hvordan løste du dem?
- Hvad er den primære forskel på denne type arkitektur og traditionel cloud-fokus?
- Hvordan kan dette flow skaleres eller overføres til et industrielt miljø?

> 💡 Tænk allerede nu på hvordan du i næste øvelse vil filtrere data og reducere unødvendig støj – så edge kun sender det mest relevante videre.

