# ❓ Workshop 5: Multiple Choice Quiz (25 spørgsmål)

**Instruktion:** Vælg det mest korrekte svar til hvert spørgsmål. Kun ét svar er korrekt. Quizzen dækker nøgleemner fra Workshop 5: UNS, emnestruktur, OPC UA, Sparkplug B og Node-RED.

---

### 1. Hvad er hovedformålet med et Unified Namespace (UNS)?
A. At kryptere al MQTT-trafik  
B. At samle alle datastrømme i ét struktureret hierarki  
C. At forbinde OPC UA direkte til SCADA  
D. At komprimere data til lav båndbredde

### 2. Hvilket element indgår typisk i et UNS-emnehierarki?
A. IP-adresse  
B. PLC-serienummer  
C. Site, area, line, device, datapunkt  
D. Kun datapunktsnavn

### 3. Hvad står "spBv1.0" for i et Sparkplug B-topic?
A. Sparkplug version 1.0  
B. Specialized broker v1.0  
C. Semantic protocol B layer 1  
D. Structured process binding

### 4. Hvad bruges Node-RED's `function`-node typisk til i UNS-mapping?
A. At sende e-mails  
B. At tildele IP-adresser  
C. At transformere og strukturere payloads  
D. At gemme flows som backup

### 5. Hvad er et "NodeId" i OPC UA?
A. Et ID til at finde specifikke MQTT-klienter  
B. En pointer til datapunkter i OPC UA's namespace  
C. En adgangskode til UA-serveren  
D. Et serienummer på en PLC

### 6. Hvad er en typisk beskedtype i Sparkplug B?
A. CONNECT  
B. NBIRTH / DDATA / DDEATH  
C. OPC_READ  
D. JSON_PUSH

### 7. Hvad bør et emne i UNS **ikke** indeholde?
A. Fysisk placering  
B. Navn på sensor  
C. Random forkortelser uden konvention  
D. Enhedens funktion

### 8. Hvilken Node-RED-node bruges til at visualisere målinger som analog visning?
A. `ui_table`  
B. `ui_gauge`  
C. `debug`  
D. `ui_button`

### 9. Hvorfor bruger man `timestamp` i UNS-data?
A. For at kunne trace målingernes alder  
B. For at aktivere alarmer  
C. For at tælle datapakker  
D. For at kryptere datapunktet

### 10. Hvad sker der, hvis to sensorer sender til samme emne i UNS uden koordinering?
A. Data bliver automatisk flettet  
B. Systemet opdager det og blokerer  
C. Der kan opstå datakonflikter  
D. Begge sensorer logger sig ud

### 11. Hvordan navngiver man typisk emner i UNS?
A. CamelCase  
B. snake_case  
C. UPPERCASE  
D. Nummerering med dato

### 12. Hvad bruges `ui_led` eller `ui_icon` til i Node-RED-dashboard?
A. At vise sensorens MAC-adresse  
B. At vise numeriske værdier  
C. At indikere status eller alarmer  
D. At konfigurere MQTT

### 13. Hvad er forskellen på OPC UA og Sparkplug B?
A. OPC UA er tekstbaseret, Sparkplug B er binær  
B. OPC UA er pub/sub, Sparkplug B er client/server  
C. OPC UA bruger REST, Sparkplug bruger WebSocket  
D. De understøtter nøjagtig samme struktur

### 14. Hvad gør en `join`-node i Node-RED?
A. Kombinerer payloads fra flere input i ét objekt  
B. Giver adgang til SCADA  
C. Downloader data fra broker  
D. Deaktiverer en MQTT-klient

### 15. Hvorfor skal man dokumentere sin UNS-struktur?
A. Så man kan publicere den online  
B. For at opfylde ISO 9001  
C. For at andre kan forstå, udvikle og vedligeholde systemet  
D. Fordi Node-RED kræver det

### 16. Hvad er et typisk problem ved flade emnestrukturer?
A. For mange målinger per emne  
B. Manglende hierarki og kontekst  
C. Brug af for mange dataformater  
D. Dårlig MQTT-båndbredde

### 17. Hvilken node bruges til at sende UNS-data videre i MQTT?
A. `mqtt-out`  
B. `inject`  
C. `change`  
D. `tcp-request`

### 18. Hvordan kan man sikre semantisk tydelighed i emner?
A. Ved at bruge forskellige sprog  
B. Ved at følge et hierarkisk navnesystem med konventioner  
C. Ved at bruge GUID’er  
D. Ved at hardkode sensornavne

### 19. Hvad er en fordel ved at samle alle protokoller i ét UNS?
A. Større it-sikkerhed  
B. Mindre fysisk støj  
C. Mere ensartet datatilgang og bedre skalerbarhed  
D. Lavere strømforbrug

### 20. Hvad skal et godt dashboard gøre?
A. Vise al rå data samtidigt  
B. Tilbyde enkle, forståelige visninger med status og værdi  
C. Lade brugeren ændre datapunkter  
D. Gemme alle datapakker lokalt

### 21. Hvad gør `ui_chart` i Node-RED?
A. Importerer flow fra OPC UA  
B. Viser historik for et datapunkt over tid  
C. Filtrerer dubletter  
D. Logger data i PostgreSQL

### 22. Hvad er vigtigt ved mapping af data til UNS?
A. At payload er mindst mulig  
B. At data transformeres så det matcher strukturen og giver mening  
C. At flow er i farver  
D. At enhed og datatype gemmes i emnetavlen

### 23. Hvad bør et datapunkt i UNS altid inkludere?
A. IP-adresse  
B. En kompressor  
C. En timestamp og enhed (unit)  
D. En fysisk sensor

### 24. Hvordan visualiserer man fejlstatus i UNS?
A. Ved brug af MQTT Explorer  
B. Med blinkende `ui_led` eller farvekoder  
C. Med en switch-node  
D. Med script i Excel

### 25. Hvordan evalueres en UNS bedst?
A. Gennem random tests  
B. Ved at måle visualiseringshastighed  
C. Ved at analysere struktur, semantik og skalerbarhed  
D. Via Google søgning

