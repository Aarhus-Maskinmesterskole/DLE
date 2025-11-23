# Python basics – Opgaver

Disse 10 opgaver følger strukturen i præsentationen `python-basic.tex` og kan bruges som øvelser til dag 1.

---

## Opgave 1 – Dit første Python‑script

**Formål:** Kom i gang med editor, kørsel og `print()`.

1. Åbn VS Code og opret en ny fil `hello.py`.
2. Skriv et program der:
   - Skriver `Hello, World!` i konsollen.
   - Skriver dit navn på næste linje.
3. Kør scriptet fra terminalen med `python hello.py`.

*Ekstra:* Tilføj en kommentar i toppen af filen med dit navn og dato.

---

## Opgave 2 – Variabler og typer

**Formål:** Øve variabler, typer og `print()`.

Lav et script `variables.py`, der:

1. Opretter følgende variabler:
   - `navn` (str)
   - `alder` (int)
   - `temperatur` (float)
   - `studerende` (bool)
2. Udskriver en sætning som fx:
   - `Mit navn er <???>, jeg er 25 år og temperaturen er 21.5°C`
3. Brug `type()` til at udskrive typen af hver variabel.

*Ekstra:* Prøv at ændre `alder` fra `"25"` (streng) til `25` (int) og se forskellen.

---

## Opgave 3 – Operatorer og udtryk

**Formål:** Arbejde med aritmetiske og logiske operatorer.

Lav et script `operators.py`, der:

1. Beder brugeren om to tal (`input()`), fx `a` og `b`.
2. Beregner og printer:
   - Summen `a + b`
   - Forskellen `a - b`
   - Produktet `a * b`
   - Kvotienten `a / b`
3. Undersøger og printer om:
   - `a > b`
   - `a == b`

*Hint:* Husk at caste `input()` til `int` eller `float` med `int()` eller `float()`.

---

## Opgave 4 – Statements, conditions og control flow

**Formål:** Bruge `if/elif/else` til at træffe beslutninger.

Lav et script `conditions.py`, der:

1. Beder brugeren om at skrive en temperatur i °C.
2. Udskriver:
   - `Det er frostvejr`, hvis temperaturen er under 0.
   - `Det er koldt`, hvis temperaturen er mellem 0 og 10.
   - `Det er mildt`, hvis temperaturen er mellem 10 og 20.
   - `Det er varmt`, hvis temperaturen er over 20.

*Ekstra:* Tilføj en input‑kontrol, der håndterer, hvis brugeren skriver noget, der ikke er et tal.

---

## Opgave 5 – Loops og lister

**Formål:** Øve `for`‑ og `while`‑loops samt lister.

Lav et script `loops.py`, der:

1. Opretter en liste med 5 heltal, fx `tal = [3, 7, 2, 9, 4]`.
2. Bruger et `for`‑loop til at:
   - Udskrive hvert tal.
   - Udregne summen af alle tal.
3. Bruger et `while`‑loop til at tælle ned fra 10 til 0 og udskrive tallene.

*Ekstra:* Lav et `for`‑loop, som kun udskriver tal større end 5.

---

## Opgave 6 – Datatyper og collections

**Formål:** Forstå forskellen på `list`, `dict` og `set` med et simpelt IoT‑scenarie.

Forestil dig, at du har nogle temperatursensorer i et lille IoT‑setup.
Lav et script `collections.py`, der:

1. Opretter:
   - En liste `temperaturer = [21.5, 22.0, 21.5, 23.1, 22.0]` (målinger fra sensorer).
   - Et dictionary `sensorer`, hvor nøglen er sensor‑navn og værdien er den seneste måling, fx:
     ```python
     sensorer = {
         "sensor_1": 21.5,
         "sensor_2": 22.0,
         "sensor_3": 23.1,
     }
     ```
   - Et set `unikke_temperaturer` baseret på listen `temperaturer`.
2. Udskriver:
   - Alle temperaturer i listen.
   - Alle sensorer og deres værdi fra dictionary.
   - Alle unikke temperaturer fra sættet.
3. Viser, hvordan du:
   - Tilføjer en ny måling til listen `temperaturer`.
   - Opdaterer værdien for `sensor_2` i dictionary.
   - Regenererer `unikke_temperaturer` efter en ændring.

*Ekstra:* Beregn gennemsnitstemperaturen ud fra listen `temperaturer`.

---

## Opgave 7 – String manipulation

**Formål:** Øve string‑metoder fra præsentationen.

Lav et script `strings.py`, der:

1. Har en streng `tekst = "Hello, World!"`.
2. Udskriver:
   - `tekst.upper()`
   - `tekst.lower()`
   - `tekst.strip()` (prøv med ekstra mellemrum før/efter)
   - `tekst.replace("World", "Python")`
   - `tekst.split(",")`
3. Lav en liste `ord = ["Python", "er", "sjovt"]` og brug `" ".join(ord)` til at samle den til en streng.

*Ekstra:* Brug slicing til at udskrive kun `Hello` fra `"Hello, World!"`.

---

## Opgave 8 – Funktioner

**Formål:** Skrive og bruge egne funktioner.

Lav et script `functions.py`, der indeholder:

