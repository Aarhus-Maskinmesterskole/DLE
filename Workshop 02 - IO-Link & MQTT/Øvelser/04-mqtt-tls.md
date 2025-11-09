# Hvad er MQTT over TLS?
MQTT over TLS (Transport Layer Security) er en metode til at sikre kommunikation mellem MQTT-klienter og -brokere ved at kryptere data, der sendes over netværket. TLS beskytter mod aflytning, manipulation og forfalskning af data, hvilket er afgørende i industrielle IoT-applikationer, hvor følsomme oplysninger ofte overføres.

## Hvorfor bruge MQTT over TLS?
1. **Sikkerhed**: TLS krypterer data, hvilket beskytter mod uautoriseret adgang og sikrer dataintegritet.
2. **Autentificering**: TLS understøtter brugen af digitale certifikater, som kan bekræfte identiteten af både klienter og brokere.
3. **Overholdelse af standarder**: Mange industrier kræver kryptering for at overholde sikkerhedsstandarder og regulativer.
4. **Beskyttelse mod angreb**: TLS hjælper med at beskytte mod forskellige netværksangreb, såsom man-in-the-middle-angreb.

## Hvad er MITM-angreb?
Man-in-the-Middle (MITM) angreb er en type cyberangreb, hvor en angriber placerer sig mellem to kommunikerende parter (f.eks. en MQTT-klient og en broker) for at opsnappe, ændre eller manipulere de data, der udveksles. Uden kryptering kan angriberen læse følsomme oplysninger eller indsætte skadelig data i kommunikationen. TLS beskytter mod MITM-angreb ved at kryptere kommunikationen og sikre, at begge parter er autentiske.

### Hvordan opsnappes data uden TLS?
Uden TLS sendes data i klartekst over netværket, hvilket betyder, at enhver, der har adgang til netværkstrafikken (f.eks. via en Wi-Fi sniffer som Wireshark eller en kompromitteret router), kan læse og potentielt ændre de data, der sendes mellem MQTT-klienten og brokeren.

![alt text](image-3.png)

Figuren ovenfor illustrerer et MITM-angreb, hvor en angriber opsnapper og potentielt kan manipulere data, der sendes mellem en MQTT-klient og en broker uden TLS. Så længe at angriberen kan opsnappe trafikken så kan han se `Source`, `Destination` og `Payload` i klartekst og kan selv nu publicere beskeder til broker'en som om han var den oprindelige klient.

## Hvordan fungerer MQTT over TLS?
1. **Certifikater**: Både MQTT-brokeren og klienterne bruger digitale certifikater til at etablere en sikker forbindelse. Certifikaterne udstedes af en betroet certificeringsmyndighed (CA).
2. **Håndtryk**: Når en klient opretter forbindelse til en broker, gennemføres et TLS-håndtryk, hvor de udveksler certifikater og aftaler krypteringsparametre.
3. **Kryptering**: Når forbindelsen er etableret, krypteres alle data, der sendes mellem klienten og brokeren, hvilket sikrer, at kun de autoriserede parter kan læse dem.
4. **Integritet**: TLS sikrer også dataintegritet ved at bruge meddelegeringskoder, som hjælper med at opdage eventuelle ændringer i data under overførslen.
## Implementering af MQTT over TLS
For at implementere MQTT over TLS skal følgende trin følges:
1. **Vælg en MQTT-broker, der understøtter TLS**: Sørg for, at den broker, du bruger, har TLS aktiveret. Dette kan være en offentlig broker eller en selvhostet løsning.
2. **Konfigurer certifikater**: Generer eller få fat i de nødvendige digitale certifikater til både klienten og broker'en. Dette inkluderer en CA (Certificate Authority) certifikat, samt eventuelle klientcertifikater.
3. **Opdater klientindstillinger**: Juster MQTT-klientens konfiguration for at bruge TLS. Dette kan inkludere at angive stien til certifikaterne og aktivere TLS i klientbiblioteket.
4. **Test forbindelsen**: Opret forbindelse til broker'en ved hjælp af den opdaterede klientkonfiguration og verificer, at forbindelsen er sikker.
