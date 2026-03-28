# Functionele functies  

Soms is het handiger en overzichtelijker als je in plaats van hele lappen code in je main programma korte regels hebt die verwijzen naar aparte functies.

De algemene syntax voor een functie:  
>\# parameterloze functie  
>def functienaam():  
>	\# hier komt de code die de functie uit moet voeren

```{python}
def begroeting():
  print("Hoi, welkom in de cursus Python Programmeren")
  print("Ik wens je een fijne dag!")

begroeting()
print( 30 * '-')
begroeting()
```

Zoals je ziet is de uitkomst vrij statisch. Iedere keer wordt het identieke geprint.  
Een *parameterloze functie* voert altijd dezelfde vaste taak uit. Je gebruikt ze bijvoorbeeld voor het printen van een begroeting, een vaste berekening of een menu.

Een functie met een of meer *parameters* is veel dynamischer. Je geeft waarden mee, parameters genoemd, waardoor de uitkomst steeds verschillend is. Het maakt dat de functie daardoor ook goed herbruikbaar.  

>\# functie met 1 parameter en een return waarde  
>def functienaam(parameter):  
>	\# hier komt de code die de functie uit moet voeren
> \# hier komt de return waarde

```{python}
def meters_yards_omrekenen(afstand):
  yard = afstand * 1.0936133
  return yard

print("Hoeveel yard is 4 meter?"
yard = meters_yards_omrekenen(4)
print(f"4 meter is gelijk aan {yard} yards")

meters = int(input("Hoeveel meter afstand moet worden omgezet in yards? ")
yards = meters_yards_omrekenen(meters)
print(f"{meters} meter is gelijk aan {yards} yards")
```

In het bovenstaand codevoorbeeld geeft de functie een retourwaarde (met *return*), die als toekenning wordt meegegeven aan een variabele. Zoals je ziet is de functie ook heel goed herbruikbaar. 
Een functie met een parameter kan ook meerdere parameters hebben. Iedere parameter moet je dan aangeven met een logische naam en die wordt dan ook in de code binnen de functie aangeroepen. Een functie met een parameter hoeft geen return waarde te hebben, zoals je in het volgende codeblok zult zien.

```{python}
def bmi_bepalen(lengte, gewicht):
  lengte = lengte/100
  bmi = gewicht/ (lengte ** 2)
  print(f"Uw bmi is {bmi}.")
  if bmi < 18.5:
    print("U heeft ondergewicht.")
  elif bmi < 25:
    print("U heeft een gezond gewicht.")
  elif bmi < 30:
    print("Er is sprake van overgewicht.")
  else:
    print("Obesitas (ernstig overgewicht)")

lengte = int(input("Geef uw lengte in cm"))
gewicht = float(input("Wat is uw gewicht"))
bmi_bepalen(lengte, gewicht)

lengte = 175
gewicht = 63
bmi_bepalen(lengte,gewicht)
```

