# 🧪 Øvelse 5: Sammenligning af edge og cloud – latenstid og robusthed

## 🎯 Formål
Formålet med denne øvelse er at udforske og dokumentere forskellene mellem **lokal (edge-baseret)** og **cloud-baseret** databehandling i IIOT-systemer, med fokus på faktorer som **latenstid, robusthed, netværksafhængighed og failover-adfærd**. Du skal opsætte parallelle flows i Node-RED og gennemføre målinger og tests for at se, hvordan de to arkitekturer reagerer under både normale og udfordrende forhold.

Øvelsen skal give dig:
- Praktisk erfaring med performance-målinger og visualisering
- En forståelse af forskellene i reaktionstid og netværksbelastning
- Indblik i edge computing som failover-strategi
- Redskaber til at argumentere for arkitekturbeslutninger i IIOT

---

## 🧰 Forudsætninger
- Du har et fungerende lokal flow med beslutningslogik fra Øvelse 4
- Du har adgang til en cloud-service, f.eks.:
  - En offentlig MQTT-broker
  - En REST-endpoint (f.eks. Webhook.site eller egen Node-RED i skyen)
  - En cloud-database eller dashboard
- Du ved hvordan man måler tidspunkter med `Date.now()` og bruger `function`, `file`, `chart`, og `text`-noder i Node-RED
- Du har oprettet et dashboard til visning og sammenligning

---

## 🧩 Trin-for-trin opgave

### 1. Opstil et test-scenarie
- Brug en `inject`-node, der sender data hvert 5–10 sekund (fx temperatur = 32.1)
- Opret to parallelle flows:
  - Et edge-flow der behandler, reagerer og logger lokalt
  - Et cloud-flow der sender data til cloud og modtager svar (fx via `mqtt-out` eller `http-request`)

Eksempel på struktur:
```plaintext
[ inject ] → [ function: timestamp start ] →
  ├──→ [ edge decision + response + timestamp end ]
  └──→ [ cloud publish/request → cloud → response → timestamp end ]
```

### 2. Mål latenstid i begge flows
- Tilføj i starten:
```javascript
msg.start = Date.now();
return msg;
```
- I sidste node i begge flows:
```javascript
msg.end = Date.now();
msg.latency = msg.end - msg.start;
return msg;
```
- Visualisér latenstid i `ui_chart`, `ui_text` og log til fil:
  - `file`-node med CSV-struktur: `timestamp,start,end,latency,flow_type`

### 3. Introducér kunstig netværksforsinkelse (valgfrit)
- Brug `delay`-node i cloud-flow til at simulere netværksforsinkelse (fx 1–3 sekunder)
- Alternativt: forbind cloud-flow til en ustabil WiFi-forbindelse eller VPN-rute og observer

### 4. Simulér netværksfejl og observer fallback
- Midlertidigt frakobl internetadgang (fx ved at slukke WiFi)
- Brug `status`- eller `catch`-noder til at vise fejl i cloud-flow
- I edge-flow:
  - Skal alt fortsat fungere normalt?
  - Reageres der stadig korrekt på data?
  - Brug `ui_icon` eller `ui_toast` til at vise status: "Edge OK – Cloud fejl!"

### 5. Opsamling og visuel sammenligning
- Vis begge flows’ latenstider over tid i `ui_chart`
- Udregn gennemsnit og maksimal latenstid i `function`-noder og vis i `ui_text`
- Opsæt visuelle forskelle:
  - Grøn indikator for lav latenstid (< 100ms)
  - Gul for middel (100–500ms)
  - Rød for høj (> 500ms)
- Gem alle målinger til fil og lav evt. et excel-plot bagefter

---

## 📋 Refleksion
Skriv 10–15 linjer i logbog eller dokument:
- Hvad var den gennemsnitlige latenstid i dine to flows?
- Hvad skete der da netværket blev afbrudt? Hvordan reagerede cloud- og edge-systemer?
- Hvilken løsning viste sig mest robust – og hvorfor?
- Hvornår vil du anbefale edge fremfor cloud i virkelige projekter?
- Hvilke forbedringer kunne du forestille dig til failover eller redundans?

> 💡 Brug erfaringerne fra denne øvelse til at forstå, hvordan edge og cloud ikke er modsætninger – men komplementære arkitekturkomponenter i skalerbare, driftssikre IIOT-løsninger.

> 🔜 I næste øvelse skal du bruge lokal pre-processing og decision logic til at lave **anomali-detektion direkte på edge**, uden cloud-assistance.

