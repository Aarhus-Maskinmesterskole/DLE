# 🧪 Øvelse 1: Introduktion til UNS og topic-design

## 🎯 Formål
Formålet med denne øvelse er at introducere dig grundigt til konceptet **Unified Namespace (UNS)** og give dig praktisk erfaring med at analysere, omskrive og designe en struktureret, semantisk rig og skalerbar emnestruktur. Denne struktur skal kunne fungere på tværs af et komplet IIOT-økosystem og gøre det muligt at tilgå, forstå og vedligeholde datastrømme uanset protokol og system. 

Du lærer, hvordan korrekt navngivning og emnehierarki er afgørende for:
- Skalerbarhed i takt med at nye devices og sites tilføjes
- Klarhed og standardisering i dokumentation og drift
- Dataens genanvendelighed i tværgående funktioner som overvågning, analyse og beslutningsstøtte

Denne øvelse er fundamentet for resten af Workshop 5 og danner bro mellem den datamodellering du lavede i Workshop 4 og den emnearkitektur, der kræves i større produktionsopsætninger.

---

## 📖 Teori

### 🔗 Hvad er et Unified Namespace (UNS)?
Et UNS er et realtidsbaseret, hierarkisk organiseret navnerum, der fungerer som en fælles datakilde – et "single source of truth" – hvor alle datapunkter, hændelser og systemstatus fra hele organisationen er tilgængelige gennem ét fælles struktur- og navngivningsprincip. 

UNS anvendes på tværs af:
- Maskiner og automationsudstyr (OT)
- Overvågningssystemer og dashboards (SCADA/HMI)
- IT-systemer som MES og ERP

### 📦 Eksempel på UNS-struktur (Sparkplug-inspireret)
```
fabrik1/
├── produktion/
│   ├── linje1/
│   │   ├── plc01/
│   │   │   ├── temperatur
│   │   │   ├── motor_status
│   │   │   └── tryk
```
### 🔑 Vigtige designprincipper:
- Navne skal være **meningsfulde, entydige og læsbare**
- Brug **hierarkisk opbygning** (site → område → enhed → datapunkt)
- Hold fast i **ens konventioner** (små bogstaver, snake_case, timestamp som ISO8601)
- Indbyg **semantik** via emne eller i payload
- Navne skal være robuste overfor ændringer i fysisk placering

---

## 🛠️ Aktivitet – Trin-for-trin

### 1. Forstå og diskuter begrebet UNS
- Læs en introduktion til UNS fra fx Cirrus Link eller HiveMQ blog
- Forklar i egne ord:
  - Hvad adskiller et UNS fra almindelig MQTT-topicstruktur?
  - Hvorfor giver et fælles navnerum værdi i organisationen?

Diskutér med din sidemand eller i grupper.

### 2. Gennemgå og analyser dine egne emner
- Åbn dine flows fra Workshop 4 (MQTT og/eller OPC UA)
- Find eksempler på:
  - Uklar navngivning (f.eks. "temp1", "randomFloat")
  - Manglende hierarki (flade emner som "device42/temp")
  - Inkonsistent formatering

Notér mindst 3 forbedringspunkter.

### 3. Omskriv til UNS-form
- Tag et råt emne som fx:
```
co2sensor = 685
```
Og omskriv det til:
```
site1/hal3/ventilation/device17/co2_level/value = 685
```
Lav 2–3 sådanne eksempler og forklar dine valg:
- Hvorfor valgte du de navne og niveauer?
- Hvordan gør det emnet mere brugbart?

### 4. Lav en komplet UNS-struktur
- Forestil dig et lille anlæg med 2 linjer:
  - Hver linje har en PLC og 2 sensorer (fx temperatur og motorstatus)
- Lav en topic-struktur som:
```
fabrik_alpha/
├── linje1/
│   ├── plc01/
│   │   ├── temp_supply
│   │   └── motor1_status
├── linje2/
│   ├── plc02/
│   │   ├── temp_exhaust
│   │   └── motor2_status
```
Du må gerne bruge draw.io, papir eller whiteboard til at tegne strukturen. Lav gerne JSON eller skriftlige eksempler på hvordan datapunkterne ville blive brugt.

---

## 📋 Refleksion
Skriv en refleksion hvor du svarer på:
- Hvad overraskede dig ved emnestrukturering?
- Hvad er nemt at gøre forkert når man bygger en UNS?
- Hvordan kunne en velbygget UNS hjælpe både teknikere, udviklere og ledere?
- Hvordan relaterer UNS til semantik og datamodellering fra Workshop 4?

> 💡 I næste øvelse skal du vurdere andres emnestrukturer og finde forbedringsforslag. Dine erfaringer her vil hjælpe dig til at analysere med et kritisk blik.

