# README: Node-RED Protokol Eksempler (MQTT, AMQP, CoAP, Modbus, WebSocket) 📄

## Introduktion 👋

Dette dokument beskriver en samling af Node-RED flows, der demonstrerer brugen af forskellige kommunikationsprotokoller og teknologier, som er essentielle inden for automation, IIoT (Industrial Internet of Things) 🏭 og moderne webudvikling 🌐. Flowene er designet som simple eksempler, der kan importeres og tilpasses til egne projekter.

De dækkede protokoller/teknologier er:

1.  **MQTT** 📡: Letvægts publish/subscribe protokol, ideel til IoT-enheder og sensornetværk.
2.  **AMQP** 📦: Robust message queuing protokol, velegnet til pålidelig kommunikation mellem systemer (bruger RabbitMQ).
3.  **CoAP** 💡: Letvægts request/response protokol designet til ressourcebegrænsede IoT-enheder.
4.  **Modbus TCP** 🔌: Udbredt protokol til industriel automation og kommunikation med PLC'er og andre enheder.
5.  **WebSocket** ↔️: Protokol til fuld duplex realtidskommunikation, ofte brugt mellem webservere og browsere.

## Forudsætninger ✅

* **Node-RED:** En kørende instans af Node-RED.
* **Nødvendige Nodes:** Sørg for at have de relevante Node-RED nodes installeret via "Manage Palette" 🎨:
    * `node-red-contrib-amqp` (for AMQP)
    * `node-red-contrib-coap` (for CoAP)
    * `node-red-contrib-modbus` (for Modbus)
    * MQTT og WebSocket nodes er typisk indbyggede i standard Node-RED installationer.
* **Eksterne Services (afhængigt af flow):**
    * En MQTT Broker (f.eks. Mosquitto, HiveMQ, eller en cloud service). Eksemplet bruger `test.mosquitto.org`.
    * En AMQP Broker (f.eks. RabbitMQ). Eksemplet forventer en kørende RabbitMQ-instans på hostnavnet `rabbitmq`.
    * En CoAP-kompatibel enhed/server (hvis du tester CoAP request). Eksemplet sender til `aams_test`.
    * En Modbus TCP Slave/Server enhed eller simulator. Eksemplet forbinder til `172.24.0.5` på port `4999`.

## Implementering af Flows ⚙️

For hvert eksempel-flow nedenfor:

1.  Kopier den tilhørende JSON-kode 📋.
2.  I din Node-RED editor, gå til Menu (≡) -> Import.
3.  Indsæt JSON-koden i "Clipboard" fanen og klik "Import".
4.  Gennemgå og tilpas konfigurationen som beskrevet 🔧.
5.  Deploy flowet ▶️.

---

### 1. MQTT (Publish/Subscribe) 📡

* **Formål:** Demonstrerer afsendelse og modtagelse af beskeder via en MQTT broker. Bruges ofte til at sende sensordata eller kommandoer.
* **Flow Beskrivelse:**
    * En `mqtt in` node abonnerer på topic'et `sensor/temperatur`.
    * En `inject` node sender et timestamp til en `mqtt out` node.
    * `mqtt out` noden publicerer timestampet til topic'et `sensor/temperatur`.
    * Begge MQTT nodes er konfigureret til at bruge en MQTT broker (her `test.mosquitto.org`).
* **Tilpasning:**
    * **MQTT Broker:** Dobbeltklik på `mqtt in` eller `mqtt out` noden. Klik på blyanten ved siden af "Broker" feltet for at redigere broker-konfigurationen. Skift `test.mosquitto.org` og port `1883` til din egen broker, hvis nødvendigt. Tilføj credentials hvis din broker kræver det.
    * **Topic:** Ændr `sensor/temperatur` i `mqtt in` og `mqtt out` noderne til de topics, du vil bruge.
 
**Eksempel**

