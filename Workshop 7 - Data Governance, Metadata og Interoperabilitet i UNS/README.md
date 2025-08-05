## 📊 Workshop 7: Lav simple alarmer og advarsler

### 🌟 **Formål**

* At lære, hvordan du sætter **grænser for dine målinger** og viser alarmer eller advarsler, når noget er “farligt” eller unormalt.
* At gøre fejlsituationer **meget tydelige** på dit dashboard eller i din log.
* At forstå, hvordan alarmer hjælper med at forebygge skader og fejl – både i industrien og i hjemmet.

---

### 👩‍💻 **Kompetencer du opbygger**

Efter workshoppen kan du:

* Sætte en øvre og/eller nedre grænse for målinger (fx temperatur, tryk).
* Få Node-RED til at vise en alarm/advarsel, når værdien går udenfor de tilladte grænser.
* Logge alarmhændelser i en fil (fx CSV) eller sende besked via dashboard.
* Forklare for andre, hvorfor alarmer er vigtige og hvordan de kan forebygge større problemer.

---

### 📚 **Introduktion**

Nu går du fra bare at **logge data** til at **handle på det**, når noget ikke er som det skal være.
Du lærer at sætte grænser og vise alarm eller advarsel med det samme – fx hvis temperaturen bliver for høj, eller trykket for lavt.

---

## 📋 Øvelse 1: Sæt grænser for din måling

**Formål:**

* At vælge fornuftige øvre/nedre grænser for én af dine målinger (fx temperatur).

**Krav:**

* Brug en function-node eller “rbe”-node til at sammenligne værdien med dine grænser (fx under 10 eller over 30 = alarm).

---

## 📋 Øvelse 2: Vis alarm på dashboard

**Formål:**

* At gøre alarmen synlig for alle – fx med rød tekst, ikon eller blinkende felt.

**Krav:**

* Brug “ui\_text”, “ui\_led”, “ui\_template” eller lignende widget i dashboardet til at vise alarmen/advarslen tydeligt.

---

## 📋 Øvelse 3: Log alarmhændelser i en fil

**Formål:**

* At kunne gemme, hvornår og hvorfor en alarm blev udløst.

**Krav:**

* Brug “file”-node til at logge tidspunkt, måling, alarmtype osv. i en CSV-fil, hver gang alarmen går.

---

## 📋 Øvelse 4: Ekstra (valgfrit): Send advarsel som besked

**Formål:**

* At øve dig i at sende alarmbesked ud til bruger (fx som email, Telegram eller anden besked).

**Krav:**

* Sæt flow op så en besked sendes, hvis en alarm aktiveres (brug fx “email”- eller “telegram”-node).

---

## 📋 Øvelse 5: Refleksion

**Formål:**

* At overveje, hvorfor alarmer er vigtige – og hvad der kan ske, hvis man ikke opdager problemer i tide.

**Krav:**

* Skriv kort om, hvilke situationer der kræver alarm/advarsel, og hvordan det kan hjælpe i virkeligheden.

---

### 📢 **Husk:**

* Alarmer gør det nemmere at spotte fejl – før det bliver dyrt eller farligt!
* Grænser kan altid justeres – prøv dig frem og se, hvad der giver mening for netop dit system.
* Du kan kombinere alarmer med logning fra dag 6, så du altid kan finde tilbage til, hvad der skete.
