---
theme: seriph
background: https://images.unsplash.com/photo-1558494949-ef010cbdcc51?auto=format&fit=crop&q=80
class: text-center
highlighter: shiki
lineNumbers: true
---

# IoT & Programmering for Maskinmestre 🛠️
## 7 Workshops: Fra Installation til Python Control
Aarhus Maskinmesterskole

<div class="pt-12">
  <span class="opacity-50">Tryk på Space for at se kursusplanen</span>
</div>

---
layout: default
---

# Kursusoversigt: De 7 Workshops

<div class="grid grid-cols-2 gap-x-10 gap-y-4">

<div v-click>
<h3 class="text-blue-500">Del 1: Node-RED & OT Integration</h3>

**WS 1: Installation & Miljø**
* Setup af Node-RED, Docker & Flows basics.

**WS 2: IO-Link & MQTT**
* Hentning af sensordata fra hardware til broker.

**WS 3: HTTP API & Server**
* Lav din egen webserver og REST endpoints.
</div>

<div v-click>
<h3 class="text-green-600">Del 2: Python & Data Science</h3>

**WS 4: Python Basics + MQTT**
* Syntaks, loops og `paho-mqtt` biblioteket.

**WS 5: Data med Pandas**
* Håndtering af store datamængder og tabeller.

**WS 6: Visualisering med Matplotlib**
* Grafer, trends og data-analyse.

**WS 7: Python MCP (Master Control Program)**
* Samling af det hele: Logik, styring og integration.
</div>

</div>

---
layout: center
class: text-center
---

# Workshop 1: Node-RED Installation 🚀
*Dagens mål: At få "motoren" op at køre.*

<div class="grid grid-cols-3 gap-4 mt-10">
  <div class="border border-main p-4 rounded">
    <carbon:settings />
    <p>Installation</p>
  </div>
  <div class="border border-main p-4 rounded">
    <carbon:flow />
    <p>First Flow</p>
  </div>
  <div class="border border-main p-4 rounded">
    <carbon:debug />
    <p>Debug Node</p>
  </div>
</div>

---

# Roadmap Visualisering
Hvordan de 7 workshops hænger sammen:

```mermaid
graph TD
  WS1[WS1: Node-RED] --> WS2[WS2: IO-Link/MQTT]
  WS2 --> WS3[WS3: HTTP API]
  WS3 --> WS4[WS4: Python MQTT]
  WS4 --> WS5[WS5: Pandas]
  WS5 --> WS6[WS6: Matplotlib]
  WS6 --> WS7[WS7: Det samlede system]
  style WS7 fill:#f96,stroke:#333,stroke-width:4px