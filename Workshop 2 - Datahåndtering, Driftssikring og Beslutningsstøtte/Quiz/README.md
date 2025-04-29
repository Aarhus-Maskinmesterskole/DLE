# 🏆 Workshop 2: Multiple Choice Quiz (25 spørgsmål)

**Spørgsmål 1:**  
Hvad er formålet med et sanity-check i datastrømme?  
A) At gemme alle data uanset kvalitet  
B) At validere om data ligger inden for forventede grænser  
C) At sende data direkte til cloud  
D) At komprimere data

---

**Spørgsmål 2:**  
Hvad bruges en watchdog til i IIOT-systemer?  
A) At analysere statistiske data  
B) At overvåge datastrømmens tilstedeværelse  
C) At visualisere dashboardet  
D) At gemme data til database

---

**Spørgsmål 3:**  
Hvad kaldes det, når en datastrøm stopper uventet?  
A) Drift  
B) Alarmhåndtering  
C) Datastrømsbrud  
D) Protokoloverførsel

---

**Spørgsmål 4:**  
Hvilken node i Node-RED kan bruges til at opdage datastrømstop?  
A) delay  
B) trigger  
C) http-request  
D) join

---

**Spørgsmål 5:**  
Hvad skal inkluderes som metadata i en datastrøm?  
A) Source, unit, timestamp, status  
B) Payload size og CRC  
C) Servernavn og IP adresse  
D) Brugeragent og cookies

---

**Spørgsmål 6:**  
Hvorfor er timestamp vigtigt i IIOT-data?  
A) For at kunne sortere data kronologisk  
B) For at skjule data  
C) For at kryptere beskeden  
D) For at øge hastigheden

---

**Spørgsmål 7:**  
Hvad bruges en function-node typisk til i sanity-check flows?  
A) At lave tidsstempler  
B) At filtrere og validere data  
C) At lagre filer  
D) At opsætte grafiske dashboards

---

**Spørgsmål 8:**  
Hvorfor logger man data til både CSV og SQLite samtidigt?  
A) For at reducere lagerplads  
B) For redundans og fleksibilitet  
C) For at bruge mindre RAM  
D) For at øge kompleksiteten

---

**Spørgsmål 9:**  
Hvilken struktur bruges typisk i en CSV-logfil?  
A) JSON  
B) SQL  
C) Kommaseparerede værdier  
D) XML-tags

---

**Spørgsmål 10:**  
Hvilken node bruges til at skrive direkte til en CSV-fil i Node-RED?  
A) file  
B) inject  
C) switch  
D) mqtt-in

---

**Spørgsmål 11:**  
Hvordan kan fejl adskilles fra normale målinger i et flow?  
A) Ved at bruge statusfeltet i metadata  
B) Ved at ændre IP-adressen  
C) Ved at ændre TCP-porten  
D) Ved at fjerne payload

---

**Spørgsmål 12:**  
Hvordan kan en fejllog separeres i Node-RED?  
A) Ved at filtrere på payload-værdi  
B) Ved at sortere på source  
C) Ved at filtrere på status "Error" eller "Warning"  
D) Ved at bruge random nodes

---

**Spørgsmål 13:**  
Hvad gemmes typisk i en fejllog?  
A) Kun gode målinger  
B) IP-adresser  
C) Timestamp, source, fejlbeskrivelse, severity  
D) Programkode

---

**Spørgsmål 14:**  
Hvilken node bruges til at samle flere beskeder over tid?  
A) join  
B) split  
C) rbe  
D) http-request

---

**Spørgsmål 15:**  
Hvilken metode kan bruges til at udregne gennemsnitstemperaturen fra flere datapunkter?  
A) RBE node  
B) Gennemsnitsberegning i en function-node  
C) HTTP API-kald  
D) Random data generator

---

**Spørgsmål 16:**  
Hvordan træffes beslutninger baseret på aggregerede data?  
A) Direkte fra rå målinger  
B) Ved at analysere trends som gennemsnit, min, max  
C) Ved at filtrere IP-adresser  
D) Ved at lave login-checks

---

**Spørgsmål 17:**  
Hvordan konfigureres en alarm i Node-RED?  
A) Ved at sende SMS direkte  
B) Ved at bruge templates med baggrundsfarver  
C) Ved at gå udenom dashboard  
D) Ved at bruge FTP

---

**Spørgsmål 18:**  
Hvilken node kan bruges til at skifte baggrundsfarve dynamisk?  
A) template  
B) switch  
C) delay  
D) mqtt-in

---

**Spørgsmål 19:**  
Hvad skal ske, hvis gennemsnitlig temperatur overstiger en grænseværdi?  
A) Afvis alle målinger  
B) Generere en alarm eller advarsel  
C) Logge alt i sorteret rekkefølge  
D) Starte en backupserver

---

**Spørgsmål 20:**  
Hvorfor bruges trigger noder i watchdog flows?  
A) For at skabe JSON-objekter  
B) For at fange manglende datastrøm  
C) For at kalde REST API'er  
D) For at lave OPC UA-certifikater

---

**Spørgsmål 21:**  
Hvordan kan et dashboard vise "OK", "Warning" og "Error" status?  
A) Ved at bruge random farver  
B) Ved at kode farver ud fra metadata-status  
C) Ved at slette flows  
D) Ved at eksportere data

---

**Spørgsmål 22:**  
Hvordan adskiller man warnings fra kritiske fejl i flowet?  
A) På baggrund af topic navn  
B) På baggrund af severity felter  
C) På baggrund af source IP  
D) Ved at ændre TCP timeout

---

**Spørgsmål 23:**  
Hvad kan bruges til at lave en visuel alarm på dashboardet?  
A) file-node  
B) template-node med farveskift  
C) sqlite-node  
D) inject-node

---

**Spørgsmål 24:**  
Hvad kan forårsage en watchdog-alarm?  
A) Overbelastning på MQTT broker  
B) Datastrøm stopper med at sende nye beskeder  
C) Forkert API-key  
D) Forkert timestamp

---

**Spørgsmål 25:**  
Hvordan skal en alarm logges, hvis severity er "Critical"?  
A) I en separat critical_log.csv  
B) I main database uden skelnen  
C) I random-access memory  
D) I browserens cache

---
