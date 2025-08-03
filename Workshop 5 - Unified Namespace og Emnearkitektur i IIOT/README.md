## 📊 Workshop 5: Lav dit eget lille dashboard

### 🌟 **Formål**

* At lære, hvordan du bygger et simpelt og overskueligt **dashboard** i Node-RED.
* At kunne vise status, målinger og evt. alarmer på en visuel måde, som alle kan forstå.
* At forstå hvorfor dashboards er vigtige i IIoT – både for overblik, fejlfinding og samarbejde.

---

### 👩‍💻 **Kompetencer du opbygger**

Efter workshoppen kan du:

* Bygge og tilpasse et Node-RED-dashboard med status, målinger og farver.
* Visualisere data fra egne og andres flows i realtid.
* Bruge dashboardet til at opdage fejl, alarmer og statusændringer.
* Forklare for andre, hvordan dashboardet virker, og hvorfor det giver overblik.

---

### 📚 **Introduktion**

Et dashboard er en “forside” til dine data:
Her kan du og andre **hurtigt se**, hvad der sker – om alt kører OK, eller der er problemer.
Det kan være tal, grafer, knapper eller indikatorer (fx grøn/rød) – alt sammen uden at kigge ind i flows eller kode.

---

## 📋 Øvelse 1: Byg et dashboard til én måling

**Formål:**

* At vise fx temperatur, tryk eller beskeder på dashboardet.

**Krav:**

* Lav en “ui\_gauge”, “ui\_text” eller “ui\_chart”, som viser en af dine målinger live.

---

## 📋 Øvelse 2: Tilføj statusindikator (OK/fejl) med farver

**Formål:**

* At kunne se om alt er OK, eller om der er en fejl, direkte på dashboardet.

**Krav:**

* Brug fx “ui\_led”, “ui\_text” eller “ui\_template” til at vise grøn (OK) eller rød (fejl).

---

## 📋 Øvelse 3: Lav flere visninger på samme dashboard

**Formål:**

* At samle flere målinger/statusser på ét sted for bedre overblik.

**Krav:**

* Tilføj mindst én ekstra visning (fx både temperatur og alarmstatus).

---

## 📋 Øvelse 4: Tilføj en alarm eller advarsel

**Formål:**

* At vise en tydelig alarm på dashboardet, hvis noget overskrider en grænse.

**Krav:**

* Lav fx et tekstfelt eller en rød indikator, der aktiveres hvis en måling går over/under en værdi.

---

## 📋 Øvelse 5: Del dit dashboard med andre

**Formål:**

* At andre kan se dit dashboard – fx på deres computer, tablet eller mobil.

**Krav:**

* Giv adressen til dashboardet videre (fx `http://[din-ip]:1880/ui`) og tjek at andre kan se det live.

---

### 📢 **Husk:**

* Et godt dashboard er **enkelt**, let at forstå og viser det vigtigste først.
* Brug farver og tydelige tekster – det gør det nemmere at spotte fejl eller ændringer.
* Spørg underviseren, hvis du vil prøve flere widgets eller visuelle tricks!
