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

## 2. Machtsverheffen in Python
Er zijn drie veelgebruikte manieren om machten te berekenen:

1.  **De operator `**`**: De meest eenvoudige manier. `2 ** 3` levert `8`. Als je met gehele getallen (integers) rekent, is het resultaat een integer. Bij floats is het resultaat een float.
2.  **`pow(basis, exponent)`**: Een ingebouwde functie. `pow(5, 2)` levert `25`.
3.  **`math.pow()`**: Deze functie uit de math-bibliotheek levert altijd een `float` op voor meer precisie. `math.pow(5, 2)` levert `25.0`.

## 3. Wortels in Python
Voor het trekken van wortels gebruik je meestal één van deze twee methoden:

* **`math.sqrt()`**: De aanbevolen methode. Het resultaat is altijd een `float`. `math.sqrt(25)` levert `5.0`. (Let op: werkt alleen voor getallen $\ge 0$).
* **`** 0.5`**: Je kunt ook de machtsoperator gebruiken om een wortel te trekken (tot de macht 0.5 verheffen).

---

## Test je kennis
Beantwoord de onderstaande vragen om te kijken of je de stof begrijpt.

```{code-cell} ipython3
from jupyterquiz import display_quiz
display_quiz("quiz_python_rekenen.json")

