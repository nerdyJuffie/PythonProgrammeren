```{code-cell} python
import jupyterquiz
print("JupyterQuiz is succesvol geladen!")
# Afronden, machten en wortels

In dit hoofdstuk leer je hoe je in Python getallen bewerkt die verder gaan dan simpel optellen of aftrekken.

## 1. Afronden in Python
Naast het rekenen met de standaard rekenoperators willen we soms ook getallen afronden. Hiervoor hebben we een aantal mogelijkheden in Python:

* **`round()`**: Rondt een getal af op de standaard wijze. **Let op!** Bij een `.5` waarde rondt `round()` af naar het dichtstbijzijnde **even** getal.
    * `round(2.5)` wordt `2`
    * `round(3.5)` wordt `4`
* **`math.ceil()`**: Rondt een getal altijd naar boven af. Hiervoor moet je eerst de module `math` importeren.
* **`math.floor()`**: Rondt een getal altijd naar beneden af.
* **`int()`**: Wordt gebruikt om een getal simpelweg af te kappen (alles achter de komma weghalen). `int(3.6)` wordt dus `3`.

### Test je kennis over afronden

```{code-cell} python
:tags: [remove-input]
from jupyterquiz import display_quiz

afronden_vragen = [
    {
        "question": "Wat is de uitkomst van round(2.5)?",
        "type": "multiple_choice",
        "answers": [
            { "answer": "3", "correct": False, "feedback": "Fout. Python rondt .5 af naar het dichtstbijzijnde EVEN getal." },
            { "answer": "2", "correct": True, "feedback": "Correct! Omdat 2 even is, rondt Python 2.5 naar beneden af naar 2." }
        ]
    },
    {
        "question": "Welke functie gebruik je om 3.1 af te ronden naar 4?",
        "type": "multiple_choice",
        "answers": [
            { "answer": "math.ceil()", "correct": True, "feedback": "Juist, ceil (plafond) rondt altijd naar boven af." },
            { "answer": "math.floor()", "correct": False, "feedback": "Nee, floor (vloer) rondt naar beneden af." },
            { "answer": "int()", "correct": False, "feedback": "Fout, int() kapt het getal af naar 3." }
        ]
    }
]

display_quiz(afronden_vragen)
```

---

## 2. Machtsverheffen in Python
Er zijn drie veelgebruikte manieren om machten te berekenen:

1.  **De operator `**`**: De meest eenvoudige manier.
    * `2 ** 3` levert `8`.
    * Als je met gehele getallen (integers) rekent, is het resultaat een integer. Bij floats is het resultaat een float.
2.  **`pow(basis, exponent)`**: Een ingebouwde functie. `pow(5, 2)` levert `25`.
3.  **`math.pow()`**: Deze functie uit de math-bibliotheek levert altijd een `float` op voor meer precisie. `math.pow(5, 2)` levert `25.0`.

---

## 3. Wortels in Python
Voor het trekken van wortels gebruik je meestal één van deze twee methoden:

1.  **`math.sqrt()`**: De aanbevolen methode.
    * *Beperking:* Werkt alleen voor getallen $\ge 0$.
    * Het resultaat is altijd een `float`.
    * `math.sqrt(25)` levert `5.0`.
2.  **`** 0.5`**: Je kunt ook de machtsoperator gebruiken om een wortel te trekken (tot de macht 0.5 verheffen).

### Oefenvraag Machten & Wortels

```{code-cell} python
:tags: [remove-input]
from jupyterquiz import display_quiz

machten_vragen = [
    {
        "question": "Wat is de uitkomst van 2 ** 3?",
        "type": "multiple_choice",
        "answers": [
            { "answer": "6", "correct": False, "feedback": "Fout, dit is 2 keer 3. Gebruik ** voor machtsverheffen." },
            { "answer": "8", "correct": True, "feedback": "Correct! 2 * 2 * 2 = 8." }
        ]
    },
    {
        "question": "Welke functie levert altijd een float op, zelfs bij gehele getallen?",
        "type": "multiple_choice",
        "answers": [
            { "answer": "pow(5, 2)", "correct": False, "feedback": "Nee, de standaard pow() geeft hier een integer terug." },
            { "answer": "math.pow(5, 2)", "correct": True, "feedback": "Juist! math.pow() geeft altijd een float (25.0)." }
        ]
    }
]

display_quiz(machten_vragen)
```
