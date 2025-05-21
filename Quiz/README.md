## DLE - IIoT baseret dataopsamling quiz (Optimeret med plausibel svarvariation)

### Quiz Regler

* Du må gerne søge information på internettet for at finde svarene.
* Det er **ikke tilladt** at bruge AI-værktøjer eller få hjælp fra AI-assistenter.
* Du har den tid, som underviseren vurderer, til at besvare quizzen.
* Alle svar skal angives som én af mulighederne: **a, b, c eller d**.
* Svarene skal skrives tydeligt ud for hvert spørgsmål.
* Arbejd individuelt og overhold reglerne for fair play.

---

**1. Hvad står MQTT for?**
a) Message Queue Telemetry Transport  
b) Message Quality Telemetry Transfer  
c) Modular Queue Transfer Technique  
d) Machine Quick Telemetry Transfer  

**2. Hvad bruges en broker til i MQTT?**
a) At etablere klientforbindelser til skyen  
b) At håndtere emnebaseret datalogning  
c) At videresende beskeder mellem publishere og subscribere  
d) At sende heartbeat-signaler til klienter  

**3. Hvad er formålet med et sanity check på data?**
a) At vurdere dataens statistiske fordeling  
b) At bekræfte at data overholder definerede grænser  
c) At identificere semantiske afvigelser i kontekst  
d) At analysere datasammenhæng med fysiske modeller  

**4. Hvilket eksempel beskriver bedst et sanity check?**
a) En dobbeltregistrering i datasættet  
b) En værdi med høj standardafvigelse  
c) En temperaturværdi uden for det teknisk mulige interval  
d) En afvigelse ift. historisk middelværdi  

**5. Hvornår bør et sanity check udføres?**
a) Når data gemmes i backend-systemet  
b) Under rapportgenerering  
c) Umiddelbart ved modtagelse af data  
d) Efter en vis datapulje er samlet  

**6. Hvilken fordel er der ved at bruge IIoT i industrien?**
a) Lavere energiforbrug i netværkstopologi  
b) Øget gennemsigtighed og beslutningsstøtte via realtidsdata  
c) Øget afhængighed af menneskelig overvågning  
d) Reduktion af sensorvedligeholdelse  

**7. Hvad betyder "publish/subscribe" i MQTT?**
a) Et system hvor kun brokeren sender data direkte til databasen  
b) En metode hvor beskeder krypteres og valideres  
c) En model hvor klienter kan distribuere og abonnere på beskeder via topics  
d) En tilgang hvor alle klienter kommunikerer parvist  

**8. Hvilket Node-RED node bruges typisk til at modtage MQTT-beskeder?**
a) mqtt link  
b) mqtt in  
c) mqtt trigger  
d) mqtt stream  

**9. Hvordan kan man udføre et sanity check i Node-RED?**
a) Med en inject-node koblet til en debug-node  
b) Med en change-node koblet til UI-noder  
c) Med en switch-node med logik for beskedtype  
d) Med en function-node der evaluerer betingelser i JavaScript  

**10. Hvad er en plausibilitetstest i forbindelse med dataopsamling?**
a) En vurdering af om data harmonerer med fysisk eller kontekstuel forventning  
b) En kontrol mod hardwarefejl  
c) En filtrering af redundans  
d) En validering op mod datastruktur  

**11. Hvordan kan man visualisere data i Node-RED?**
a) Ved at eksportere flowet til JSON  
b) Med dashboard-noder som chart, gauge eller text  
c) Ved at bruge file-noder og hente data i Excel  
d) Med debug-noder koblet til function-noder  

**12. Hvilket lag i OSI-modellen arbejder MQTT primært på?**
a) Transportlaget  
b) Applikationslaget  
c) Netværkslaget  
d) Sessionlaget  

**13. Hvad er et "topic" i MQTT?**
a) En metode til at identificere klienter  
b) En kanal hvor beskeder distribueres efter emne  
c) En måde at kryptere beskeder på  
d) En JSON-struktur i payload  

**14. Hvordan sikrer man data i IIoT-systemer?**
a) Ved at udveksle nøgler uden kryptering  
b) Ved TLS-kryptering og adgangskontrol på enhedsniveau  
c) Ved at bruge dynamiske IP-adresser  
d) Ved at begrænse netværksadgang via subnetting alene  

**15. Hvilken af følgende er et eksempel på en sensor, der kan bruges i IIoT?**
a) Labelprinter med USB  
b) Temperaturføler med Modbus-grænseflade  
c) Ethernet-switch med SNMP  
d) HMI-panel med touch-funktion  

**16. Hvordan kan man sende data fra Node-RED til en MQTT-broker?**
a) Ved at anvende inject kombineret med debug-noden  
b) Ved at logge data til local storage  
c) Ved at bruge mqtt out-noden konfigureret med topic og payload  
d) Ved at bruge en http request-node med JSON  

**17. Hvad betyder QoS i MQTT?**
a) En standard for pakkestørrelser i netværk  
b) En grænseværdi for topic-længde  
c) En mekanisme til at definere leveringssikkerhed af beskeder  
d) En metode til datakryptering  

**18. Hvordan kan man overvåge en produktionslinje med IIoT?**
a) Ved at isolere netværket helt fra skyen  
b) Ved at kombinere sensorinputs med edge computing og visualisering  
c) Ved kun at bruge manuelle aflæsninger og tjeklister  
d) Ved at opsamle data uden nogen analyse  

**19. Hvad er en "payload" i MQTT-sammenhæng?**
a) En signaltype på TCP-niveau  
b) En måleværdi fra brokeren  
c) Det indhold, som transporteres i beskeden til abonnenten  
d) En kalibreringsparameter til sensorer  

**20. Hvilken ulempe kan der være ved trådløs dataopsamling?**
a) Bedre fysisk adgang til sensorer  
b) Øgede netværkshastigheder  
c) Risiko for interferens og ustabilt signal i industrielle miljøer  
d) Større kabelføringskompleksitet  

**21. Hvad bruges en gateway til i IIoT?**
a) At samle kabler i en fysisk boks  
b) At definere topologier i netværk  
c) At oversætte og forbinde forskellige kommunikationsprotokoller  
d) At etablere sensorparametre  

**22. Hvad betyder data drift?**
a) En gradvis forskydning i måledata uden ændringer i selve processen  
b) En variation forårsaget af samplingfejl  
c) En form for datatransformation fra edge til cloud  
d) Et tab af datapakker under netværksbelastning  

**23. Hvordan kan man opdage data drift i et IIoT-system?**
a) Ved at sætte MQTT QoS til 2   
b) Ved løbende statistisk analyse af trends over tid  
c) Ved at filtrere alle outliers automatisk  
d) Ved at begrænse dataudsendelse  

**24. Hvordan kan man beskytte IIoT-enheder mod cyberangreb?**
a) Ved at holde firmware opdateret og benytte firewalls samt kryptering  
b) Ved at bruge standardlogin for nem adgang  
c) Ved at isolere systemer helt uden adgang til internettet  
d) Ved at anvende ukrypterede forbindelser for hastighed  

**25. Hvad er forskellen på MQTT og HTTP?**
a) MQTT bruger publish/subscribe og er letvægts, mens HTTP bruger request/response og er tungere  
b) HTTP er optimeret til realtidskommunikation  
c) MQTT bruger sessionbaseret kommunikation, HTTP gør ikke  
d) Der er ingen funktionel forskel i moderne netværk  
