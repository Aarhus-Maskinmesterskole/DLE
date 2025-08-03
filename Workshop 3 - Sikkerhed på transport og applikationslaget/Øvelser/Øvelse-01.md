## 📋 Øvelse 1: Introduktion til HTTP og datasikkerhed

### **Formål**

* At forstå, hvad HTTP er, og hvordan data sendes åbent uden beskyttelse.
* At få indsigt i, hvorfor usikret datakommunikation kan være en risiko.

---

### **Baggrund**

HTTP står for “HyperText Transfer Protocol” og bruges, når vi besøger almindelige hjemmesider eller sender data mellem computere på nettet – fx fra sensorer til servere.
**Vigtigt:** Når du bruger HTTP, sendes alle data som “åbne breve”. Alle på netværket kan i princippet læse med eller opsnappe beskeden!

---

### **Sådan gør du – step by step**

1. **Tænk over, hvordan du normalt bruger internettet**

   * Har du prøvet at besøge en hjemmeside, hvor der står “http\://” forrest i adressen?
   * Hvordan kan du se, om forbindelsen er sikker (hint: hængelås/“https”)?

2. **Diskutér i grupper eller på holdet:**

   * Hvilke data sender du, når du bruger HTTP (fx beskeder, adgangskoder, målinger)?
   * Hvem kan “se” de data på vejen fra din computer til serveren, hvis det er HTTP?

3. **Find eksempler sammen med underviser:**

   * Prøv at besøge en offentlig hjemmeside, der stadig bruger HTTP, og bemærk at browseren advarer: “Denne side er ikke sikker”.

4. **Notér fordele og ulemper:**

   * Fordel: HTTP er nemt og hurtigt at bruge.
   * Ulempe: Alle kan aflure eller ændre dine data.

5. **(Valgfrit) Se et simpelt eksempel:**

   * Underviseren kan vise, hvordan data nemt kan læses i klartekst med et netværksværktøj.

---

### **Krav til øvelsen**

* Du skal kunne forklare, hvad HTTP er, og hvorfor det ikke beskytter dine data.
* Du skal kunne nævne mindst én risiko ved at sende data ukrypteret.

---

### **Når du er færdig**

* Gå videre til næste øvelse, hvor du bygger din egen HTTP-service i Node-RED!
