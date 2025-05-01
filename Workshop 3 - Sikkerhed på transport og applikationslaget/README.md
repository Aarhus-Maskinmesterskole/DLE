# 🔐 Transport- og Applikationslagets Sikkerhed (MITM)

## 👋 Velkommen til Workshop 3

Denne workshop handler om **sikkerhed i IIOT-datastrømme**. Du kommer til at arbejde med, hvordan man beskytter forbindelser mod aflytning og manipulation. Det gør vi ved at simulere et **Man-in-the-Middle (MITM)** angreb, hvor en tredje part kan opsnappe og ændre dine data, hvis trafikken ikke er sikret.

Du skal bruge et færdigt Python-script med grafisk brugerflade (GUI), som du kører på din computer. Du skal **ikke udvikle kode**, men blot følge instruktionerne og observere hvad der sker. Derefter skal du analysere, hvordan TLS og adgangskontrol kan forhindre det samme angreb.

---

## 🌟 Formål
- Se med egne øjne hvordan datastrømme kan aflures og manipuleres.
- Forstå hvordan man kan beskytte forbindelser med TLS og brugervalidering.
- Træne i at dokumentere og analysere sikkerhedshåndtering i IIOT-systemer.

---

## 🤮 Øvelser du skal igennem

| Øvelse | Fokus |
|:------:|:------|
| 1 | Forstå IIOT-sikkerhedstrusler (sniffing, spoofing, MITM) |
| 2 | Kør færdigt Python-script og start GUI |
| 3 | Indtast IP’er og vælg interface – start MITM-angreb |
| 4 | Observer opsnappede beskeder i realtid (GUI-visning) |
| 5 | Afprøv hvordan beskeder kunne manipuleres |
| 6 | Stop angrebet og analyser hvad du så |
| 7 | Implementér TLS og login i din MQTT-kommunikation |
| 8 | Gennemfør ny test og sammenlign effekten |
| 9 | Dokumentér og optag video/screenshot |
| 10 | Reflektér: Hvordan ville du sikre et produktionsmiljø? |

---

## 🔄 Sådan bruger du værktøjet

Du skal nu arbejde med det udleverede Python-script `mitm.py`, som åbner en simpel brugerflade.

Følg disse trin:

1. Start scriptet.
2. Indtast IP-adresser for din “target” og “gateway” (f.eks. dig selv og din router).
3. Vælg det netværksinterface du er på (WiFi eller kabel).
4. Tryk på **“Start Attack”** – og følg med i hvilke beskeder der opsnappes i vinduet.
5. Tryk **“Stop Attack”** for at afslutte.

I de næste øvelser skal du arbejde videre med det du observerer, og teste hvordan sikkerhed ændrer på dataadgangen.

---

## 🤝 Din rolle
- Du arbejder aktivt med at opsætte, analysere og beskytte en datastrøm.
- Du følger en færdig løsning og forholder dig kritisk til resultaterne.
- Du dokumenterer dine observationer og reflekterer over sikkerhedsaspekter.

---

## 🔍 Du skal aflevere
Efter workshoppen skal du:

- Dokumentere din opsætning med video eller screenshots (GUI, angreb, evt. beskyttet test).
- Notere dine observationer under og efter angrebet.
- Besvare disse refleksionsspørgsmål:
  1. Hvilke typer data kunne du opsnappe?
  2. Hvad ville en angriber kunne udrette med disse data?
  3. Hvordan ændrede det sig, da du aktiverede TLS og login?
  4. Hvad ville du anbefale, hvis dette var et rigtigt produktionsmiljø?

Afleveres som en del af jeres portfolio.

---

## 🚀 Når du er færdig, skal du kunne:
- Udføre og forstå et MITM-angreb på en lokal MQTT-forbindelse.
- Forstå hvilke sårbarheder der findes i usikret netværkskommunikation.
- Beskytte en forbindelse med TLS og adgangskontrol.
- Forklare dine resultater og anbefale sikkerhedsforbedringer.

---

## 📆 Vurdering
- Workshoppen indgår i din gruppeportfolio.
- Du bedømmes på dokumentation og refleksion – ikke på hvor mange pakker du fanger.
- Bedømmelsen er: **Godkendt / Ikke godkendt**.

Held og lykke med workshoppen – og husk: det du lærer her, kan forhindre store fejl i fremtiden! 🚀

