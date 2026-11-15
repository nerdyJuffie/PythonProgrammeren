# 🌲 Python Skill Tree

Klik op een knooppunt om takken in of uit te klappen. Zoom met je muiswiel of de knoppen en sleep met de muis om te verschuiven.

```{raw} html
<style>
  .skilltree-wrap { margin-bottom: 30px; }
  .skilltree-bar { display: flex; gap: 6px; margin-bottom: 6px; flex-wrap: wrap; }
  .skilltree-bar button {
    padding: 3px 12px; border-radius: 6px; cursor: pointer;
    border: 1px solid var(--pst-color-border, #aaa);
    background: var(--pst-color-surface, #f5f5f5);
    color: var(--pst-color-text-base, inherit);
  }
  #skilltree-svg {
    width: 100%; height: 600px;
    border: 1px solid var(--pst-color-border, #ddd); border-radius: 8px;
    --markmap-text-color: #333;
  }
  html[data-theme="dark"] #skilltree-svg {
    --markmap-text-color: #e6e6e6;
    --markmap-a-color: #6ab0ff;
    --markmap-a-hover-color: #9cc9ff;
  }
  #skilltree-msg { color: #c0392b; }
</style>

<div class="skilltree-wrap">
  <div class="skilltree-bar">
    <button type="button" id="st-in">＋ Inzoomen</button>
    <button type="button" id="st-out">－ Uitzoomen</button>
    <button type="button" id="st-fit">⤢ Passend maken</button>
  </div>
  <svg id="skilltree-svg"></svg>
  <p id="skilltree-msg"></p>
</div>

<!-- Hieronder staat de inhoud van de boom. Pas dit gerust aan! -->
<script id="skilltree-data" type="text/template">
# 🐍 Python 4 Havo

## 📘 H1: De Basis
### 📖 [Theorie H1](hoofdstuk1.html)
### 🥉 Brons: Paspoort-Script
#### 🎯 Doel: Variabelen & input()
#### 📺 [Bekijk Video](https://www.youtube.com/)
### 🥈 Zilver: Story Generator
#### 🎯 Doel: f-strings gebruiken
#### 📺 [Bekijk Video](https://www.youtube.com/)
### 🥇 Goud: Factuurgenerator
#### 🎯 Doel: Rekenen & Type Casting
#### 📺 [Bekijk Video](https://www.youtube.com/)

## 📗 H2: Beslissingen (If/Else)
### 📖 [Theorie H2](hoofdstuk5.html)
### 🥉 Brons: Toegangscode
#### 🎯 Doel: Vergelijkingsoperators
### 🥈 Zilver: Cijfer-Beoordelaar
#### 🎯 Doel: Elif-structuren
### 🥇 Goud: Text RPG Game
#### 🎯 Doel: Nested conditions

## 📙 H3: Herhaling (Loops)
### 📖 [Theorie H3](hoofdstuk7.html)
### 🥉 Brons: Teltrainer
### 🥈 Zilver: Raad het Getal
### 🥇 Goud: Wachtwoord Validator
</script>

<script>
(function () {
  var D3 = "https://cdn.jsdelivr.net/npm/d3@7";
  var VIEW = "https://cdn.jsdelivr.net/npm/markmap-view";

  function esc(s) { return s.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;"); }
  function inline(s) {
    return esc(s).replace(/\[([^\]]+)\]\(([^)\s]+)\)/g,
      '<a href="$2" target="_blank" rel="noopener">$1</a>');
  }
  /* Zet de Markdown-koppen om in een boom: # = wortel, ## = takken, ### = bladeren, enz. */
  function parse(md) {
    var root = null, stack = [];
    md.split("\n").forEach(function (line) {
      var m = line.match(/^(#{1,6})\s+(.*)$/);
      if (!m) return;
      var lvl = m[1].length, node = { content: inline(m[2].trim()), children: [] };
      while (stack.length && stack[stack.length - 1].lvl >= lvl) stack.pop();
      if (stack.length) stack[stack.length - 1].node.children.push(node);
      else if (root) root.children.push(node);
      else root = node;
      stack.push({ lvl: lvl, node: node });
    });
    return root;
  }
  function load(src) {
    return new Promise(function (resolve, reject) {
      var s = document.createElement("script");
      s.src = src; s.onload = resolve;
      s.onerror = function () { reject(new Error("Kon " + src + " niet laden")); };
      document.head.appendChild(s);
    });
  }
  function start() {
    var svg = document.getElementById("skilltree-svg");
    var root = parse(document.getElementById("skilltree-data").textContent);
    var mm = window.markmap.Markmap.create(svg, { autoFit: true, duration: 400, initialExpandLevel: 2 }, root);
    document.getElementById("st-in").onclick = function () { mm.rescale(1.25); };
    document.getElementById("st-out").onclick = function () { mm.rescale(0.8); };
    document.getElementById("st-fit").onclick = function () { mm.fit(); };
  }

  /* Dit boek laadt RequireJS (voor Live Code). Daardoor melden bibliotheken als d3 zich
     als 'module' aan en niet als globale variabele. Zet define daarom tijdelijk uit. */
  var oudeDefine = window.define;
  window.define = undefined;
  function herstel() { if (oudeDefine !== undefined) window.define = oudeDefine; else delete window.define; }

  load(D3).then(function () { return load(VIEW); })
    .then(start)
    .catch(function (e) {
      document.getElementById("skilltree-msg").textContent =
        "De skill tree kon niet worden geladen: " + e.message + ". Controleer je internetverbinding.";
    })
    .then(herstel, herstel);
})();
</script>
```
