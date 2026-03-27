# 01 – Installation af Pandas og Matplotlib (VS Code)

## Hvad skal du kunne til sidst

- Installere `pandas` og `matplotlib`.
- Køre et lille test‑program i VS Code.
- Lægge dine Python‑filer i en simpel mappe.

---

## Helt kort: hvad installerer vi

| Pakke        | Hvad den gør                              |
|--------------|-------------------------------------------|
| `pandas`     | Arbejde med tabeller og data (DataFrames) |
| `matplotlib` | Tegne grafer                              |

---

## Trin 1: Åbn VS Code og find terminalen

1. Start VS Code.
2. Åbn terminal:
   - Tastatur: `Ctrl` + `` ` `` (backtick)
   - Eller menu: `Terminal → New Terminal`.

---

## Trin 2: Tjek at Python virker

Skriv én af disse i terminalen og tryk Enter:

```bash
python --version

# eller på nogle computere

python3 --version

# på Windows kan denne også findes

py --version
```

Du skal se et versionsnummer. Hvis ikke, så installer Python fra <https://www.python.org>.

---

## Trin 3: Installer pakkerne

Standardkommando:

```bash
pip install pandas matplotlib
```

Hvis den siger, at `pip` ikke findes, prøv i stedet:

```bash
python -m pip install pandas matplotlib
python3 -m pip install pandas matplotlib
py -m pip install pandas matplotlib   # Windows
```

---

## Trin 4: Lav din testfil

1. I VS Code: `File → New File`.
2. Gem den som `test_installation.py` (fx i en mappe `python/`).
3. Skriv et lille program, der:
   - Importerer `pandas` og `matplotlib.pyplot`.
   - Skriver versionsnummeret for `pandas` ud.
   - Opretter en lille DataFrame og printer den.
   - Tegner en simpel linje‑graf og viser den med `plt.show()`.

*(Hint: du kan tage udgangspunkt i et minieksempel fra undervisningen)*

---

## Trin 5: Kør din test

1. Åbn `test_installation.py` i editoren.
2. Kør scriptet på én af disse måder:
   - Højreklik i editoren og vælg **Run Python File in Terminal**, eller
   - Klik på den grønne play‑knap i øverste højre hjørne.
3. Tjek at:
   - Der bliver udskrevet en lille tabel i terminalen.
   - Der åbner et vindue med en linjegraf.

Hvis begge dele sker, er du klar.

---

## Fejlfinding i børnehøjde

### A: `ModuleNotFoundError: No module named 'pandas'`

Du mangler pakken. Kør installationen igen:

```bash
python -m pip install pandas matplotlib
```

### B: Den kører et *forkert* Python

Vælg den rigtige interpreter i VS Code:

1. Åbn kommandopaletten (`Ctrl` + `Shift` + `P`).
2. Søg efter `Python: Select Interpreter`.
3. Vælg den, der passer til din installation (ofte den med nyeste version).

### C: `pip` virker ikke

Brug `python -m pip` eller `python3 -m pip` som vist ovenfor.

---

## Bonus: hold styr på pakker

### Virtuelt miljø (valgfrit)

Brug kun dette, hvis du vil holde et projekt helt rent.

```bash
# lav et miljø
python -m venv env

# aktiver
# Windows:
env\Scripts\activate

# macOS/Linux:
source env/bin/activate

# installer i miljøet
pip install pandas matplotlib
```

### `requirements.txt` som huskeliste

```bash
pip freeze > requirements.txt
```

Andre kan installere det samme med:

```bash
pip install -r requirements.txt
```

---

## Mappestruktur der er nem at forstå

En simpel struktur kan fx være:

```text
mit-projekt/
├─ python/
│  └─ test_installation.py
└─ requirements.txt   (valgfri)
```

Læg dine `.py`‑filer i mappen `python/`.

---

## Klar til næste trin

- Du kan importere `pandas` og `matplotlib`.
- Du kan køre en Python‑fil i VS Code.
- Du kan gemme dine filer i en simpel mappe.