```javascript
[
    {
        "id": "4a828d69aacf64f6",
        "type": "group",
        "z": "3f49c92746d6dd8e",
        "style": {
            "stroke": "#999999",
            "stroke-opacity": "1",
            "fill": "none",
            "fill-opacity": "1",
            "label": true,
            "label-position": "nw",
            "color": "#a4a4a4"
        },
        "nodes": [
            "c50a92a7f0506b85",
            "7692f01bddc408ee",
            "83115ae7db19723f",
            "b791b0b35e210e5b"
        ],
        "x": 54,
        "y": 59,
        "w": 472,
        "h": 182
    },
    {
        "id": "c50a92a7f0506b85",
        "type": "mqtt in",
        "z": "3f49c92746d6dd8e",
        "g": "4a828d69aacf64f6",
        "name": "",
        "topic": "sensor/temperatur",
        "qos": "2",
        "datatype": "auto-detect",
        "broker": "449949c91ed42202",
        "nl": false,
        "rap": true,
        "rh": 0,
        "inputs": 0,
        "x": 190,
        "y": 100,
        "wires": [
            [
                "b791b0b35e210e5b"
            ]
        ]
    },
    {
        "id": "7692f01bddc408ee",
        "type": "mqtt out",
        "z": "3f49c92746d6dd8e",
        "g": "4a828d69aacf64f6",
        "name": "",
        "topic": "sensor/temperatur",
        "qos": "",
        "retain": "",
        "respTopic": "",
        "contentType": "",
        "userProps": "",
        "correl": "",
        "expiry": "",
        "broker": "449949c91ed42202",
        "x": 410,
        "y": 200,
        "wires": []
    },
    {
        "id": "83115ae7db19723f",
        "type": "inject",
        "z": "3f49c92746d6dd8e",
        "g": "4a828d69aacf64f6",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 160,
        "y": 200,
        "wires": [
            [
                "7692f01bddc408ee"
            ]
        ]
    },
    {
        "id": "b791b0b35e210e5b",
        "type": "debug",
        "z": "3f49c92746d6dd8e",
        "g": "4a828d69aacf64f6",
        "name": "debug 1",
        "active": false,
        "tosidebar": true,
        "console": false,
        "tostatus": true,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "payload",
        "statusType": "auto",
        "x": 380,
        "y": 100,
        "wires": []
    },
    {
        "id": "449949c91ed42202",
        "type": "mqtt-broker",
        "name": "",
        "broker": "test.mosquitto.org",
        "port": 1883,
        "clientid": "",
        "autoConnect": true,
        "usetls": false,
        "protocolVersion": 4,
        "keepalive": 60,
        "cleansession": true,
        "autoUnsubscribe": true,
        "birthTopic": "",
        "birthQos": "0",
        "birthRetain": "false",
        "birthPayload": "",
        "birthMsg": {},
        "closeTopic": "",
        "closeQos": "0",
        "closeRetain": "false",
        "closePayload": "",
        "closeMsg": {},
        "willTopic": "",
        "willQos": "0",
        "willRetain": "false",
        "willPayload": "",
        "willMsg": {},
        "userProps": "",
        "sessionExpiry": ""
    }
]
```

---

### 2. AMQP (Message Queuing med RabbitMQ) 📦

* **Formål:** Viser afsendelse og modtagelse af beskeder via en AMQP broker (RabbitMQ). Bruges til robust, asynkron kommunikation mellem applikationer.
* **Flow Beskrivelse:**
    * En `amqp in` node lytter på en kø (`test_queue`), som er bundet til en exchange (`temp` med routing key `temp`).
    * En `inject` node sender et timestamp til en `amqp out` node.
    * `amqp out` noden sender timestampet til `temp` exchange med routing key `temp`.
    * Begge AMQP nodes er konfigureret til at bruge en AMQP broker på hostnavnet `rabbitmq`.
* **Tilpasning:**
    * **AMQP Broker:** Dobbeltklik på `amqp in` eller `amqp out` noden. Klik på blyanten ved "Broker" for at redigere. Skift `rabbitmq` og port `5672` til adressen på din RabbitMQ server. Tilføj credentials hvis nødvendigt.
    * **Exchange/Queue/Routing Key:** Juster navnene (`temp`, `test_queue`) og routing key (`temp`) i `amqp in` og `amqp out` noderne, så de passer til din RabbitMQ opsætning.

