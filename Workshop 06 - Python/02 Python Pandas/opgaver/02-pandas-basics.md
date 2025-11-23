# 02 – Pandas Basics

## Mål

- Forstå forskellen på `DataFrame` og `Series`.
- Hente elspot‑priser ned i et `DataFrame`.
- Bruge `.head()`, `.info()` og `.describe()` til at kigge på data.

---

## Hvad er en DataFrame?

Tænk en `DataFrame` som et lille regneark:

- Rækker og kolonner (som i Excel).
- En `Series` er **én kolonne** fra tabellen.

---

## Trin 1: Importér pandas

```python
import pandas as pd
```

---

## Trin 2: Hent elspot‑priser som tabel

>Vi vil bruge elspot‑priser fra en åben data‑kilde [elprisenligenu.dk](https://www.elprisenligenu.dk/api/v1/prices/2025/11-23_DK2.json).

API konstruktion: https://www.elprisenligenu.dk/api/v1/prices/[ÅR]/[MÅNED]-[DAG]_[PRISKLASSE].json

1. Find en elspot‑API eller CSV (fx fra **elprisenligenu.dk** eller en anden offentlig datakilde), som giver dig priser time for time for et døgn.
2. Gem data lokalt som en CSV‑fil, fx `elspot.csv`.
3. Indlæs data i et `DataFrame` `df`, så du mindst har disse kolonner:
   - Time_start (læsbart format)
   - Time_end (læsbart format)
   - DKK_per_kWh
   - EUR_per_kWh

---

## Trin 3: Udforsk tabellen som en detektiv

Kig hurtigt på formen, indholdet og tallene:

- brug head(), info() og describe()
    - Find mean, max og minimum for prisene
    - brug columns til at se kolonnenavnene

**Husk:**

- `.head()` viser 5 rækker (brug `.head(10)` for 10).
- `.info()` viser datatyper og om der mangler værdier.
- `.describe()` virker på tal‑kolonner.

---

## Trin 4: Hvad er en Series?

Tag én kolonne (fx prisen) ud af tabellen – så har du en `Series`:

```python
pris = df["DKK_per_kWh"]   # dette er en Series
print(pris)
print(type(pris))         # <class 'pandas.core.series.Series'>
```

---

## Trin 5: Tilføj en ny kolonne

Alle rækker får fx samme tekst i en ny kolonne (område eller kilde):

```python
df["område"] = "DK1"   # eller "DK2" alt efter område
print(df.head())
```

---

## Trin 6: Filtrér rækker over en grænse

Filtrér de dyre timer i `dyre_timer`, og de billige timer i `billige_timer`, indsæt selv et passende bestemt niveau:

```python 
dyre_timer = df[df["DKK_per_kWh"] > 0.5]  # tilpas grænse
```

