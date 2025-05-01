# ❓ Workshop 3: Multiple Choice Quiz (25 spørgsmål med udvidede beskrivelser)

**Instruktion:** Vælg det mest korrekte svar til hvert spørgsmål. Kun ét svar er korrekt. Formålet med denne quiz er at teste din forståelse af centrale emner i Workshop 3, herunder netværkssikkerhed, MITM-angreb, TLS, logging, adgangskontrol og visualisering i IIOT-systemer.

---

### 1. Hvad står MITM for?
A. Message Integrity Transfer Model  
B. Man-in-the-Middle  
C. Multi Input Transmission Monitor  
D. Managed IoT Transport Mechanism

MITM er en forkortelse for Man-in-the-Middle og henviser til en type angreb, hvor en uautoriseret tredjepart placerer sig mellem to kommunikerende enheder for at aflytte eller manipulere data.

### 2. Hvad er formålet med et MITM-angreb?
A. At optimere systemets datastrømme  
B. At sniffe, opsnappe eller manipulere data mellem to parter  
C. At validere krypterede certifikater  
D. At synkronisere MQTT-topics

Angriberen forsøger at læse eller ændre data uden at nogen af de legitime parter opdager det.

### 3. Hvilken port bruger MQTT som standard (uden TLS)?
A. 8883  
B. 22  
C. 443  
D. 1883

Port 1883 er standardporten for MQTT uden kryptering. Ved TLS bruges ofte 8883.

### 4. Hvad gør TLS?
A. Øger netværkshastigheden  
B. Sender data til flere enheder samtidigt  
C. Krypterer og beskytter datatrafik mod MITM  
D. Gemmer data i lokal buffer

TLS (Transport Layer Security) sikrer, at data ikke kan læses eller manipuleres under overførsel.

### 5. Hvad er et typisk tegn på et MITM-angreb i et netværk?
A. Langsom login på systemet  
B. Dobbelte beskeder i loggen  
C. Forbindelser oprettes med forkerte certifikater  
D. MQTT stopper med at virke helt

Manglende tillid til certifikater og mærkelige netværksruter kan indikere MITM.

### 6. Hvad bruges ARP spoofing til i en MITM?
A. At ændre data i databasen  
B. At sende beskeder hurtigere  
C. At narre netværket til at sende trafik via angriberen  
D. At finde ud af MAC-adresser i databasen

Angriberen manipulerer ARP-tabellen, så trafik går igennem den forkerte maskine.

### 7. Hvilket værktøj brugte du til MITM-simuleringen?
A. Node-RED  
B. Wireshark  
C. Python GUI script  
D. Mosquitto monitor

Et færdiglavet Python-script med GUI blev brugt til at simulere MITM og vise opsnappet data.

### 8. Hvad sker der typisk med data, når TLS er aktiveret?
A. Det vises som uforståelige tegn for en angriber  
B. Det slettes automatisk efter 30 sekunder  
C. Det konverteres til JSON  
D. Det bliver mere læsbart

Kryptering gør det umuligt at forstå data uden den rette nøgle.

### 9. Hvad er en typisk indikator for, at TLS er aktivt i en MQTT-klient?
A. Port 1883 anvendes  
B. Der kræves brugernavn og adgangskode  
C. Klienten opretter forbindelse via port 8883  
D. Payload vises som XML

TLS-baseret MQTT kommunikerer oftest på port 8883.

### 10. Hvorfor bruger man adgangskontrol på MQTT-brokere?
A. For at forhindre tab af målinger  
B. For at forbedre datalagring  
C. For at styre, hvem der må publicere og abonnere  
D. For at vise beskeder i dashboard

Adgangskontrol begrænser systemadgang til autoriserede brugere.

### 11. Hvad er formålet med en fejllog?
A. At debugge JavaScript-funktioner  
B. At adskille fejl fra normal drift  
C. At vise temperaturmålinger  
D. At filtrere unødvendig trafik

Fejllogs gør det nemmere at analysere uregelmæssigheder og finde fejl i systemet.

