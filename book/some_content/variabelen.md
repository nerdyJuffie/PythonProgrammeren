# Variabelen

## wat is een variabele
Als je aan een kind wilt uitleggen hoe deze bijvoorbeeld een som moet optellen, bijvoorbeeld 4 + 3 , dan begin je vaak met "je hebt een getal 4 en daarbij tel je op een ander getal 3". Wat je gedaan hebt is aangegeven dat 4 en 3 niet hetzelfde getal zijn, maar twee verschillende getallen. Je hebt ze als het ware in doosjes met een label gestopt: getal en ander_getal. 

Een {ref} variabele kun je voorstellen als een pizzadoos met een opschrift wat voor pizza er in zit.    

```{figure} ../figures/legePizzaDoos.jpeg
---
width: 75%
align: right
---
```

Net als een pizzadoos maar 1 pizza kan bevatten, kan een variabele maar 1 ding van een soort bevatten:
- **integer**: geheel getal
- **float/ double**: een kommagetal
- **char**: een karakter
- **string**: een stuk tekst
- **boolean**: true of false
- **array**: een geordende lijst
- en zo zijn er nog een paar

Bij de meeste programmeertalen geldt de regel dat als een doosje een label en type inhoud heeft gekregen, dat doosje niet later iets van een ander type kan bevatten.

## eisen aan de naam
De naam van een variabele moet aan een aantal eisen voldoen:
- begint altijd met een kleine letter of underscore (_)
- mag alleen uit letters, cijfers en underscores (_) bestaan.
- moet logisch zijn, beschrijvend.
- indien bestaat uit meerdere woorden, dan begint ieder nieuw woord met een hoofdletter.


```{exercise}
:label: my-exercise

Welke van de onderstaande variabelenamen voldoen niet aan bovenstaande eisen? Leg per naam die niet voldoet uit waarom niet!
1.  classificatie 
2.  Classificatie 
3.  cl@ssificatie 
4.	class1f1cat1e 
5.	1classificatie 
6.	_classificatie 
7.	class
8.	Class
9.  PI
```

Als je de opgave gemaakt hebt kun je de uitwerking hier bekijken.
````{solution} my-exercise
:label: my-solution
:class: dropdown

Hier is de oplossing:
1.  voldoet
2.  voldoet niet, want start met een hoofdletter
3.  voldoet niet, bevat een verboden teken
4.  voldoet niet, want een naam moet logisch en beschijvend zijn. Het is onlogisch om de 1-en middenin de tekst te stoppen.
5.  voldoet niet, want het begint met een cijfer
6.  voldoet, maar is onlogisch
7.  voldoet niet, want class is een gereserveerd woord in Python
8.  voldoet niet, want begint met een hoofdletter. Op moment dat het met een kleine letter is voldoet het niet, want gereserveerd woord.
9.  voldoet. In python schrijven we constanten in CAPS (hoofdletters), om duidelijk het verschil tussen een gewone variabele en een constante aan te geven.

````
