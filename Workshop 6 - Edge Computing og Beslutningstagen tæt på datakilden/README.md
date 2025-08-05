## 📊 Workshop 6: Gem dine målinger

### 🌟 **Formål**

* At lære, hvordan du kan **gemme dine IIoT-målinger** i en fil (fx CSV eller regneark) i Node-RED.
* At kunne **finde gamle målinger** frem igen og se, om der har været fejl, ændringer eller mønstre over tid.
* At forstå, hvorfor logning og historik er vigtigt i “den virkelige verden”.

---

### 👩‍💻 **Kompetencer du opbygger**

Efter workshoppen kan du:

* Sende data fra Node-RED til en log-fil eller et simpelt regneark.
* Åbne og læse gamle målinger, fx i Excel eller Google Sheets.
* Finde fejl, outliers eller gentagende mønstre i dine historiske data.
* Forklare for andre, hvorfor det er smart at logge data – og hvordan man gør det enkelt.

---

### 📚 **Introduktion**

I dag går vi fra at vise data **her og nu** – til at **samle dem op og gemme dem**, så du altid kan kigge tilbage.
Du vil kunne se, om der har været fejl (fx for høj temperatur), gentagelser eller udviklinger, og du kan analysere dine data i et regneark.

---

## 📋 Øvelse 1: Gem målinger i en CSV-fil

**Formål:**

* At sende målinger fra Node-RED til en tekstfil i CSV-format (komma-adskilt).

**Krav:**

* Brug “file”-node i Node-RED til at gemme fx temperatur, tid og status på én linje hver gang der kommer nye data.

---

## 📋 Øvelse 2: Åbn og kig på din log-fil

**Formål:**

* At kunne åbne din fil i fx Excel, Google Sheets eller Notepad og se dine målinger over tid.

**Krav:**

* Find eksempler på fejl (fx for høj/lav værdi), gentagelser eller ændringer i data.
* Marker mindst ét mønster eller fejl, du har fundet.

---

## 📋 Øvelse 3: Udvid loggen med mere information

**Formål:**

* At gøre loggen endnu mere nyttig ved at tilføje flere felter (fx dato, alarmstatus, navn på målepunkt).

**Krav:**

* Udvid CSV-filen så hver række indeholder fx tid, måling, status og evt. enhed/ID.

---

## 📋 Øvelse 4: Refleksion – hvorfor logge data?

**Formål:**

* At overveje og forklare, hvorfor det er vigtigt at have historiske data i industrien, hjemme eller i skolen.

**Krav:**

* Skriv eller fortæl kort, hvad du kan bruge gamle data til (fx fejlfinding, rapportering, dokumentation, optimering).

---

### 📢 **Husk:**

* CSV-filer er lette at lave og kan åbnes på næsten alle computere.
* Hvis du vil prøve at logge til en database (fx SQLite), så spørg underviseren – det er næste skridt, men CSV er rigeligt til at starte med!
* Gode logs kan vise dig *alt*, hvad der er sket – også hvis ingen så det live.