**Eksempel**
```javascript
[
    {
        "id": "5b6b4a789a377bda",
        "type": "amqp-in",
        "z": "29820773d60f94ac",
        "name": "",
        "broker": "0ffadb38a4b4454f",
        "prefetch": 0,
        "reconnectOnError": false,
        "noAck": true,
        "exchangeName": "temp",
        "exchangeType": "topic",
        "exchangeRoutingKey": "temp",
        "exchangeDurable": true,
        "queueName": "test_queue",
        "queueType": "classic",
        "queueExclusive": false,
        "queueDurable": false,
        "queueAutoDelete": false,
        "headers": "{}",
        "x": 250,
        "y": 360,
        "wires": [
            [
                "1d0366e5a19a10ca"
            ]
        ]
    },
    {
        "id": "914c8245493dc5ad",
        "type": "amqp-out",
        "z": "29820773d60f94ac",
        "name": "",
        "broker": "0ffadb38a4b4454f",
        "reconnectOnError": false,
        "exchangeName": "temp",
        "exchangeType": "topic",
        "exchangeRoutingKey": "temp",
        "exchangeRoutingKeyType": "str",
        "exchangeDurable": true,
        "amqpProperties": "{ \"headers\": {} }",
        "rpcTimeoutMilliseconds": 3000,
        "outputs": 0,
        "x": 770,
        "y": 280,
        "wires": []
    },
    {
        "id": "a10fb5a0608a01ac",
        "type": "function",
        "z": "29820773d60f94ac",
        "name": "function - temperature and timestamp",
        "func": "msg.payload = {\n    temperatur: Number(Math.random()),\n    timestamp: new Date().toISOString()\n};\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 510,
        "y": 280,
        "wires": [
            [
                "914c8245493dc5ad"
            ]
        ]
    },
    {
        "id": "334cbdbab0393288",
        "type": "inject",
        "z": "29820773d60f94ac",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "1",
        "crontab": "",
        "once": true,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 250,
        "y": 280,
        "wires": [
            [
                "a10fb5a0608a01ac"
            ]
        ]
    },
    {
        "id": "1d0366e5a19a10ca",
        "type": "debug",
        "z": "29820773d60f94ac",
        "name": "debug 4",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": true,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "payload",
        "statusType": "auto",
        "x": 760,
        "y": 360,
        "wires": []
    },
    {
        "id": "0ffadb38a4b4454f",
        "type": "amqp-broker",
        "name": "",
        "host": "rabbitmq",
        "port": 5672,
        "vhost": "/",
        "tls": false,
        "credsFromSettings": false
    }
]
```

---

### 3. CoAP (Constrained Application Protocol) 💡

* **Formål:** Demonstrerer CoAP som en letvægtsprotokol for IoT, både ved at modtage requests (server-rolle) og sende requests (klient-rolle).
* **Flow Beskrivelse:**
    * **Server-del:** En `coap in` node lytter på stien `/temp` for POST requests. Når en request modtages, formaterer en `function` node payload'en og sender et svar tilbage via `coap response`.
    * **Klient-del:** En `inject` node sender et timestamp til en `coap request` node, som sender en POST request til `coap://aams_test:5683/temp`.
* **Tilpasning:**
    * **Server Port/Sti:** Dobbeltklik på `coap in` noden. Klik på blyanten ved "Server" for at ændre den port, Node-RED lytter på (standard 5683). Ændr stien `/temp` hvis nødvendigt.
    * **Klient URL:** Ret URL'en `coap://aams_test:5683/temp` i `coap request` noden, så den peger på den CoAP-enhed/server, du vil kommunikere med. Juster metode (POST, GET, etc.) og content-format efter behov.
    * **Function Node:** Tilpas logikken i `function` noden efter, hvordan du vil behandle indkommende CoAP data.

