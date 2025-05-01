# 🧪 Øvelse 1: Introduktion til Edge Computing og arkitektur

## 🎯 Formål
Formålet med denne øvelse er at give dig en grundlæggende forståelse for, hvad **Edge Computing** betyder i praksis, og hvordan det passer ind i en moderne IIOT-arkitektur. Du skal lære, hvordan beslutningstagen, databehandling og automation kan rykkes **tættere på datakilden** – hvilket giver gevinster i form af lavere forsinkelse, bedre robusthed og lokal autonomi.

Denne øvelse danner grundlag for de kommende aktiviteter i workshoppen, hvor du vil implementere, teste og evaluere edge-løsninger. Den kombinerer læsning, diskussion og skitsering af arkitektur.

---

## 📖 Teori – læs og forstå

### 🔍 Hvad er Edge Computing?
Edge computing er en arkitektur, hvor databehandling, analyse og beslutningstagen sker tæt på datakilden – fx på en PLC, et edge-device som en Raspberry Pi eller en industriel gateway. Dette står i kontrast til cloud computing, hvor data sendes langt væk og behandles centralt.

### 💡 Hvorfor bruge edge computing i IIOT?
- **Lavere latenstid:** Hurtig reaktion uden ventetid fra netværk eller cloud
- **Robusthed:** Edge fortsætter med at fungere selv ved netværksfejl
- **Båndbreddeoptimering:** Kun vigtige, filtrerede data sendes videre
- **Skalerbarhed:** Lokale beslutninger gør det lettere at udvide systemet
- **Sikkerhed:** Mindre data eksponeres til nettet eller cloud

### 📦 Edge vs Cloud – sammenligning
| Parameter       | Edge                       | Cloud                      |
|----------------|----------------------------|----------------------------|
| Latenstid       | Meget lav                  | Moderat til høj            |
| Afhængighed af netværk | Nej (lokal drift mulig)  | Ja                         |
| Skalerbarhed    | Begrænset til hardware     | Teoretisk ubegrænset       |
| Datafiltrering  | Lokalt                     | Efter modtagelse           |
| Autonomi        | Høj                        | Lav/moderat                |

---

## 🛠️ Praktisk aktivitet

### 1. Læs anbefalet materiale (30–45 minutter)
- Edge-computing forklaring fra Hivemq, Siemens eller ABB (find links i undervisningsmateriale)
- Find egne eksempler fra industrien (maskiner, robotter, procesanlæg), hvor edge kan give værdi

### 2. Diskussion i grupper (20–30 minutter)
Diskutér med sidemanden eller i grupper:
- Hvilke fordele og ulemper ser I ved at flytte logik ud til kanten?
- Hvilke use cases kræver hurtig reaktion (ms til sekunder)?
- Hvad sker der, hvis al logik er central, og forbindelsen går ned?

### 3. Tegn en edge-arkitektur (30 minutter)
- Brug papir, whiteboard eller draw.io
- Vis mindst én sensor, én edge-enhed og én cloud-forbindelse
- Vis hvad der sker på edge-niveau og hvad der sendes videre til cloud

**Eksempel:**
- Temperaturmåling → behandles på edge → hvis > 70°C → aktiver relæ og log hændelse lokalt
- Samtidig sendes kun gennemsnitsværdi hvert 10. minut til cloud

---

## 📋 Refleksion
Skriv 5–10 linjer i din notesbog eller dokument:
- Hvad forstod du ved edge computing, som du ikke vidste før?
- Hvilke fordele så du tydeligst i dagens diskussion?
- Hvordan tror du, edge og cloud kan arbejde sammen i dit eget systemdesign?

> 💡 Husk: I næste øvelse skal du bygge dit eget edge-flow – så notér idéer du fik undervejs!

