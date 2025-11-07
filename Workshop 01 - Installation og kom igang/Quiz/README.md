# Node-RED Quiz

Her er en quiz med 20 spørgsmål, der dækker de emner og opgaver, I har arbejdet med i Node-RED (basics og advanced):

---

## 🟢 Basale Noder (Spørgsmål 1-10)

**1. Hvad bruges en Inject-node til i Node-RED?**
A) At vise data på dashboardet  
B) At sende beskeder ind i flowet (fx "Hello World", tal eller timestamp)  
C) At gemme data i en fil  
D) At konvertere data til JSON

**2. Hvilken node bruges til at vise beskeder og data under udvikling?**
A) Function-node  
B) Debug-node  
C) Switch-node  
D) Join-node

**3. I en Debug-node kan du vise output direkte under noden. Hvad skal du gøre?**
A) Klikke på Deploy  
B) Enable "node-status (32 characters)"  
C) Tilføje en Function-node  
D) Bruge en Template-node

**4. I en Function-node, hvordan ændrer du beskeden til "Du har trykket på knappen!"?**
A) `msg.payload = "Du har trykket på knappen!"`  
B) `return "Du har trykket på knappen!"`  
C) `console.log("Du har trykket på knappen!")`  
D) `msg.text = "Du har trykket på knappen!"`

**5. Hvad gør en Change-node?**
A) Samler beskeder  
B) Ændrer indholdet af en besked (fx msg.payload eller tilføjer nye felter)  
C) Deler arrays op  
D) Viser data i Debug

**6. Hvilken node bruges til at fordele beskeder baseret på betingelser (fx om et tal er større eller mindre end 5)?**
A) Function-node  
B) Split-node  
C) Switch-node  
D) Delay-node

**7. Hvad bruges en Template-node til?**
A) At formatere beskeder med placeholders (fx "Hej {{payload}}!")  
B) At konvertere JSON til CSV  
C) At gemme data i en fil  
D) At samle beskeder

**8. Hvordan installerer du `node-red-dashboard` paletten?**
A) Via kommandolinjen  
B) Via menuen → Manage palette → Install  
C) Ved at redigere package.json  
D) Det er indbygget i Node-RED

**9. Hvad bruges Link-in og Link-out noder til?**
A) At forbinde noder uden at trække ledninger direkte mellem dem  
B) At vise data i dashboardet  
C) At gemme data i en fil  
D) At konvertere data til JSON

**10. Hvad gør en Delay-node?**
A) Forsinker beskeder med en bestemt tid (fx 5 sekunder)  
B) Sender beskeder hurtigere  
C) Konverterer data til JSON  
D) Viser data i Debug

---

## 🟠 Avancerede Noder (Spørgsmål 11-20)

**11. Hvad gør en CSV-node?**
A) Konverterer mellem CSV-format og JSON  
B) Kun læser CSV-filer  
C) Kun skriver CSV-filer  
D) Viser CSV-data i dashboardet

**12. Hvad gør en Split-node?**
A) Samler flere beskeder til én  
B) Deler en array op i enkeltbeskeder  
C) Konverterer data til CSV  
D) Læser data fra en fil

**13. Hvilken node bruges til at samle flere beskeder til én samlet besked efter en Split-node?**
A) Template-node  
B) Join-node (i 'manual mode')  
C) Change-node  
D) Switch-node

**14. Hvordan laver du en HTML-tabel fra en array af objekter i Node-RED?**
A) Med en CSV-node  
B) Med en Template-node og HTML-kode (fx `<table>` med `{{#payload}}`)  
C) Med en Debug-node  
D) Med en Function-node alene

**15. Hvilken node bruges til at konvertere en JSON-tekststreng til et JavaScript-objekt?**
A) CSV-node  
B) JSON-node (Convert to Object)  
C) Template-node  
D) Split-node

**16. Hvad gør en Write File-node?**
A) Læser data fra en fil  
B) Skriver data til en fil (append eller overwrite)  
C) Viser data i Debug  
D) Konverterer data til CSV

**17. Hvad gør en Read File-node?**
A) Skriver data til en fil  
B) Læser data fra en fil og sender indholdet videre i flowet  
C) Samler beskeder  
D) Konverterer data til JSON

**18. I en JSON-node, hvordan konverterer du et objekt til en JSON-streng?**
A) Vælg 'Convert to Object'  
B) Vælg 'Convert to String'  
C) Brug en CSV-node  
D) Brug en Template-node

**19. Hvad bruges en Trigger-node til?**
A) At sende en besked (fx "Start") og derefter en anden besked (fx "Stop") efter en vis tid  
B) At forsinke beskeder  
C) At konvertere data til CSV  
D) At læse data fra en fil

**20. Hvilken kombination af noder bruges til at dele en array op og derefter samle den igen?**
A) Inject → Debug  
B) Split → Join  
C) CSV → JSON  
D) Read File → Write File

---

## ✅ Facit

1. B
2. B
3. B
4. A
5. B
6. C
7. A
8. B
9. A
10. A
11. A
12. B
13. B
14. B
15. B
16. B
17. B
18. B
19. A
20. B