### 12. Hvilken type data kunne opsnappes i et MITM-angreb før TLS?
A. Komprimerede billeder  
B. Brugerdata og måleværdier i klartekst  
C. Kun MAC-adresser  
D. Kun timestamps

I et ukrypteret netværk kan alle datapunkter ses af angriberen.

### 13. Hvordan ser du typisk forskel på TLS og ikke-TLS i MQTT?
A. Via payload-længde  
B. Via portnummer og certifikater  
C. Via antal forbindelser  
D. Via farve på MQTT-node

TLS bruges typisk på en anden port og kræver certifikater.

### 14. Hvad betyder det, hvis MITM ikke længere viser data efter TLS er aktiveret?
A. Scriptet er gået ned  
B. Payloads er nu krypteret og beskyttet  
C. Broker er gået offline  
D. MQTT er skiftet til HTTP

TLS skjuler indholdet, så det ikke kan læses selv ved aflytning.

### 15. Hvad er vigtigst at dokumentere efter et MITM-angreb?
A. Udseende af Node-RED flow  
B. Billedlayout i dashboard  
C. Payload og topics opsnappet samt tidspunkt  
D. Samlede datamængde

Dokumentation skal vise hvad der blev opsnappet, hvornår og hvordan.

### 16. Hvordan konfigurerer man adgangskontrol i Mosquitto?
A. I Node-RED  
B. Med TLS-noder  
C. Via `mosquitto_passwd`  
D. I mqtt-explorer GUI

`mosquitto_passwd` bruges til at oprette brugere og gemme adgangskoder.

### 17. Hvad er et selv-signeret certifikat?
A. Et certifikat fra Amazon  
B. Et midlertidigt password  
C. Et certifikat genereret uden en CA (Certificate Authority)  
D. Et billede med signatur

Selv-signerede certifikater bruges ofte til test og undervisning.

### 18. Hvad betyder det, hvis en MQTT-klient nægter adgang?
A. MQTT er ikke installeret  
B. Broker er forkert konfigureret  
C. TLS eller adgangskode er forkert  
D. Netværket er for langsomt

Fejl i certifikat eller loginoplysninger vil føre til afvisning.

### 19. Hvad er en fordel ved at logge til både fil og database?
A. Man får bedre farver i Node-RED  
B. Redundans og mulighed for forskellige analyser  
C. Det virker bedre med MQTT  
D. Det forhindrer fejl helt

Fil og database kan bruges til backup og forskellige analyser.

### 20. Hvad er formålet med at manipulere data i MITM-testen?
A. At forbedre sensorens præcision  
B. At måle svartid  
C. At vise hvor nemt det er at ændre payload  
D. At teste batterilevetid

Manipulation demonstrerer sårbarhed, når ingen kryptering er til stede.

### 21. Hvordan indikerer et dashboard normalt en fejl?
A. Grøn tekst  
B. Blå blink  
C. Rød farve eller ikon  
D. Gråt baggrundsbillede

Rød farve signalerer ofte noget kritisk eller alarmerende.

### 22. Hvad er vigtigst i en sikkerheds-visualisering?
A. At data er farverige  
B. At alle værdier vises samtidig  
C. At status fremstår tydeligt og letforståeligt  
D. At der er animationer

Det visuelle skal støtte hurtig beslutning og være let at afkode.

### 23. Hvad er et godt eksempel på en kritisk hændelse?
A. Temperatur stiger med 0.2 °C  
B. Kommunikation stopper uventet  
C. MQTT-topic ændrer navn  
D. Logfil vokser langsomt

Manglende kommunikation kan være tegn på alvorlig fejl eller angreb.

### 24. Hvorfor er refleksion vigtig i Workshop 3?
A. For at kunne genskabe flowet  
B. For at huske portnumre  
C. For at lære af angreb og forbedre sikkerheden  
D. For at kopiere certifikater

Refleksion sikrer, at erfaringer bruges til forbedringer fremadrettet.

### 25. Hvilket sikkerhedslag beskytter bedst mod MITM?
A. Gateway routing  
B. HTTP headers  
C. TLS-kryptering og autentifikation  
D. Ethernet-kabler

TLS sikrer dataintegritet og krypterer hele forbindelsen for at forhindre MITM.

