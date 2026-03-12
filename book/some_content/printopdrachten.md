# Printopdrachten nader uitgelegd  

In de voorgaande voorbeelden heb je al een beetje het gebruik van het __print( )__ commando gezien.  
print( ) gebruik je om _output_ te genereren op de console.

Je kunt verschillende stukken tekst aan elkaar vastmaken met de + in een printopdracht, dit noemen we _concatenatie_.
---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Printopdrachten in Markdown

In dit bestand gebruiken we **MyST Markdown**. Dit ziet eruit als een gewoon tekstbestand, maar de codeblokken hieronder zijn interactief voor de leerlingen zodra ze op de raketknop klikken.

## 1. Uitleg Concatenatie
Je kunt tekst aan elkaar plakken met het `+` teken. Dit noemen we concatenatie.

```{code-cell} python
# Probeer de tekst aan te passen en klik op 'Run'
tekst1 = "Programmeren is "
tekst2 = "leuk!"
print(tekst1 + tekst2)


