# Kom godt i gang med MQTT Explorer
Denne vejledning fører dig sikkert fra installation til opsætning af forbindelse til en MQTT-broker ved hjælp af MQTT Explorer.
---
## Forudsætninger
* Windows-, macOS- eller Linux-pc med internetadgang
* Kendskab til grundlæggende MQTT-koncept (emner, publicering, abonnement)
* Adgang til en MQTT-broker (*offentlig broker: test.mosquitto.org*)
---
## Trin 1 – Hent MQTT Explorer
1. Gå til [MQTT Explorer](https://mqtt-explorer.com/) og klik på "Download" for det styresystem, du bruger.
2. Gem installationsfilen lokalt.
3. Kør installationsfilen og følg installationsguiden.
---
## Trin 2 – Start MQTT Explorer
1. Åbn MQTT Explorer-applikationen.
![alt text](image.png)

2. Klik på *"Host"* feltet for at konfigurere en ny forbindelse og indsæt følgende oplysninger:
   - **Host**: `test.mosquitto.org`
   - **Port**: `1883` (standard port for ukrypteret MQTT)
   - **Client ID**: Lad stå tomt for automatisk generering eller indtast en unik ID.
3. Klik på *"Connect"* knappen for at oprette forbindelse til broker'en.
    ![alt text](image-1.png)
   Dette billede viser at du er forbundet til broker'en og lytter til alle emner. Dette visere endvidere at ingen beskeder på denne broker er krypteret.

4. Prøv at publicere en besked fra MQTT Explorer til topic `aams/test` med payload `first message` og se om den dukker op i MQTT Explorer.

   ![alt text](image-2.png)

5. Prøv at publicere en besked fra Node-RED til samme topic `aams/test` med payload `second message` og se om den dukker op i MQTT Explorer.

   
