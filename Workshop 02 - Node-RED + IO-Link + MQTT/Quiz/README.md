# Quiz – Dag 2: IO-Link & MQTT

Her er en quiz med 25 spørgsmål, der tester din forståelse af IO-Link, MQTT, MQTT Explorer og MQTT over TLS fra dagens øvelser.

---

## 🔵 IO-Link & moneo (Spørgsmål 1-8)

**1. Hvad er formålet med ifm moneo | configure?**
A) At programmere PLC'er  
B) At konfigurere og overvåge IO-Link master og sensorer  
C) At installere Node-RED  
D) At analysere netværkstrafik

**2. Hvad skal du gøre for at PC og IO-Link master kan kommunikere?**
A) De skal bare være tændt  
B) De skal være i samme subnet  
C) De skal bruge forskellige IP-adresser på forskellige netværk  
D) Masteren behøver ingen IP-adresse

**3. Hvilken funktion i moneo bruges til at finde IO-Link master på netværket?**
A) Process data  
B) Network scan / Netværksscan  
C) Subscription  
D) Notification

**4. Hvad betyder det, hvis en port på IO-Link masteren har status "IO-Link"?**
A) Porten er deaktiveret  
B) Porten bruges til digital I/O  
C) Der er en aktiv IO-Link sensor forbundet  
D) Der er en fejl på porten

**5. Hvordan kan du se live processdata fra en IO-Link sensor i moneo?**
A) Via Network scan  
B) Via Process data / Live data fanen  
C) Via MQTT Explorer  
D) Via Node-RED

**6. Hvilket web-interface kan du bruge til at verificere IO-Link masterens konfiguration?**
A) `http://[master-IP]/web`  
B) `http://localhost:5000`  
C) `http://test.mosquitto.org`  
D) `http://moneo.ifm.com`

**7. Hvor konfigurerer du MQTT broker og topic i IO-Link masteren?**
A) Under Network scan  
B) Under Process data  
C) Under Notification → Consumer setup  
D) Under moneo | configure free license

**8. Hvad skal du gøre hvis masteren ikke dukker op i netværksscannet?**
A) Opgive og købe en ny master  
B) Tjekke 24V forsyning, subnet, firewall og kabel  
C) Genstarte computeren  
D) Deaktivere alle porte

---

## 🟢 MQTT i Node-RED (Spørgsmål 9-15)

**9. Hvad er MQTT, og hvad bruges det til i Node-RED?**
A) Et databaseformat  
B) En kommunikationsprotokol til pub/sub beskeder  
C) En type sensor  
D) En dashboard-komponent

**10. Hvilken node bruges til at modtage beskeder fra en MQTT-broker i Node-RED?**
A) MQTT-out  
B) MQTT-in  
C) Inject  
D) Debug

**11. Hvad er et "topic" i MQTT-sammenhæng?**
A) En type sensor  
B) En beskedtype  
C) En kanal/emne, hvor beskeder sendes og modtages (fx `test/io-link`)  
D) En dashboard-widget

**12. Hvordan kan du simulere IO-Link data i Node-RED, hvis du ikke har adgang til rigtig data?**
A) Med en Debug-node  
B) Med en Inject-node → JSON-node → MQTT-out  
C) Med en Switch-node  
D) Med en CSV-node

**13. Hvilken node bruges til at konvertere en JSON-streng til et JavaScript-objekt i Node-RED?**
A) CSV-node  
B) JSON-node (Convert to Object)  
C) Function-node alene  
D) Dashboard-node

**14. I en Function-node, hvordan tjekker du om metadata (timestamp, deviceId, status) er til stede?**
A) `if (msg.payload.timestamp && msg.payload.deviceId && msg.payload.status)`  
B) `if (msg.metadata.exists())`  
C) `if (msg.payload == true)`  
D) Med en Switch-node

**15. Hvilket format sendes IO-Link data oftest i via MQTT?**
A) CSV  
B) XML  
C) JSON  
D) HTML

---

## 🟡 MQTT Explorer (Spørgsmål 16-19)

**16. Hvad er formålet med MQTT Explorer?**
A) At programmere MQTT-brokers  
B) At debugge og monitorere MQTT-kommunikation i realtid  
C) At erstatte Node-RED  
D) At kryptere MQTT-beskeder

**17. Hvilken port bruges til ukrypteret MQTT-forbindelse?**
A) 8883  
B) 443  
C) 1883  
D) 5000

**18. Hvad kan du se i MQTT Explorer når du forbinder til en public broker som test.mosquitto.org?**
A) Kun dine egne beskeder  
B) Alle beskeder på alle topics (ingen kryptering!)  
C) Kun krypterede beskeder  
D) Ingen beskeder

**19. Hvordan publicerer du en besked i MQTT Explorer?**
A) Via Node-RED alene  
B) Ved at angive topic og payload, derefter trykke publish  
C) Med en Inject-node  
D) Det er ikke muligt

---

## 🔴 MQTT over TLS (Spørgsmål 20-25)

**20. Hvad står TLS for?**
A) Total Link Security  
B) Transport Layer Security  
C) Trusted Login System  
D) Topic Layer Service

**21. Hvad er den primære fordel ved at bruge MQTT over TLS?**
A) Hurtigere datatransmission  
B) Kryptering af data og beskyttelse mod MITM-angreb  
C) Mindre dataforbrug  
D) Bedre dashboard visualisering

**22. Hvad er et MITM-angreb (Man-in-the-Middle)?**
A) En type sensor  
B) Et angreb hvor en angriber opsnapper data mellem klient og broker  
C) En sikker kommunikationsmetode  
D) En type MQTT topic

**23. Hvordan sendes data når MQTT bruges UDEN TLS (port 1883)?**
A) Krypteret med AES  
B) I klartekst (kan læses af alle)  
C) Komprimeret  
D) Som binær data

**24. Hvilken port bruges typisk til MQTT over TLS?**
A) 1883  
B) 8883  
C) 443  
D) 80

**25. Hvad bruges digitale certifikater til i MQTT over TLS?**
A) At gøre kommunikationen langsommere  
B) At autentificere broker og klient, samt etablere kryptering  
C) At formatere JSON data  
D) At erstatte topics

---

## ✅ Facit

1. B (Konfigurere og overvåge IO-Link)
2. B (Samme subnet)
3. B (Network scan)
4. C (Aktiv IO-Link sensor)
5. B (Process data / Live data)
6. A (`http://[master-IP]/web`)
7. C (Notification → Consumer)
8. B (Tjek forsyning, subnet, firewall)
9. B (Pub/sub protokol)
10. B (MQTT-in)
11. C (Kanal/emne)
12. B (Inject → JSON → MQTT-out)
13. B (JSON-node)
14. A (if statement check)
15. C (JSON)
16. B (Debug og monitorere MQTT)
17. C (1883)
18. B (Alle beskeder - ingen kryptering!)
19. B (Topic + payload + publish)
20. B (Transport Layer Security)
21. B (Kryptering og MITM beskyttelse)
22. B (Angreb der opsnapper data)
23. B (I klartekst)
24. B (8883)
25. B (Autentificering og kryptering)
