
# ❓ Workshop 6: Multiple Choice Quiz (25 spørgsmål)

**Instruktion:** Vælg det mest korrekte svar til hvert spørgsmål. Kun ét svar er korrekt. Quizzen dækker nøgleemner fra Workshop 6: Edge Computing, lokal behandling, pre-processing, thresholds, robusthed og anomali-detektion.

---

### 1. Hvad er hovedformålet med edge computing?
A. At bruge flere cloud-tjenester  
B. At reducere datalagring  
C. At behandle og reagere på data tæt på datakilden  
D. At filtrere al netværkstrafik

### 2. Hvad er typisk en fordel ved at køre beslutningslogik på edge?
A. Øget netværkstrafik  
B. Øget svartid  
C. Lokal autonomi og lavere latenstid  
D. Kræver konstant internetforbindelse

### 3. Hvad anvendes en `switch`-node til i Node-RED?
A. At skifte dashboardvisning  
B. At styre routing baseret på betingelser  
C. At gemme filer  
D. At måle latenstid

### 4. Hvad er en glidende gennemsnit (moving average)?
A. En metode til at skifte mellem dashboards  
B. En teknik til at udjævne og analysere trends i data  
C. En MQTT-protokol  
D. En netværksmåling

### 5. Hvad gør `rbe`-noden (report by exception)?
A. Rapporterer konstant  
B. Rapportere kun, når værdien ændrer sig  
C. Rapportere ved netværksfejl  
D. Bruges til at gemme konfiguration

### 6. Hvad betyder en threshold i et edge-flow?
A. En maksimal pakkestørrelse  
B. En betinget handling baseret på værdi  
C. Et sted hvor flowet pauser  
D. En MQTT-topic

### 7. Hvad sker der i et edge-system ved netværksfejl?
A. Systemet stopper helt  
B. Edge-systemet kan fortsætte lokalt  
C. Alle data slettes  
D. Der opstår en cloud-automatisk backup

### 8. Hvor vises lokal beslutningsstatus typisk i et dashboard?
A. `ui_slider`  
B. `ui_led` eller `ui_icon`  
C. `ui_form`  
D. `ui_camera`

### 9. Hvordan beregnes et simpelt gennemsnit?
A. Max værdi / min værdi  
B. Summer alle værdier og divider med antal  
C. Brug af z-score  
D. MQTT encode af data

### 10. Hvilket værktøj bruges typisk til at vise grafer over tid i Node-RED?
A. `ui_button`  
B. `ui_chart`  
C. `ui_table`  
D. `ui_code`

### 11. Hvad gør en `ui_toast`-node?
A. Afsender MQTT  
B. Viser en midlertidig pop-up besked  
C. Logger fejl  
D. Tæller datapakker

### 12. Hvilken enhed bruger man ofte som fysisk edge device?
A. Ethernet switch  
B. WiFi repeater  
C. Raspberry Pi eller industriel gateway  
D. Cloud-API

### 13. Hvordan gemmer man lokal data i fil i Node-RED?
A. Med `change`-node  
B. Med `mqtt-in`-node  
C. Med `file`-node i append mode  
D. Med `switch`-node

### 14. Hvornår bør man bruge edge frem for cloud?
A. Når data skal krypteres  
B. Når lokal reaktionstid er kritisk og netværket ustabilt  
C. Når internetadgang er garanteret  
D. Når man har en VPN

### 15. Hvordan beregner man forskel mellem to målinger?
A. log10(værdi)  
B. value * 2  
C. Math.abs(current - previous)  
D. value % 100

### 16. Hvad betyder “anomaly == true” i dit flow?
A. At systemet er i standby  
B. At værdien er under threshold  
C. At der er opdaget afvigelse  
D. At brugeren har trykket en knap

### 17. Hvad bruges `flow.set()` og `flow.get()` til?
A. Til at sende beskeder  
B. Til at gemme og hente lokal variabel i Node-RED  
C. Til at loope en MQTT-pakke  
D. Til at ændre farver i dashboard

### 18. Hvad gør en `ui_button` med en `context.set("alarm", false)`-funktion?
A. Slukker Node-RED  
B. Kvitterer en alarm  
C. Starter en ny flow-fil  
D. Logger sensorens ID

### 19. Hvorfor visualiserer man gennemsnit og rå data side om side?
A. For at fylde dashboardet  
B. For at vise sensorens IP  
C. For at analysere trends og opdage outliers  
D. For at sammenligne to MQTT-klienter

### 20. Hvad kan være en ulempe ved udelukkende at bruge cloud?
A. For høj CPU-brug  
B. Manglende strømforsyning  
C. Øget afhængighed af netværk og højere latenstid  
D. Øget sensorkalibrering

### 21. Hvilket datalogisk element indikerer robusthed?
A. Systemet genstarter ved fejl  
B. Systemet er afhængigt af JSON  
C. Systemet reagerer selvstændigt ved netværksnedbrud  
D. Systemet kræver VPN

### 22. Hvilken node logger beskeder til en tekstfil?
A. `debug`  
B. `ui_led`  
C. `file`  
D. `http-request`

### 23. Hvad er en fordel ved lokal anomali-detektion?
A. Højere cloud-beskyttelse  
B. Bedre MQTT-ydeevne  
C. Tidlig reaktion uden netværk  
D. Lavere opløsning

### 24. Hvad bruges glidende gennemsnit primært til?
A. Til at tælle alarmer  
B. Til at aktivere REST-kald  
C. Til at glatte målinger og opdage afvigelser  
D. Til at vælge MQTT-topic

### 25. Hvad skal en god edge-løsning kunne?
A. Kunne koble til flere UI-farver  
B. Køre kontinuerligt og tage beslutninger lokalt  
C. Kun virke med WiFi  
D. Sende 100% af data til skyen

