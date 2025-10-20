# README – Dag 2: IO-Link & MQTT

## Formål
På denne dag lærer du at arbejde med MQTT i Node-RED og at hente, parse og bruge data fra en IO-Link enhed, der sender data via MQTT. Du får praktisk erfaring med at forbinde til en MQTT-broker, modtage og simulere IO-Link data, samt validere og visualisere data i Node-RED.

## Læringsmål
- Forstå hvad MQTT er, og hvordan det bruges i Node-RED
- Kunne forbinde til en MQTT-broker og abonnere på topics
- Modtage og vise IO-Link data i Node-RED
- Parse og validere JSON-data fra IO-Link sensorer
- Håndtere metadata og statusinformation
- Simulere IO-Link data hvis rigtig data ikke er tilgængelig

## Opgaver
Se filen `mqtt-io-link.md` for detaljerede step-by-step øvelser:

1. Opret forbindelse til en MQTT-broker og send/modtag testbeskeder
2. Modtag og vis IO-Link data fra MQTT
3. Parse og brug IO-Link data i Dashboard
4. Tjek for metadata og statusinformation i sensordata
5. Simuler IO-Link data hvis du ikke har adgang til rigtig data

## Tips
- Brug Debug-noder flittigt for at se hvad der sker i flowet
- Husk at deploye flowet efter ændringer
- Hvis du ikke har adgang til en rigtig IO-Link enhed, kan du simulere data med Inject-noder
- Spørg underviseren hvis du har problemer med MQTT-forbindelsen

## Ekstra
- Prøv at udvide flowet med sanity checks, plausibilitetstest eller watchdog/heartbeat, som du lærte på dag 6

Held og lykke med øvelserne!