**Eksempel**
```javascript
[
    {
        "id": "ce195a52c2023c30",
        "type": "coap in",
        "z": "29820773d60f94ac",
        "method": "POST",
        "name": "",
        "server": "ae239dc7fa0a729e",
        "url": "/temp1",
        "x": 250,
        "y": 80,
        "wires": [
            [
                "3e4597ade844810c"
            ]
        ]
    },
    {
        "id": "7a6ecf1f77505eab",
        "type": "coap response",
        "z": "29820773d60f94ac",
        "name": "",
        "statusCode": "",
        "contentFormat": "application/json",
        "x": 590,
        "y": 80,
        "wires": []
    },
    {
        "id": "5733dc28f6757c78",
        "type": "coap request",
        "z": "29820773d60f94ac",
        "method": "POST",
        "confirmable": false,
        "observe": false,
        "multicast": false,
        "multicastTimeout": 20000,
        "url": "coap://nr4000:5683/temp1",
        "content-format": "application/json",
        "raw-buffer": false,
        "name": "",
        "x": 430,
        "y": 160,
        "wires": [
            [
                "c96c5b128c69e722"
            ]
        ]
    },
    {
        "id": "2281a1f6711abf46",
        "type": "inject",
        "z": "29820773d60f94ac",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "1",
        "crontab": "",
        "once": true,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 250,
        "y": 160,
        "wires": [
            [
                "5733dc28f6757c78"
            ]
        ]
    },
    {
        "id": "3e4597ade844810c",
        "type": "function",
        "z": "29820773d60f94ac",
        "name": "function 1",
        "func": "\nreturn msg;",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 420,
        "y": 80,
        "wires": [
            [
                "7a6ecf1f77505eab",
                "5e5b71d77be71fb5"
            ]
        ]
    },
    {
        "id": "c96c5b128c69e722",
        "type": "debug",
        "z": "29820773d60f94ac",
        "name": "debug 2",
        "active": false,
        "tosidebar": true,
        "console": false,
        "tostatus": true,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "payload",
        "statusType": "auto",
        "x": 600,
        "y": 160,
        "wires": []
    },
    {
        "id": "5e5b71d77be71fb5",
        "type": "debug",
        "z": "29820773d60f94ac",
        "name": "debug 3",
        "active": false,
        "tosidebar": true,
        "console": false,
        "tostatus": true,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "payload",
        "statusType": "auto",
        "x": 600,
        "y": 20,
        "wires": []
    },
    {
        "id": "ae239dc7fa0a729e",
        "type": "coap-server",
        "name": "",
        "port": "5683",
        "ipv6": false
    }
]
```

---

### 4. Modbus TCP (Industriel Kommunikation) 🔌

* **Formål:** Viser hvordan Node-RED kan agere som en Modbus TCP Master (Client) for at læse data fra en Modbus Slave (Server).
* **Flow Beskrivelse:**
    * En `modbus-read` node er konfigureret til periodisk (hvert sekund) at læse 16 Coils (FC1) fra adresse 1 på Unit ID 1.
    * Noden bruger en Modbus Client konfiguration, der peger på en TCP Host `172.24.0.5` på port `4999`.
    * Resultatet sendes til debug-noder.
* **Tilpasning:**
    * **Modbus Server:** Dobbeltklik på `modbus-read` noden. Klik på blyanten ved "Server". Ret `TCP Host` og `TCP Port` til adressen og porten på din faktiske Modbus TCP slave/server enhed.
    * **Læse Operation:** Juster `Unit-Id`, `FC` (Function Code: 1, 2, 3, 4, etc.), `Address` og `Quantity` i `modbus-read` noden, så den passer til de data, du vil læse fra din Modbus-enhed.
    * **Rate:** Ændr polling-intervallet efter behov.

