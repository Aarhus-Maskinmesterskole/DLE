# 🔧 Function Node - Kort intro

Function-noden i Node-RED bruges her som en **lille introduktion** til, at man kan skrive korte JavaScript-snippets til at ændre data.

Målet er ikke at kunne alt — kun at se idéen:
- læse `msg.payload`
- ændre data
- sende resultatet videre med `return msg;`

---

## 1️⃣ Opgave 1: Gør et tal større

**Formål:** Prøv at ændre en værdi i en Function-node.

**Opgave:**
- Opret en Inject-node med tallet `10`
- Brug en Function-node til at lægge `5` til
- Vis resultatet i en Debug-node

**Hjælp:**
```javascript
msg.payload = msg.payload + 5;
return msg;
```

---

## 2️⃣ Opgave 2: Simpel temperaturtekst

**Formål:** Brug `if/else` i en Function-node.

**Opgave:**
- Opret en Inject-node der sender fx `22` eller `35`
- Hvis værdien er over `30`, skal payload være `"For varmt"`
- Ellers skal payload være `"OK"`

**Hjælp:**
```javascript
if (msg.payload > 30) {
  msg.payload = "For varmt";
} else {
  msg.payload = "OK";
}

return msg;
```

---

## 3️⃣ Opgave 3: Tilføj timestamp

**Formål:** Lav et lille objekt med flere oplysninger.

**Opgave:**
- Opret en Inject-node med en temperatur, fx `24`
- Lav payload om til et objekt med:
  - værdi
  - enhed
  - timestamp

**Hjælp:**
```javascript
msg.payload = {
  value: msg.payload,
  unit: "°C",
  timestamp: new Date().toISOString()
};

return msg;
```

---

## 4️⃣ Opgave 4: Husk antal klik

**Formål:** Se at Function-noden kan huske noget mellem kald med `context`.

**Opgave:**
- Opret en Inject-node du kan trykke flere gange på
- Brug en Function-node til at tælle antal klik
- Vis tælleren i Debug

**Hjælp:**
```javascript
var count = context.get('count') || 0;
count = count + 1;
context.set('count', count);

msg.payload = "Klik: " + count;
return msg;
```

---

## 5️⃣ Opgave 5: Send til forskellige outputs

**Formål:** Se at én Function-node kan sende til flere veje.

**Opgave:**
- Opret en Inject-node med et tal
- Sæt Function-noden til **2 outputs**
- Send lave værdier til output 1 og høje værdier til output 2

**Hjælp:**
```javascript
if (msg.payload < 30) {
  return [msg, null];
} else {
  return [null, msg];
}
```

---

## 🎯 Mini-bonus

Lav en Function-node der:
1. modtager en temperatur
2. tjekker om den er over `30`
3. sender et objekt videre med både temperatur og status

**Eksempel:**
```javascript
msg.payload = {
  temperature: msg.payload,
  status: msg.payload > 30 ? "For varmt" : "OK"
};

return msg;
```

---

## 📚 Det vigtigste at huske

```javascript
// Læs data
msg.payload

// Ændr data
msg.payload = "Ny værdi";

// Send beskeden videre
return msg;
```

Hvis du vil gemme noget mellem kald:

```javascript
context.set('navn', værdi);
var værdi = context.get('navn');
```

---

## ✅ Når du er færdig

Så har du prøvet at bruge en Function-node til at:
- [ ] ændre data
- [ ] bruge simpel logik
- [ ] lave et objekt
- [ ] gemme en værdi med `context`
- [ ] sende data til flere outputs

---

**Det er nok til en god introduktion. Resten kommer senere.**
