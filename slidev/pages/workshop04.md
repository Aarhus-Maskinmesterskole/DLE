# Workshop 4: Python Basics + MQTT

Velkommen til kodesiden! I dag tager vi de første skridt i Python. Vi skal lære syntaksen at kende og hurtigt få vores scripts til at tale med den MQTT-broker, vi satte op i Workshop 2.

---
layout: section
---

# Workshop 4: Python Basics + MQTT 🐍
> "Programmering er ikke svært – det er bare logik skrevet med tekst."

---
layout: default
---

# Hvorfor Python for Maskinmestre? 🛠️
Python er blevet industriens foretrukne sprog til IoT og data-analyse.

* **Læsbart:** Det ligner næsten almindeligt engelsk.
* **Batteries Included:** Der findes biblioteker til alt (PLC'er, databaser, grafer).
* **Fleksibelt:** Kører på alt fra din laptop til en Raspberry Pi eller en Industrial PC.

<div v-click class="mt-8 p-4 bg-green-50 dark:bg-green-900/20 border-l-4 border-green-500">
  <strong>Dagens mission:</strong> 
  Skriv et Python-script, der simulerer en sensor og sender data til Node-RED via MQTT.
</div>

---
layout: two-cols
---

# Lynkursus i Syntaks ⚡

De vigtigste byggeklodser:

**1. Variabler & Typer**
```python
temp = 22.5          # Float
maskine_id = "MMS-1" # String
is_running = True    # Boolean
```

**2. Betingelser (If-else)**
```python
if temp > 25:
    print("Alarm: For varmt!")
else:
    print("Temperatur OK")
```

::right::

<v-click class="ml-4">

**3. Loops (Løkker)**
```python
for i in range(5):
    print(f"Måling nr: {i}")
```

**4. Funktioner**
```python
def check_status(id):
    return f"Status for {id} er OK"

print(check_status("Pumpe_A"))
```

<div class="mt-4 p-2 bg-yellow-100 dark:bg-yellow-900/30 rounded text-sm">
  <carbon:warning class="inline mr-2"/> 
  Husk indrykning (Tabs/Spaces)! I Python betyder indrykning alt for din logik.
</div>

</v-click>

---
layout: default
---

# MQTT i Python: `paho-mqtt` 📨

For at tale med vores broker skal vi bruge et bibliotek. Terminalen er din ven:

```bash
pip install paho-mqtt
```

### De 3 trin i koden:
1. **Import:** Hent biblioteket ind i dit script.
2. **Connect:** Fortæl Python, hvor din broker bor (IP-adresse).
3. **Publish:** Send dine data afsted på et specifikt topic.

---
layout: two-cols
---

# Din første MQTT-klient 💻

Dette script sender data hvert 5. sekund.

```python {all|1-2|5-7|9-11|13-17}
import paho.mqtt.client as mqtt
import time

# 1. Setup
broker = "localhost" # Eller IP på din RPi
client = mqtt.Client("MMS_Python_Script")

# 2. Forbind
print("Forbinder til broker...")
client.connect(broker)

# 3. Main Loop
while True:
    data = "Pumpe aktiv: 45.2 L/m"
    client.publish("mms/workshop4/status", data)
    print("Data sendt!")
    time.sleep(5)
```

::right::

<v-click class="ml-4">

### Opgave:
1. Opret en ny fil: `mqtt_test.py`.
2. Kopier koden til venstre.
3. Kør den med `python mqtt_test.py`.
4. **Tjek i Node-RED:** Kan du se dine data dukke op i en debug-node?

<div class="mt-8 border-2 border-dashed border-main p-4 rounded text-center">
  <carbon:rocket class="text-3xl mb-2"/>
  <p>Bonus: Prøv at sende et JSON-objekt i stedet for en tekststreng!</p>
</div>

</v-click>

---
layout: center
---

# Hvad lærte vi i dag? 🎓

- Vi har installeret Python-biblioteker med `pip`.
- Vi har forstået variabler og loops.
- Vi har bygget en bro mellem **Python** (kode) og **Node-RED** (visualisering).

> **Næste gang:** Vi skal kigge på **Pandas** – det vildeste værktøj til at knuse data fra tusindvis af sensorer på én gang!

---