**Eksempel**
```javascript
[
    {
        "id": "f8ac1f64bd57d20a",
        "type": "modbus-read",
        "z": "29820773d60f94ac",
        "name": "",
        "topic": "FC 1",
        "showStatusActivities": false,
        "logIOActivities": false,
        "showErrors": false,
        "showWarnings": true,
        "unitid": "1",
        "dataType": "Coil",
        "adr": "1",
        "quantity": "16",
        "rate": "1",
        "rateUnit": "s",
        "delayOnStart": false,
        "startDelayTime": "",
        "server": "74d7cc1d2d6a9f23",
        "useIOFile": false,
        "ioFile": "",
        "useIOForPayload": false,
        "emptyMsgOnFail": false,
        "x": 250,
        "y": 460,
        "wires": [
            [
                "5dfab487a539eb5a"
            ],
            [
                "ae3bbf64705fa84e"
            ]
        ]
    },
    {
        "id": "5dfab487a539eb5a",
        "type": "debug",
        "z": "29820773d60f94ac",
        "name": "debug 5",
        "active": false,
        "tosidebar": true,
        "console": false,
        "tostatus": true,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "payload",
        "statusType": "auto",
        "x": 560,
        "y": 460,
        "wires": []
    },
    {
        "id": "ae3bbf64705fa84e",
        "type": "debug",
        "z": "29820773d60f94ac",
        "name": "debug 9",
        "active": false,
        "tosidebar": true,
        "console": false,
        "tostatus": true,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "payload",
        "statusType": "auto",
        "x": 560,
        "y": 540,
        "wires": []
    },
    {
        "id": "74d7cc1d2d6a9f23",
        "type": "modbus-client",
        "name": "",
        "clienttype": "tcp",
        "bufferCommands": true,
        "stateLogEnabled": false,
        "queueLogEnabled": false,
        "failureLogEnabled": true,
        "tcpHost": "172.24.0.5",
        "tcpPort": "4999",
        "tcpType": "DEFAULT",
        "serialPort": "/dev/ttyUSB",
        "serialType": "RTU-BUFFERD",
        "serialBaudrate": 9600,
        "serialDatabits": 8,
        "serialStopbits": 1,
        "serialParity": "none",
        "serialConnectionDelay": 100,
        "serialAsciiResponseStartDelimiter": "0x3A",
        "unit_id": 1,
        "commandDelay": 1,
        "clientTimeout": 1000,
        "reconnectOnTimeout": true,
        "reconnectTimeout": 2000,
        "parallelUnitIdsAllowed": true,
        "showErrors": false,
        "showWarnings": true,
        "showLogs": true
    }
]
```

---

### 5. WebSocket (Real-time Kommunikation) ↔️

* **Formål:** Demonstrerer en WebSocket loopback-forbindelse, hvor Node-RED både er server og klient. Dette er primært til test og demonstration af WebSocket-noderne.
* **Flow Beskrivelse:**
    * En `websocket in` node lytter på stien `/ws/test` (på Node-REDs standard port, typisk 1880).
    * En `inject` node sender et timestamp til en `websocket out` node.
    * `websocket out` noden er konfigureret som en klient, der forbinder til `ws://localhost:1880/ws/test` (sin egen listener).
    * Modtagne beskeder vises i debug-ruden.
* **Tilpasning (for at forbinde til eksterne):**
    * **Node-RED som Server:** Behold `websocket in` noden. Slet `websocket out` og `inject`. Eksterne klienter kan nu forbinde til `ws://<din-node-red-ip>:1880/ws/test`. Sørg for at port 1880 er publiceret, hvis Node-RED kører i Docker.
    * **Node-RED som Klient:** Behold `websocket out` og `inject`. Slet `websocket in`. Dobbeltklik på `websocket out`, klik på blyanten ved "Client", og ret URL'en (`ws://localhost:1880/ws/test`) til den eksterne WebSocket server, du vil sende data til (f.eks. `ws://nr4000:4000/ws/data`).

