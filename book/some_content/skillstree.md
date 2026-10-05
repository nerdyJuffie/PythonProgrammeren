---
layout: page
title: 🌲 Python Skill Tree
permalink: /skilltree/
---

<!-- Markmap bibliotheken laden -->
<script src="https://jsdelivr.net"></script>
<script src="https://jsdelivr.net"></script>
<script src="https://jsdelivr.net"></script>

<div class="skilltree-wrapper">
  <h1>🌲 Interactieve Python Skill Tree</h1>
  <p>Klik op de cirkels/knooppunten om takken in of uit te klappen. Gebruik je muiswiel om te zoomen.</p>
  
  <!-- De container waar de boom in getekend wordt -->
  <svg id="mindmap" style="width: 100%; height: 500px; border: 1px solid #ddd; border-radius: 8px; background: #fafafa;"></svg>
</div>

<!-- Hieronder staat jouw data in Markdown-formaat. Pas dit gerust aan! -->
<script id="markmap-data" type="text/template">
# 🐍 Python 4 Havo

## 📘 H1: De Basis
### 📖 [Theorie H1](https://github.io)
### 🥉 Brons: Paspoort-Script
#### 🎯 Doel: Variabelen & input()
#### 📺 [Bekijk Video](https://youtube.com)
### 🥈 Zilver: Story Generator
#### 🎯 Doel: f-strings gebruiken
#### 📺 [Bekijk Video](https://youtube.com)
### 🥇 Goud: Factuurgenerator
#### 🎯 Doel: Rekenen & Type Casting
#### 📺 [Bekijk Video](https://youtube.com)

## 📗 H2: Beslissingen (If/Else)
### 📖 [Theorie H2](https://github.io)
### 🥉 Brons: Toegangscode
#### 🎯 Doel: Vergelijkingsoperators
### 🥈 Zilver: Cijfer-Beoordelaar
#### 🎯 Doel: Elif-structuren
### 🥇 Goud: Text RPG Game
#### 🎯 Doel: Nested conditions

## 📙 H3: Herhaling (Loops)
### 📖 [Theorie H3](https://github.io)
### 🥉 Brons: Teltrainer
### 🥈 Zilver: Raad het Getal
### 🥇 Goud: Wachtwoord Validator
</script>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    // 1. Haal de Markdown data op uit het script-element
    const markdownData = document.getElementById('markmap-data').textContent;
    
    // 2. Initialiseer de Markmap transformer
    const { Markmap, loadCSS, loadJS, Transformer } = window.markmap;
    const transformer = new Transformer();
    const { root, features } = transformer.transform(markdownData);
    
    // 3. Render de mindmap in de SVG
    const svgElement = document.getElementById('mindmap');
    const mm = Markmap.create(svgElement, {
      autoFit: true,
      duration: 500
    }, root);

    // 4. Voeg een handige toolbar toe (Inzoomen, Uitzoomen, Reset)
    const { Toolbar } = window.markmap;
    const toolbar = Toolbar.create(mm);
    toolbar.attach();
    svgElement.parentElement.appendChild(toolbar.render());
  });
</script>

<style>
  /* Zorgt ervoor dat de toolbar netjes linksonder de mindmap zweeft */
  .markmap-toolbar {
    position: relative;
    margin-top: -40px;
    margin-left: 10px;
    z-index: 10;
  }
  .skilltree-wrapper {
    margin-bottom: 30px;
  }
</style>