1. En funktion `add(a, b)` som returnerer summen af to tal.
2. En funktion `is_even(n)` som returnerer `True`, hvis tallet er lige, ellers `False`.
3. En funktion `greet(name)` som printer `Hej <name>!`.
4. En `main`‑sektion hvor du kalder funktionerne med forskellige værdier og udskriver resultaterne.

*Ekstra:* Lav en funktion `average(numbers)`, der tager en liste af tal og returnerer gennemsnittet.

---

## Opgave 9 – Programstruktur og hovedprogram

**Formål:** Bruge den typiske struktur med `if __name__ == "__main__":`.

Lav et script `program.py`, der følger denne struktur:

```python
import time

WELCOME_MESSAGE = "Velkommen til mit program"

def menu():
    print("1) Sig hej")
    print("2) Vis tiden")
    print("3) Afslut")

def say_hello():
    name = input("Hvad hedder du? ")
    print(f"Hej {name}!")

if __name__ == "__main__":
    print(WELCOME_MESSAGE)
    while True:
        menu()
        choice = input("Vælg et punkt: ")
        if choice == "1":
            say_hello()
        elif choice == "2":
            print("Klokken er:", time.strftime("%H:%M:%S"))
        elif choice == "3":
            print("Farvel!")
            break
        else:
            print("Ugyldigt valg, prøv igen.")
```

*Opgave:* Skriv koden selv (kopiér ikke), forstå hver del og udbyg evt. menuen med et ekstra punkt.

---

## Opgave 10 – Brug af modul (`random`)

**Formål:** Introducere brug af eksterne moduler.

Lav et script `guess_game.py`, der bruger `random` til et simpelt gæt‑et‑tal‑spil:

1. Importér `random`.
2. Lad programmet vælge et tilfældigt tal mellem 1 og 20.
3. Brugeren skal gætte tallet:
   - Hvis gættet er for højt: skriv `For højt!`
   - Hvis gættet er for lavt: skriv `For lavt!`
   - Hvis gættet er rigtigt: skriv `Tillykke, du gættede rigtigt!` og afslut.
4. Giv brugeren maks. 5 forsøg.

*Ekstra:* Vis hvor mange forsøg brugeren brugte, når spillet er slut.

---

## Kort eksempel – Hente data fra en API

Inden API‑opgaverne kan du vise et helt simpelt eksempel på et API‑kald.

```python
import requests

url = "https://api.agify.io/?name=peter"

response = requests.get(url)

print("Statuskode:", response.status_code)

data = response.json()  # JSON -> dict

print("Rå data:", data)
print("Navn:", data["name"])
print("Gættet alder:", data["age"])
print("Antal personer i datasæt:", data["count"])
```

---

## Ekstra – API‑opgaver

Disse opgaver kræver modulet `requests` og kan bruges som ekstra udfordring.

Installer først `requests` (i en terminal):

```bash
pip install requests
```

### Opgave A - Hent Elspotpriser via en API
**Formål:** Lære at hente og arbejde med elspotpriser fra en [web-API](https://www.elprisenligenu.dk/).

Du skal skrive et Python-program, der henter elspotpriser fra API’en og viser dem pænt på skærmen.

### Opgave B – Hent valutakurser via en API

**Formål:** Lære at kalde en API, læse JSON‑data og udtrække de felter, du skal bruge.

Du skal skrive et Python‑program, der henter den aktuelle valutakurs mellem to valutaer ved hjælp af en web‑API og viser resultatet pænt på skærmen.

1. Find en API, der giver valutakurser (på den angivne side), og læs kort dokumentationen:
   - Hvordan ser URL’en ud?
   - Hvilke parametre skal med i URL’en (for eksempel basisvaluta)?

2. Skriv en funktion som:
   - Sender en HTTP `GET`‑forespørgsel til API’en.
   - Modtager svaret som JSON og omdanner det til Python‑data.
   - Finder kursen base `currency` til `to_currency` i svaret.
   - Returnerer denne kurs som tal.

3. I dit hovedprogram (`if __name__ == "__main__":`):
   - Sæt `from_currency` til `"USD"` og `to_currency` til `"DKK"`.
   - Kald funktionen og gem resultatet i en variabel `rate`.
   - Hvis du fik en gyldig kurs, så print en sætning i stil med:
     - `Exchange rate from USD to DKK: 7.12`
   - Hvis du ikke fik en gyldig kurs (for eksempel hvis API’en ikke kendte valutaen), så print en passende fejlbesked.

4. Udvidelse (valgfri):
   - Brug `time`‑modulet til også at udskrive tidspunktet for (skal være læsevenligt), hvornår data sidst blev opdateret, hvis API’en giver denne information (for eksempel et felt med “last updated” i JSON‑svaret).

**Krav til løsningen:**

- Du skal bruge `requests`‑biblioteket til at lave HTTP‑kald.
- Du skal selv finde ud af, hvilke felter i JSON‑svaret der indeholder:
  - Basisvaluta
  - Dato/tid (hvis muligt)
  - Kursen til `to_currency`
- Programmet skal kunne køre uden at du manuelt retter i svaret – alt skal hentes og behandles i Python. Du skal kunne forklare alt i koden til underviseren og dine medstuderende.
