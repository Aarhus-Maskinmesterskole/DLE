# ❓ Workshop 4: Multiple Choice Quiz (25 spørgsmål)

**Instruktion:** Vælg det mest korrekte svar til hvert spørgsmål. Kun ét svar er korrekt. Quizzen dækker nøgleemner fra Workshop 4 om interoperabilitet, OPC UA, MQTT og Sparkplug B.

---

### 1. Hvad betyder semantisk interoperabilitet?
A. At data sendes hurtigt nok  
B. At data kan forstås og tolkes korrekt af modtageren  
C. At data komprimeres med semantisk algoritme  
D. At systemer bruger samme IP-adresse

### 2. Hvilken protokol har indbygget understøttelse for hierarki og datamodeller?
A. HTTP  
B. MQTT  
C. OPC UA  
D. Modbus

### 3. Hvad er et typisk eksempel på rå data?
A. { "value": 23.4, "unit": "°C" }  
B. "23.4"  
C. { "temperature": { "value": 23.4 } }  
D. [ 23.4, 24.1 ]

### 4. Hvad står OPC i OPC UA for?
A. Open Protocol Communication  
B. Open Platform Control  
C. OLE for Process Control  
D. Operator Protocol Converter

### 5. Hvad bruges MQTT normalt til?
A. Tidsstyret databaseret styring  
B. Public/Subscribe-baseret dataoverførsel  
C. Video-streaming over WiFi  
D. Access control

### 6. Hvad tilføjer Sparkplug B til MQTT?
A. Multiplexet dataoverførsel  
B. Semantisk struktur og payload standardisering  
C. Automatisk datapakke-kryptering  
D. REST-baseret kommunikation

### 7. Hvilket format bruger Sparkplug B typisk til sine payloads?
A. XML  
B. CSV  
C. JSON  
D. Protobuf (Binary)

### 8. Hvilket element findes i en Sparkplug topic-struktur?
A. /home/data/temp  
B. spBv1.0/group/DDATA/edge/device  
C. mqtt://client/node  
D. opc.tcp://localhost:4840

### 9. Hvad repræsenterer en metric i Sparkplug B?
A. Et XML-tag  
B. En enhedskonfiguration  
C. Et enkelt datapunkt med metadata  
D. Et måleinstrument

### 10. Hvilken type af besked sender en enhed ved opstart i Sparkplug B?
A. NBIRTH  
B. NDEATH  
C. HELLO  
D. INIT

### 11. Hvad er et node-id i OPC UA?
A. Enheds IP-adresse  
B. En unik identifikator for en datapunkt i namespace  
C. En gateway MAC-adresse  
D. En navngivet database

### 12. Hvordan visualiseres data typisk i Node-RED?
A. Ved brug af `ui_template`-noder  
B. Ved brug af `http-in`-noder  
C. Ved brug af `debug`-vindue  
D. Ved brug af `sql-out`-noder

### 13. Hvad er en fordel ved at bruge semantik i din datamodel?
A. Mindre hukommelsesforbrug  
B. Højere hastighed  
C. Mere meningsfulde data, der er lettere at genbruge  
D. Mere kompliceret dokumentation

### 14. Hvad er forskellen på syntaktisk og semantisk interoperabilitet?
A. Der er ingen forskel  
B. Syntaktisk = struktur, semantisk = betydning  
C. Semantisk = hurtigere  
D. Syntaktisk = kun tekst, semantisk = grafik

### 15. Hvad kaldes det, når man kombinerer flere datapunkter i ét dashboard?
A. Join  
B. Merge  
C. Link  
D. Stack

### 16. Hvilken type data vil du typisk visualisere i et IIOT-dashboard?
A. Sensorstatus, målinger og alarmer  
B. Videoovervågning  
C. Brugerinput og logins  
D. Netværksbåndbredde

### 17. Hvorfor bruges `function`-noder i Node-RED?
A. Til at oprette nye MQTT-forbindelser  
B. Til at definere adgangskontrol  
C. Til at transformere og berige payloads  
D. Til at sortere data alfabetisk

### 18. Hvad står "UA" for i OPC UA?
A. Unified Architecture  
B. Universal Application  
C. User Assignment  
D. UDP Adapter

### 19. Hvad bruges `ui_gauge` til i Node-RED-dashboard?
A. At sende e-mails  
B. At oprette Sparkplug metrics  
C. At vise målinger visuelt  
D. At generere SQL-forespørgsler

### 20. Hvad repræsenterer "DDATA" i Sparkplug?
A. Data om deviceens død  
B. Device-baseret historik  
C. En periodisk opdatering af enhedens målinger  
D. Diagnose af netværket

### 21. Hvad gør en `join`-node i Node-RED?
A. Kombinerer flere flow-filer  
B. Samler beskeder fra flere kilder i én payload  
C. Deler en besked i flere dele  
D. Udfører logning af flow

### 22. Hvad bruger man typisk en `ui_table` til?
A. At sende data til cloud  
B. At vise flere datapunkter i overskuelig form  
C. At oprette node-id’er  
D. At eksportere flows til PDF

### 23. Hvilken metode er mest semantisk stærk i IIOT?
A. Ren MQTT  
B. OPC UA  
C. CSV-logning  
D. TCP-sockets

### 24. Hvordan angiver du enhed og datatype i Sparkplug?
A. I emne-navnet  
B. I JSON-header  
C. Som attribut i hver metric  
D. Via brokerens konfiguration

### 25. Hvorfor er interoperabilitet vigtig i IIOT?
A. For at spare strøm  
B. For at alle systemer kan samarbejde effektivt og forstå hinanden  
C. For at opnå redundans  
D. For at mindske opdateringsfrekvensen

