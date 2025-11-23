# 03 – Import og eksport af CSV‑filer

## Mål

- Importere CSV‑filer med `read_csv()`.
- Gemme `DataFrame` som CSV med `to_csv()`.
- Forstå forskel på **separator**, **encoding** og **index**.

---

## Hvad er en CSV?

En CSV er en tekstfil hvor:

- Hver linje er en række.
- Kolonner er skilt af et tegn – ofte komma `,` eller semikolon `;`.

Tænk på det som et meget simpelt regneark.

---

## Trin 1: Læg filen ved siden af dit script

En simpel projektstruktur kunne være:

```text
mit-projekt/
├─ python/
│  ├─ script.py
│  └─ data.csv    # læg CSV her, samme mappe som scriptet
```

Hvis din CSV ligger et andet sted, skal du bruge en sti, fx:

```python
"data/elspotpriser.csv"      # undermappe
"../elspotpriser.csv"        # en mappe op
```

---

## Trin 2: Læs en CSV hurtigt

Eksempel på indhold i `elspotpriser.csv`:

```text
DKK_per_kWh,EUR_per_kWh,EXR,time_start,time_end
0.38014,0.05089,7.469799,2025-11-23T00:00:00+01:00,2025-11-23T01:00:00+01:00
```

Python‑kode:

```python
import pandas as pd

data = pd.read_csv("elspotpriser.csv")
print(data.head())      # kig på de første 5 rækker
print(data.tail())      # kig på de sidste 5 rækker
```

Hvis du får `FileNotFoundError`, er stien eller filnavnet forkert – ret det.

---

## Trin 3: Brug det rigtige skilletegn

I Danmark er CSV ofte med semikolon `;`, hvor andre bruger komma.

Ret elspotpriser.csv til at bruge semikolon ved et ekstra argument i `read_csv()`. Brug `sep=";"`:

---

## Trin 4: Decimal‑komma og æøå

Ofte vil vi gerne kunne aflæse en csv med decimal‑komma og gemme en csv der kan åbnes pænt i dansk Excel. Brug følgende argumenter ved gemning:

- `index=False`
- `sep=";"`
- `encoding="utf-8-sig"`

---

## Trin 5: Udforsk data som en detektiv
Efter at have gemt data så indlæs det igen og kig på info og statistik:

---