**Eksempel**
```javascript
[
    {
        "id": "a1b2c3d4e5f6a1b2",
        "type": "inject",
        "z": "29820773d60f94ac",
        "name": "Send Timestamp",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 240,
        "y": 660,
        "wires": [
            [
                "f6e5d4c3b2a1f6e5"
            ]
        ]
    },
    {
        "id": "f6e5d4c3b2a1f6e5",
        "type": "websocket out",
        "z": "29820773d60f94ac",
        "name": "Send to Loopback",
        "server": "",
        "client": "c3b2a1f6e5d4c3b2",
        "x": 460,
        "y": 660,
        "wires": []
    },
    {
        "id": "d4c3b2a1f6e5d4c3",
        "type": "websocket in",
        "z": "29820773d60f94ac",
        "name": "Receive from Loopback",
        "server": "b2a1f6e5d4c3b2a1",
        "client": "",
        "x": 230,
        "y": 780,
        "wires": [
            [
                "e5d4c3b2a1f6e5d4"
            ]
        ]
    },
    {
        "id": "e5d4c3b2a1f6e5d4",
        "type": "debug",
        "z": "29820773d60f94ac",
        "name": "WebSocket Msg Received",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 480,
        "y": 780,
        "wires": []
    },
    {
        "id": "c3b2a1f6e5d4c3b2",
        "type": "websocket-client",
        "path": "ws://localhost:1880/ws/test",
        "tls": "",
        "wholemsg": "false",
        "hb": "0",
        "subprotocol": "",
        "headers": []
    },
    {
        "id": "b2a1f6e5d4c3b2a1",
        "type": "websocket-listener",
        "path": "/ws/test",
        "wholemsg": "false"
    }
]
```

---

## Hvorfor Lære Disse Protokoller/Teknologier? 🤔

For studerende inden for automation, IT, og ingeniørfag (som dem du underviser på aams, Anders) er kendskab til disse kommunikationsmetoder afgørende af flere årsager:

1.  **Industriel Relevans (Modbus, AMQP):** Modbus 🏭 er stadig en de facto standard i mange industrielle miljøer til kommunikation med PLC'er, sensorer og aktuatorer. AMQP (via RabbitMQ) 📨 bruges ofte i større systemer til pålidelig dataudveksling mellem maskiner og softwarelag. At kunne integrere med disse er essentielt for automationsingeniører.
2.  **IoT Udbredelse (MQTT, CoAP, WebSocket):** Internettet af Ting 📈 vokser eksplosivt. MQTT 📡 er den mest populære protokol til at forbinde millioner af enheder til skyen på grund af dens effektivitet. CoAP 💡 er designet til endnu mere ressourcebegrænsede enheder. WebSockets 🕸️ bruges ofte til at vise realtidsdata fra IoT-enheder på web-dashboards. Kendskab til disse åbner døre til IoT-udvikling.
3.  **Systemintegration:** Moderne systemer består sjældent af én enkelt teknologi. Evnen til at få forskellige systemer, der taler forskellige "sprog" (protokoller), til at kommunikere er en kernekompetence 🤝. Node-RED excellerer her ved at tilbyde en visuel måde at bygge bro mellem disse teknologier.
4.  **Fleksibilitet og Problemløsning:** At forstå fordele og ulemper ved forskellige protokoller gør studerende i stand til at vælge det rigtige værktøj til opgaven 🛠️. Skal data sendes pålideligt? (AMQP). Skal det være letvægtigt og til mange enheder? (MQTT). Skal det være realtid til en browser? (WebSocket).
5.  **Øget Beskæftigelsesværdi:** Virksomheder inden for automation, produktion, smart cities, og softwareudvikling efterspørger medarbejdere, der kan håndtere disse teknologier 💼. At have praktisk erfaring med dem, f.eks. via Node-RED projekter, er et stort plus på CV'et ⭐.

Node-RED fungerer som en fantastisk læringsplatform 🎓, da den abstraherer noget af kompleksiteten væk og lader studerende fokusere på *hvordan* data flyder og *hvordan* systemer forbindes, uden at skulle skrive omfattende kode for hver protokol fra bunden.

## Konklusion 🎉

Disse eksempel-flows giver et udgangspunkt for at arbejde med centrale kommunikationsprotokoller i Node-RED. Ved at importere, tilpasse og eksperimentere med dem, kan man opnå en praktisk forståelse for, hvordan moderne systemer udveksler data.
