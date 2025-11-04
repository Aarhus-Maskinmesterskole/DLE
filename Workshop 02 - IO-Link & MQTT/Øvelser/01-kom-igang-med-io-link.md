# Kom godt i gang med IO‑Link og ifm moneo

Denne vejledning fører dig sikkert fra download til live data – inkl. netværksscan, port‑status og kontrol i masterens web‑interface.

---

## Forudsætninger

* Windows‑pc med administratorrettigheder
* Ethernet (pc ↔ IO‑Link‑master) og 24 V forsyning til masteren
* IO‑Link‑master (fx ifm AL13xx/AL19xx) og mindst én IO‑Link‑sensor
* Kendt IP‑adresse eller mulighed for at sætte masterens IP på samme subnet som pc’en

> Tip: Hvis masteren står på fabriks‑IP eller DHCP, kan du stadig finde den via **moneo | configure** netværksscan og derefter sætte en fast IP.

---

## Trin 1 – Hent moneo

1. Gå til ifm’s [**moneo downloads**](https://www.ifm.com/dk/da/shared/moneo-downloads?startDownload=/moneo_edgeGateway/V_1.18/moneo-edgegateway-AE2100-1.18.1-2025-08.moneoupdate) og hent **moneo | configure (free)**. Filen hedder **Installations- og opdateringsfil til ifm moneo til anvendelse i Windows**
2. Gem installationsfilen lokalt.

> Note: moneo‑pakken består af flere moduler. Til grundopsætning og parametrering er **moneo | configure** nok.

---

## Trin 2 – Installer moneo

1. Højreklik på installationsfilen og vælg **Kør som administrator**.
2. Følg guiden. Genstart hvis du bliver bedt om det.
3. (Kun relevant for betalte moduler) Aktiver licenser med de tilsendte LAC‑koder.

---

## Trin 3 – Sæt pc og master i samme netværk

**A. Direkte forbindelse (hurtigt til test)**

* Forbind pc ↔ master med et netværkskabel.
* Sæt pc’en til en statisk IP i samme subnet, fx pc: `192.168.0.10/24`, gateway tom.

**B. Via eksisterende netværk (drift)**

* Forbind masteren til switchen (og 24 V forsyning).
* Sørg for, at pc’en kan nå masterens subnet (VLAN, firewall m.m.).

> Har masteren ukendt IP? Du kan ændre den fra **moneo | configure** → **Netværksscan** → **Marker master** → **Konfigurér IP**.

---

## Trin 4 – Scan netværket for IO‑Link‑enheder

1. Start **moneo | configure**.
2. Vælg **Network scan / Netværksscan**.
3. Vælg korrekt netværksinterface (din pc’s Ethernet) og tryk **Scan**.
4. Når master(e) vises, fold dem ud for at se tilkoblede IO‑Link‑enheder.

> Hvis du ikke ser noget: tjek firewall, subnet, og at masteren har 24 V.

---

## Trin 5 – Opret forbindelse (connect) til master/enhed

1. Dobbeltklik på masteren for at forbinde.
2. Markér en sensor under masteren og vælg **Connect** for at åbne enheds‑vinduet.
3. Brug **Read**/**Write** til at hente og ændre parametre (om nødvendigt).

---

## Trin 6 – Identificér portenes status (i brug / deaktiveret)

* I master‑visningen ser du alle porte (1…8). Hver port har en **tilstand**:

  * **IO‑Link** (aktiv IO‑Link‑kanal)
  * **DI/DO** (digital input/output – afhænger af mastertype)
  * **Disabled** (port deaktiveret)
* Brug konfigurationsvinduet til at skifte porttilstand eller aktivere/deaktivere en port efter behov.

> LED’er på masteren afspejler ofte portstatus (IO‑Link kommunikation, fejl m.m.).

---

## Trin 7 – Se livedata fra sensoren i moneo

* Åbn sensoren i **moneo | configure** og find fanen **Process data** / **Live data**.
* Bekræft, at værdierne opdateres (fx afstand, temperatur, tælling).
* Gem evt. en **Device snapshot** (backup af parametre).

---

## Trin 8 – Verificér opsætningen i masterens web‑interface

1. Åbn en browser og skriv masterens IP (fx `http://192.168.0.50`).
2. Log ind (default brugernavn/adgangskode kan variere pr. model – ændr dem ved første login).
3. Gå til **IO‑Link / Ports** og kontroller, at de **samme enheder/porte** fremgår som i moneo.
4. Brug siden for **Diagnostics / Process data** til at se liveværdier.

> Formål: Sikre at masterens egen visning matcher moneo‑billedet. Uoverensstemmelser peger ofte på IP/subnet‑fejl, forkskellige masters, eller port‑tilstande der ikke er gemt.

---

## Trin 9 – Tjek data under **Subscription** i web‑interfacet

1. I masterens web‑menu: find sektionen **IoT / Data / Subscription** (navnet kan være *Subscription*, *IoT Core*, *Data Server*, eller lignende afhængigt af model/firmware).
2. Åbn **Subscription**‑siden og gennemgå listerne/kanalerne:

   * Der skal findes datagrupper for **Port 1…8** (eller per enhed) med **Process Data / Value / Status**.
   * Kontroller at de **porte du bruger** er inkluderet i subscriptionen.
3. Hvor det er relevant: bekræft transport (fx **MQTT/HTTPS/JSON**) og at publishing er **Enabled**.
4. Gem/Apply og verificér, at tællere/tidsstempler ændres når sensoren påvirkes.

> Målet her er at sikre, at de data moneo viser, også publiceres/eksponeres korrekt gennem masterens IoT/Subscription‑funktion – og at de ligger under **de rigtige porte**.

---

## Tjekliste

* [ ] moneo | configure installeret og kører
* [ ] Master og pc i samme subnet (ping fungerer)
* [ ] Netværksscan viser master og sensor(er)
* [ ] Porttilstande korrekte (IO‑Link for aktive sensorer)
* [ ] Live processdata ses i moneo
* [ ] Web‑interface viser samme master/porte/enheder som moneo
* [ ] Subscription‑siden indeholder data for de korrekte porte

---

## Fejlfinding (kort)

* **Master dukker ikke op i scan** → Tjek 24 V, subnet, firewall; prøv direkte kabel pc↔master og statisk IP.
* **Kan ikke logge på web** → Tjek login/rolle; brug HTTPS hvis påkrævet; skift default password.
* **Ingen data i Subscription** → Sørg for at porten er **IO‑Link**, enheden er forbundet og **publishing** er slået til; tryk **Apply/Save**.
* **Forkerte porte** → Sammenlign masterens serienummer/IP i både moneo og web; sørg for at du kigger på **samme master**.
* **Ændringer “forsvinder”** → Husk at vælge **Write/Apply** og gem konfigurationen på masteren.

---

## Bilag – Hurtige IP‑eksempler

* Test direkte: pc `192.168.0.10/24` ↔ master `192.168.0.50/24`
* Drift: Brug fast IP i produktions‑subnet, eller DHCP‑reservation per MAC‑adresse

---

### Done!

Du har nu moneo kørende, masteren i netværk, ports status afklaret, livedata i moneo, og verificeret, at web‑/Subscription‑siden viser data under de rigtige porte.
