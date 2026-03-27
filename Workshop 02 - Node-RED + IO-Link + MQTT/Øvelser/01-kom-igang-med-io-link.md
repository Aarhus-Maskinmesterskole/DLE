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

<img width="775" height="580" alt="image" src="https://github.com/user-attachments/assets/1c68b230-811f-43f9-a435-14781234b34a" />

---

## Trin 3 – Sæt pc og master i samme netværk

**A. Direkte forbindelse (hurtigt til test)**

* Forbind pc ↔ master med et netværkskabel.
* Sæt pc’en til en statisk IP i samme subnet, fx pc: `192.168.0.10/24`, gateway tom.

<img width="1382" height="790" alt="image" src="https://github.com/user-attachments/assets/849fc907-a5f8-40ab-8e12-65e807b00837" />


**B. Via eksisterende netværk (drift)**

* Forbind masteren til switchen (og 24 V forsyning).
* Sørg for, at pc’en kan nå masterens subnet (VLAN, firewall m.m.).

> Har masteren ukendt IP? Du kan ændre den fra **moneo | configure** → **Netværksscan** → **Marker master** → **Konfigurér IP**.

---

## Trin 4 - Start Moneo

1. Åben på Moneo som ligger på skrivebordet.
2. Udfyld alle felter.
   
<img width="1890" height="1020" alt="image" src="https://github.com/user-attachments/assets/9c77c352-f981-4612-b369-3bd95eb22241" />

3. Login med bruger og password du lige har oprettet

<img width="1862" height="1017" alt="image" src="https://github.com/user-attachments/assets/edc1ec6d-1eee-49e1-9300-86fc2a43a75b" />

4. Vælge **moneo|configure free license activation or activate Condition Monitoring trial**

<img width="1862" height="1017" alt="image" src="https://github.com/user-attachments/assets/4f3203be-a60f-4db2-8076-7dd0b9825acc" />

5. Vælge **Free moneo configure SA (Stand-Alone)** og tryk **Finish**

<img width="1862" height="1020" alt="image" src="https://github.com/user-attachments/assets/580584d3-5b6f-439f-8366-64addcb6477a" />


*OBS! Hvis moneo ikke vil åbne ved at bruge skrivebordsikonet så prøv da at åbne browseren og skriv: localhost:5000/shell*

---

## Trin 5 – Scan netværket for IO‑Link‑enheder

1. Start **moneo | configure** (hvis ikke startet).
2. Vælg **Network scan / Netværksscan**.

<img width="1860" height="1017" alt="image" src="https://github.com/user-attachments/assets/ea4244e0-159f-4911-8d10-f0b78d9e25ad" />

4. Vælg **Scan all** og tryk derefter *SCAN* i bunden.

<img width="1862" height="1020" alt="image" src="https://github.com/user-attachments/assets/4004c636-6b54-4752-aa91-0941d71ec3c2" />

6. Når master(e) vises, så tryk på **IP** og vælge *Configure IP* og giv den en IP adresse i samme subnet som dit netkort fx `192.168.0.20`

<img width="1865" height="1020" alt="image" src="https://github.com/user-attachments/assets/68734547-91cc-4cc0-82a3-f601d5d73f42" />

7. Angiv både IP address, Subnet mask og tryk derefter *WRITE TO DEVICE*

<img width="1865" height="1020" alt="image" src="https://github.com/user-attachments/assets/4aeef8c3-cf1d-4eb8-afe8-4c5a5c55ce0b" />

> Hvis du ikke ser noget: tjek firewall, subnet, og at masteren har 24 V.

---

## Trin 6 – Opret forbindelse (connect) til master/enhed

1. Dobbeltklik på masteren for at forbinde.
3. Markér en sensor under masteren og vælg **Connect** for at åbne enheds‑vinduet.

<img width="1865" height="1020" alt="image" src="https://github.com/user-attachments/assets/cfa8747e-7ff3-4716-84f7-a70f735189e4" />

5. Brug **Read**/**Write** til at hente og ændre parametre (om nødvendigt).

---

## Trin 7 – Identificér portenes status (i brug / deaktiveret)

* I master‑visningen ser du alle porte (1…8). Hver port har en **tilstand**:

  * **IO‑Link** (aktiv IO‑Link‑kanal)
  * **DI/DO** (digital input/output – afhænger af mastertype)
  * **Disabled** (port deaktiveret)
* Brug konfigurationsvinduet til at skifte porttilstand eller aktivere/deaktivere en port efter behov.

> LED’er på masteren afspejler ofte portstatus (IO‑Link kommunikation, fejl m.m.).

---

## Trin 8 – Se livedata fra sensoren i moneo

* Åbn sensoren i **moneo | configure** og find fanen **Process data** / **Live data**.

<img width="1860" height="1017" alt="image" src="https://github.com/user-attachments/assets/3ecd5649-92b9-4149-95b8-8d5b4e355a58" />

<img width="1865" height="1017" alt="image" src="https://github.com/user-attachments/assets/0bc59497-b69b-431d-93d6-d70a7cf2b121" />

* Bekræft, at værdierne opdateres (fx afstand, temperatur, tælling).

---

## Trin 9 – Verificér opsætningen i masterens web‑interface

1. Åbn en browser og skriv masterens IP (fx `http://192.168.0.20/web`).

<img width="1862" height="1015" alt="image" src="https://github.com/user-attachments/assets/3ca3700e-44c8-4878-b514-194418c8a74c" />

2. Kontroller at det er den samme sensor som fremgår i moneo.
5. Brug siden for **Diagnostics / Process data** til at se liveværdier.

> Formål: Sikre at masterens egen visning matcher moneo‑billedet. Uoverensstemmelser peger ofte på IP/subnet‑fejl, forkskellige masters, eller port‑tilstande der ikke er gemt.

---

## Trin 10 – Tjek data under **Subscription** i web‑interfacet

1. Åbn **Subscription**‑siden og ved at skriv følgende i browseren `192.168.0.20/web/subscribe`:

<img width="1865" height="1020" alt="image" src="https://github.com/user-attachments/assets/2143fdcd-db41-4efe-b18d-30962374c28f" />

2. Åben *Processdata* og se værdien på de enkelte sensorer 

> Målet her er at sikre, at de data moneo viser, også publiceres/eksponeres korrekt gennem masterens IoT/Subscription‑funktion – og at de ligger under **de rigtige porte**.

## Trin 11 - Angiv channel og broker
1. Gå til Notification
2. Tryk på det lille **'+'** nær *Unsubscribe*

<img width="1862" height="1017" alt="image" src="https://github.com/user-attachments/assets/4eab03cc-39c9-48a7-8f85-0c9fb9cbe46a" />

3. Vælge *counter* og tryk næste

<img width="1862" height="1015" alt="image" src="https://github.com/user-attachments/assets/15e8ab84-752f-4a3c-980f-542909b39db4" />

4. I søge feltet skriv *pdin* og vælge for den port du har en sensor på og tryk derefter næste

<img width="1862" height="1020" alt="image" src="https://github.com/user-attachments/assets/4feeaaeb-fd86-4cbc-a6df-2827bdbe8cb9" />

5. Sæt følgende og tryk dernæst *Finish*:
   - **Consumer ID:** 1
   - **IP Adress:** 142.93.135.2
   - **Port:** 1883 (ubeskyttet)
   - **Topic:** /dle/gr1/distance

<img width="1860" height="1020" alt="image" src="https://github.com/user-attachments/assets/d85a6a7c-4e05-4b98-8d2e-f2297c1877aa" />

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
