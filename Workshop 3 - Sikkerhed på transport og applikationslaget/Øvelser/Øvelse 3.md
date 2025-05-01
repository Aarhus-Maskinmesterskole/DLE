# 🧪 Øvelse 3: Manipuler datastrømmen

## 🎯 Formål
I denne øvelse skal du eksperimentere med, hvordan en angriber potentielt kan ændre indholdet af beskeder i et Man-in-the-Middle (MITM)-scenarie i et IIOT-miljø. Målet er at demonstrere, at ubeskyttede MQTT-forbindelser ikke blot kan opsnappes og læses i klartekst – men også manipuleres undervejs, uden at afsender eller modtager nødvendigvis opdager det. 

Ved at arbejde med manipulation af MQTT-data får du en dybere forståelse for de alvorlige konsekvenser af manglende sikkerhed i industrielle netværk. Denne øvelse sætter fokus på, hvordan selv små ændringer i data kan have store konsekvenser i produktion, bygningsautomatik eller energisystemer. Du fortsætter med det samme Python-script som i Øvelse 2, men skifter fokus fra passiv til aktiv analyse.

---

## 🛠️ Forudsætninger
For at kunne gennemføre øvelsen korrekt og opnå størst læringsudbytte, skal følgende være opfyldt:

- Du har gennemført Øvelse 2 og har set MQTT-data blive opsnappet i realtid gennem GUI'en.
- Du har stadig adgang til Python-scriptet `mitm.py` og er i stand til at ændre midlertidigt i dets kode.
- Du er forbundet til et netværk, hvor du enten kan bruge din egen maskine som "target", eller samarbejder med en medstuderende som fungerer som offer.
- Du har forståelse for hvordan beskeder flyder mellem klient og broker i et MQTT-baseret system.

---

## ⚙️ Praktisk fremgangsmåde

1. **Rediger scriptet midlertidigt (kun denne øvelse)**
   - Find funktionen `process_packet()` i dit `mitm.py`-script.
   - Du skal nu indsætte kode, der ændrer en værdi i den modtagne MQTT-besked, så du kan simulere et angreb, hvor en besked bliver manipuleret undervejs:
```python
if packet.haslayer(TCP) and packet.haslayer(Raw):
    original = packet[Raw].load.decode(errors='ignore')
    print(f"Intercepted: {original}")
    manipulated = original.replace("23.0", "87.0")  # eksempel: ændring af temperaturværdi
    print(f"Manipulated: {manipulated}")
```
   - Scriptet vil nu både vise original og manipuleret værdi i terminalen/GUI.
   - **OBS:** Du sender ikke den manipulerede besked videre i denne øvelse – du observerer kun, hvordan manipulationen kunne foregå.

2. **Overvej konsekvenserne af manipulation**
   - Forestil dig, at den manipulerede besked handlede om temperaturen i en bygning, en tryksensor i et anlæg eller en adgangsgodkendelse.
   - Hvordan kunne en falsk måling ændre på systemets reaktion? Kunne det føre til falsk alarm, unødig nedlukning eller i værste fald forkert drift?

3. **Samarbejd og diskuter**
   - Tal med en sidemand eller gruppe:
     - Hvad var let eller svært ved at gennemføre manipulationen?
     - Hvordan kunne man i praksis opdage, at beskeder var blevet ændret?
     - Hvilke svagheder i MQTT gør denne type angreb mulig?

---

## 📋 Refleksion
Brug dine observationer til at overveje følgende:

- Hvilken betydning har det, at beskeder kan ændres i transit?
- Hvordan ville en dygtig angriber kunne skjule sine spor endnu bedre?
- Hvordan kan man som systemadministrator, udvikler eller operatør beskytte sig mod den type sårbarhed?
- Hvilke konkrete værktøjer, teknologier eller protokoller kunne anvendes til at forhindre manipulation af beskeder?

Lav evt. stikord, så du er klar til næste øvelse, hvor vi implementerer sikring.

---

> **Bemærk:** Du skal ikke gemme ændringerne i scriptet permanent – scriptet nulstilles i Øvelse 4, hvor du genskaber den oprindelige version.

👉 Gå videre til Øvelse 4, hvor vi fokuserer på beskyttelse mod denne type angreb gennem TLS og adgangskontrol.

